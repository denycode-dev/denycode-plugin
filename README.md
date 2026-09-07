# denycode-plugin

Plugin untuk **Google Antigravity** yang menyediakan bundel kemampuan kustom: Skills, Rules, Subagents, MCP Servers, dan Lifecycle Hooks.

Dokumentasi resmi Antigravity Plugins: [https://antigravity.google/docs/plugins/](https://antigravity.google/docs/plugins/)

---

## 📁 Struktur Direktori Project

```text
denycode-plugin/
├── plugin.json               # [Wajib] Manifest utama plugin
├── mcp_config.json           # [Opsional] Konfigurasi server MCP (Model Context Protocol)
├── hooks.json                # [Opsional] Event hooks (PreToolUse, PostToolUse, sessionStart)
├── skills/                   # [Opsional] Koleksi workflow/skills untuk agen
│   └── sample-skill/
│       └── SKILL.md          # Definisi skill dengan frontmatter YAML
├── rules/                    # [Opsional] Aturan perilaku atau standar coding
│   └── denycode-rules.md     # Panduan dan batasan agen
├── agents/                   # [Opsional] Template definisi subagent kustom
│   └── denycode-agent.md     # Persona & instruksi subagent
├── .gitignore                # File git ignore
└── README.md                 # Dokumentasi plugin
```

---

## ⚙️ Komponen Plugin

### 1. `plugin.json` (Wajib)
Manifest utama plugin yang mendefinisikan metadata identitas plugin:
```json
{
  "name": "denycode-plugin",
  "version": "0.1.0",
  "description": "Antigravity plugin for denycode",
  "author": {
    "name": "denycode"
  },
  "license": "MIT",
  "keywords": [
    "antigravity",
    "antigravity-plugin",
    "denycode"
  ]
}
```

### 2. `skills/` (Skills)
Folder ini berisi daftar kemampuan/prosedur on-demand yang dapat dipanggil oleh agen. Setiap skill berada dalam subdirektori tersendiri dan memiliki file `SKILL.md`:
```yaml
---
name: sample-skill
description: Kapan dan mengapa skill ini digunakan
---

# Instruksi dan alur kerja skill di sini
```

### 3. `rules/` (Rules)
File Markdown yang mendefinisikan aturan global yang harus selalu ditaati oleh agen (seperti aturan penulisan kode, arsitektur, dan batasan operasional).

### 4. `agents/` (Subagents)
Definisi template subagent untuk mendelegasikan tugas-tugas spesifik (misalnya code reviewer, security auditor, tester).

### 5. `mcp_config.json` (Model Context Protocol)
Mendefinisikan server MCP eksternal yang terhubung dengan plugin ini untuk menyediakan tool tambahan:
```json
{
  "mcpServers": {
    "my-server": {
      "command": "node",
      "args": ["./servers/mcp-server.js"]
    }
  }
}
```

### 6. `hooks.json` (Event Hooks)
Mendefinisikan skrip otomatis yang dipicu pada event lifecycle agen (misalnya `PreToolUse`, `PostToolUse`, `sessionStart`, `beforeShellExecution`):
```json
{
  "hooks": {
    "PreToolUse": [],
    "PostToolUse": [],
    "sessionStart": []
  }
}
```

---

## 🚀 Cara Instalasi / Pemasangan Plugin

Plugin Antigravity dapat dipasang di level **Workspace (Proyek)** atau secara **Global**:

### A. Pemasangan Tingkat Workspace (Proyek Tertentu)
Agar plugin hanya aktif di satu project/workspace, letakkan direktori plugin ke dalam folder `.agents/plugins/`:
```text
<workspace_root>/
└── .agents/
    └── plugins/
        └── denycode-plugin/
            ├── plugin.json
            ├── ...
```

### B. Pemasangan Tingkat Global (Semua Workspace)
Agar plugin aktif di seluruh workspace di komputer Anda, salin/pindahkan folder plugin ke direktori konfigurasi global:
* **Windows**: `%USERPROFILE%\.gemini\config\plugins\denycode-plugin\` (contoh: `C:\Users\<User>\.gemini\config\plugins\denycode-plugin\`)
* **macOS / Linux**: `~/.gemini/config/plugins/denycode-plugin/`
