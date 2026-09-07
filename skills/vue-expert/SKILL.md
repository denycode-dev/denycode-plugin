---
name: vue-expert
description: Master modern Vue 3 development with Composition API, script setup, TypeScript, Pinia, Vue Router, VueUse, and Vite optimization.
---

# Vue 3 Expert Guide

This skill provides production-grade architectural guidance, best practices, and patterns for Vue 3 application development.

---

## 1. Composition API & `<script setup>` Standards

### Modern Syntax & Structure
Always use `<script setup lang="ts">` for concise, type-safe, and high-performance components:

```vue
<script setup lang="ts">
import { ref, computed, onMounted } from 'vue'
import { useUserStore } from '@/stores/user'
import type { UserProfile } from '@/types/user'

// 1. Props & Emits Definition
interface Props {
  userId: string
  initialStatus?: 'active' | 'inactive'
  editable?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  initialStatus: 'active',
  editable: false
})

const emit = defineEmits<{
  (e: 'update:status', status: 'active' | 'inactive'): void
  (e: 'save', profile: UserProfile): void
}>()

// 2. State & Stores
const userStore = useUserStore()
const isLoading = ref(false)
const searchQuery = ref('')

// 3. Computed Properties
const isProfileComplete = computed(() => {
  return Boolean(userStore.currentUser?.name && userStore.currentUser?.email)
})

// 4. Methods / Event Handlers
function handleSave() {
  if (userStore.currentUser) {
    emit('save', userStore.currentUser)
  }
}
</script>

<template>
  <div class="profile-card">
    <div v-if="isLoading" class="skeleton-loader">Loading...</div>
    <div v-else>
      <h2>{{ userStore.currentUser?.name }}</h2>
      <button :disabled="!editable" @click="handleSave">Save</button>
    </div>
  </div>
</template>
```

---

## 2. Reactivity Rules & Best Practices

1. **Prefer `ref()` over `reactive()`**:
   - `ref()` works consistently for all primitives, arrays, and objects.
   - Destructuring `reactive()` loses reactivity unless wrapped in `toRefs()`.
   - `ref` makes reactivity explicit in TypeScript.

2. **Handling Deep Reactivity & Performance**:
   - For large immutable datasets (e.g., 10,000 table rows), use `shallowRef()` or `shallowReactive()` to prevent deep proxy overhead.
   - Avoid mutating props directly; emit updates to parents (`emit('update:modelValue', val)`).

3. **`computed()` Best Practices**:
   - Computeds must be pure (no side effects, no API calls, no DOM mutations).
   - For side effects, use `watch()` or `watchEffect()`.

```ts
// Good: Pure computed
const filteredItems = computed(() => {
  return items.value.filter(item => item.name.includes(searchQuery.value.trim()))
})

// Good: Side effect in watch with cleanup
watch(selectedId, async (newId, oldId, onCleanup) => {
  const controller = new AbortController()
  onCleanup(() => controller.abort())

  const data = await fetchData(newId, controller.signal)
  details.value = data
})
```

---

## 3. Composable Architecture (VueUse & Custom Hooks)

Encapsulate reusable logic in composables (`use*` naming convention):

```ts
// composables/usePagination.ts
import { ref, computed } from 'vue'

export function usePagination<T>(items: Ref<T[]>, pageSize = 10) {
  const currentPage = ref(1)

  const totalPages = computed(() => Math.ceil(items.value.length / pageSize))

  const paginatedData = computed(() => {
    const start = (currentPage.value - 1) * pageSize
    return items.value.slice(start, start + pageSize)
  })

  function nextPage() {
    if (currentPage.value < totalPages.value) currentPage.value++
  }

  function prevPage() {
    if (currentPage.value > 1) currentPage.value--
  }

  return {
    currentPage,
    totalPages,
    paginatedData,
    nextPage,
    prevPage
  }
}
```

---

## 4. State Management with Pinia

- Use Setup Stores (`defineStore('id', () => { ... })`) for idiomatic Vue 3 Composition API consistency:

```ts
// stores/counter.ts
import { defineStore } from 'pinia'
import { ref, computed } from 'vue'

export const useCounterStore = defineStore('counter', () => {
  const count = ref(0)
  const doubleCount = computed(() => count.value * 2)

  function increment() {
    count.value++
  }

  function reset() {
    count.value = 0
  }

  return { count, doubleCount, increment, reset }
})
```

- When destructuring store state/getters in components, use `storeToRefs()` to preserve reactivity:
```ts
import { storeToRefs } from 'pinia'
const store = useCounterStore()
const { count, doubleCount } = storeToRefs(store)
const { increment } = store // Actions can be destructured directly
```

---

## 5. Performance Checklist
- **`v-memo`**: Cache subtrees in large loops (`v-for` lists with low change frequency).
- **Component Async Loading**: Use `defineAsyncComponent` for heavy modal or below-the-fold components.
- **KeepAlive**: Use `<KeepAlive>` for expensive tabs or form wizards.
- **Provide / Inject**: Use `InjectionKey<T>` from `vue` for type-safe deep dependency injection.
