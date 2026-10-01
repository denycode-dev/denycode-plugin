--- api-design-principles ---

# SkillSpector Security Report

**Skill:** api-design-principles  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\api-design-principles`  
**Scanned:** 2026-10-01 04:28:36 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 5 of 5 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 76/100 |
| Severity | HIGH |
| Recommendation | DO NOT INSTALL |

## Components (6)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 40 | No |
| `assets/api-design-checklist.md` | markdown | 155 | No |
| `assets/rest-api-template.py` | python | 182 | Yes |
| `references/graphql-schema-design.md` | markdown | 583 | No |
| `references/rest-best-practices.md` | markdown | 408 | No |
| `resources/implementation-playbook.md` | markdown | 513 | No |

## Issues (8)

### 🔴 HIGH: AE1

**Location:** `SKILL.md:36`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:40`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: TM1

**Location:** `references/rest-best-practices.md:79`  
**Confidence:** 80%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🔴 HIGH: TM1

**Location:** `resources/implementation-playbook.md:72`  
**Confidence:** 80%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🟡 MEDIUM: E1

**Location:** `references/rest-best-practices.md:143`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

### 🟡 MEDIUM: E1

**Location:** `references/rest-best-practices.md:144`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

### 🟡 MEDIUM: E1

**Location:** `references/rest-best-practices.md:145`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

### 🟡 MEDIUM: E1

**Location:** `references/rest-best-practices.md:146`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 6 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| llm_batch_failed | `assets/api-design-checklist.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `assets/rest-api-template.py` | LLM analysis failed for this file range. |
| llm_batch_failed | `assets/rest-api-template.py:1-182` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/graphql-schema-design.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/graphql-schema-design.md:493-505` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/graphql-schema-design.md:511-520` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/graphql-schema-design.md:526-534` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md:112-121` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md:127-134` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md:197-232` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md:311-325` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md:343-351` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md:357-384` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/rest-best-practices.md:390-407` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:66-81` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:87-142` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:148-203` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:209-233` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:338-425` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:431-470` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** Yes

*Generated by SkillSpector v2.11.2*

--- api-security-best-practices ---

# SkillSpector Security Report

**Skill:** api-security-best-practices  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\api-security-best-practices`  
**Scanned:** 2026-10-01 04:28:48 UTC  

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 30/100 |
| Severity | MEDIUM |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 910 | No |

## Issues (4)

### 🔴 HIGH: PE3

**Location:** `SKILL.md:194`  
**Confidence:** 70%  

**Message:** Credential Access

**Remediation:** Remove references to credential paths. Use environment variables or secrets managers. For docs, use placeholder paths (e.g., /path/to/config). Never load .env or token files in production code paths.

---

### 🔴 HIGH: PE3

**Location:** `SKILL.md:287`  
**Confidence:** 70%  

**Message:** Credential Access

**Remediation:** Remove references to credential paths. Use environment variables or secrets managers. For docs, use placeholder paths (e.g., /path/to/config). Never load .env or token files in production code paths.

---

### 🔴 HIGH: PE3

**Location:** `SKILL.md:318`  
**Confidence:** 70%  

**Message:** Credential Access

**Remediation:** Remove references to credential paths. Use environment variables or secrets managers. For docs, use placeholder paths (e.g., /path/to/config). Never load .env or token files in production code paths.

---

### 🔴 HIGH: PE3

**Location:** `SKILL.md:708`  
**Confidence:** 70%  

**Message:** Credential Access

**Remediation:** Remove references to credential paths. Use environment variables or secrets managers. For docs, use placeholder paths (e.g., /path/to/config). Never load .env or token files in production code paths.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | successful |
| Status | partial |
| Coverage | 100.0% |
| Fully inspected | 1 |
| Partially inspected | 0 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| reference_missing | `SKILL.md:184-184` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:231-231` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- architect-review ---

# SkillSpector Security Report

**Skill:** architect-review  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\architect-review`  
**Scanned:** 2026-10-01 04:28:51 UTC  

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | SAFE |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 172 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | successful |
| Status | complete |
| Coverage | 100.0% |
| Fully inspected | 1 |
| Partially inspected | 0 |
| Entirely uninspected | 0 |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- architecture-patterns ---

# SkillSpector Security Report

**Skill:** architecture-patterns  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\architecture-patterns`  
**Scanned:** 2026-10-01 04:29:08 UTC  

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | SAFE |

## Components (2)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 45 | No |
| `resources/implementation-playbook.md` | markdown | 479 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | successful |
| Status | complete |
| Coverage | 100.0% |
| Fully inspected | 2 |
| Partially inspected | 0 |
| Entirely uninspected | 0 |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- audit-context-building ---

# SkillSpector Security Report

**Skill:** audit-context-building  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\audit-context-building`  
**Scanned:** 2026-10-01 04:29:45 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 1 of 4 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 29/100 |
| Severity | MEDIUM |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 303 | No |

## Issues (3)

### 🔴 HIGH: MP3

**Location:** `SKILL.md:151`  
**Confidence:** 80%  

**Message:** Memory Manipulation

**Remediation:** Protect agent memory and state from modification by untrusted content. Use read-only memory for critical instructions and validate all state changes.

---

### 🟡 MEDIUM: SQP-1

**Location:** `SKILL.md:14–26`  
**Confidence:** 75%  

**Message:** Vague activation condition: 'When active' provides no explicit trigger phrases or invocation criteria

**Remediation:** Add an explicit list of trigger phrases (e.g., 'audit context', 'build context for audit') and at least one negative example clarifying when the skill should NOT activate (e.g., 'do not activate on general code questions without the audit context keyword').

---

### 🟢 LOW: SQP-1

**Location:** `SKILL.md:25–37`  
**Confidence:** 70%  

**Message:** Missing trigger scope constraints and negative examples for activation

**Remediation:** Supplement the 'When to Use' section with specific invocation commands or trigger keywords (e.g., 'activated only when user says "start context build" or "audit context phase"') and add examples of requests that should NOT trigger the skill.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | successful |
| Status | partial |
| Coverage | 100.0% |
| Fully inspected | 1 |
| Partially inspected | 0 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_structured_response_invalid | `SKILL.md` | LLM returned a malformed structured response after bounded retries. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| degraded | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer meta_analyzer status: degraded.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- audit-skills ---

# SkillSpector Security Report

**Skill:** audit-skills  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\audit-skills`  
**Scanned:** 2026-10-01 04:30:09 UTC  

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 81/100 |
| Severity | CRITICAL |
| Recommendation | DO NOT INSTALL |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 130 | No |

## Issues (7)

### 🔴 HIGH: TM1

**Location:** `SKILL.md:57`  
**Confidence:** 90%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🔴 HIGH: TM1

**Location:** `SKILL.md:57`  
**Confidence:** 90%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🔴 HIGH: TM1

**Location:** `SKILL.md:57`  
**Confidence:** 85%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🔴 HIGH: SC2

**Location:** `SKILL.md:82`  
**Confidence:** 90%  

**Message:** External Script Fetching

**Remediation:** Avoid downloading and executing remote scripts. Use trusted packages from PyPI/npm. If remote fetch is required, verify checksums and use HTTPS.

---

### 🟡 MEDIUM: SQP-2

**Location:** `SKILL.md:13`  
**Confidence:** 91%  

**Message:** The comment explicitly allowlists the dangerous `curl | bash` pattern, which may cause scanners or systems honoring this directive to suppress warnings for downloaded scripts executed by a shell. Although this file only mentions that pattern as an example, the silent allowlist could mask the same behavior elsewhere in the skill or bundle.

**Remediation:** Remove the allowlist directive. If an exception is necessary for a specific benign example, scope it narrowly and document the reason without suppressing detection of the pattern across the skill or bundle.

---

### 🟡 MEDIUM: RA2

**Location:** `SKILL.md:65`  
**Confidence:** 75%  

**Message:** Session Persistence

**Remediation:** Remove any persistence mechanisms (cron jobs, startup scripts, state files). Skills should not maintain state across sessions without explicit user consent.

---

### 🟡 MEDIUM: RA2

**Location:** `SKILL.md:65`  
**Confidence:** 75%  

**Message:** Session Persistence

**Remediation:** Remove any persistence mechanisms (cron jobs, startup scripts, state files). Skills should not maintain state across sessions without explicit user consent.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | successful |
| Status | partial |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| obfuscated_instruction_text | `SKILL.md` | Obfuscated instruction text could not be fully evaluated by the deterministic layer. |
| reference_missing | `SKILL.md:63-63` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:65-65` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:71-71` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:85-85` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| completed | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| completed | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| degraded | `` |  |
| completed | `` |  |

### Limitations

- Analyzer static_patterns_agent_snooping status: degraded.
- Analyzer static_patterns_anti_refusal status: degraded.
- Analyzer static_patterns_deserialization status: degraded.
- Analyzer static_patterns_excessive_agency status: degraded.
- Analyzer static_patterns_harmful_content status: degraded.
- Analyzer static_patterns_memory_poisoning status: degraded.
- Analyzer static_patterns_privilege_escalation status: degraded.
- Analyzer static_patterns_prompt_injection status: degraded.
- Analyzer static_patterns_rogue_agent status: degraded.
- Analyzer static_patterns_ssrf status: degraded.
- Analyzer static_patterns_supply_chain status: degraded.
- Analyzer static_patterns_system_prompt_leakage status: degraded.
- Analyzer static_patterns_tool_misuse status: degraded.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- auth-implementation-patterns ---

# SkillSpector Security Report

**Skill:** auth-implementation-patterns  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\auth-implementation-patterns`  
**Scanned:** 2026-10-01 04:31:59 UTC  

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 90/100 |
| Severity | CRITICAL |
| Recommendation | DO NOT INSTALL |

## Components (2)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 42 | No |
| `resources/implementation-playbook.md` | markdown | 618 | No |

## Issues (6)

### 🔴 HIGH: AE1

**Location:** `SKILL.md:33`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:42`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: PE3

**Location:** `resources/implementation-playbook.md:130`  
**Confidence:** 70%  

**Message:** Credential Access

**Remediation:** Remove references to credential paths. Use environment variables or secrets managers. For docs, use placeholder paths (e.g., /path/to/config). Never load .env or token files in production code paths.

---

### 🔴 HIGH: PE3

**Location:** `resources/implementation-playbook.md:162`  
**Confidence:** 70%  

**Message:** Credential Access

**Remediation:** Remove references to credential paths. Use environment variables or secrets managers. For docs, use placeholder paths (e.g., /path/to/config). Never load .env or token files in production code paths.

---

### 🔴 HIGH: SQP-2

**Location:** `resources/implementation-playbook.md:329`  
**Confidence:** 90%  

**Message:** Passing the access token via URL query parameter during OAuth callback redirect exposes the token in browser history, server logs, referrer headers, and proxy logs. This is a documented anti-pattern that can lead to token leakage/session hijacking even though it's a common educational example.

**Remediation:** Avoid putting tokens in URL query strings. Instead, set the token in an httpOnly secure cookie, or use a short-lived one-time code exchanged server-side for the token (authorization code pattern), or post the token via a secure fragment with immediate clearing.

---

### 🔴 HIGH: PE3

**Location:** `resources/implementation-playbook.md:592`  
**Confidence:** 70%  

**Message:** Credential Access

**Remediation:** Remove references to credential paths. Use environment variables or secrets managers. For docs, use placeholder paths (e.g., /path/to/config). Never load .env or token files in production code paths.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | successful |
| Status | partial |
| Coverage | 50.0% |
| Fully inspected | 1 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| static_parse_limit | `resources/implementation-playbook.md` | A security-relevant expression exceeded a bounded static parser's span limit. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| degraded | `` |  |
| completed | `` |  |

### Limitations

- Analyzer static_patterns_tool_misuse status: degraded.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- clean-code ---

# SkillSpector Security Report

**Skill:** clean-code  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\clean-code`  
**Scanned:** 2026-10-01 04:32:10 UTC  

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | SAFE |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 94 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | successful |
| Status | complete |
| Coverage | 100.0% |
| Fully inspected | 1 |
| Partially inspected | 0 |
| Entirely uninspected | 0 |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- context-mode ---

# SkillSpector Security Report

**Skill:** context-mode  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\context-mode`  
**Scanned:** 2026-10-01 04:32:17 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 5 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 100/100 |
| Severity | CRITICAL |
| Recommendation | DO NOT INSTALL |

## Components (5)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 300 | No |
| `references/anti-patterns.md` | markdown | 283 | No |
| `references/patterns-javascript.md` | markdown | 298 | No |
| `references/patterns-python.md` | markdown | 304 | No |
| `references/patterns-shell.md` | markdown | 277 | No |

## Issues (26)

### 🔴 HIGH: SQP-2

**Location:** `SKILL.md:103`  
**Confidence:** 80%  

**Message:** ctx_purge operation lacks adequate warning about permanent data loss

**Remediation:** Add a dedicated warning block (e.g., using a Markdown blockquote or bold caution callout) near the ctx_purge reference explaining that this operation is irreversible and permanently destroys all indexed knowledge base content. Consider advising users to confirm scope before running.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:286`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:300`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:297`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:298`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:299`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: TM1

**Location:** `references/patterns-shell.md:36`  
**Confidence:** 85%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🔴 HIGH: TM1

**Location:** `references/patterns-shell.md:67`  
**Confidence:** 85%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🔴 HIGH: TM1

**Location:** `references/patterns-shell.md:97`  
**Confidence:** 85%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🔴 HIGH: TM1

**Location:** `references/patterns-shell.md:119`  
**Confidence:** 85%  

**Message:** Tool Parameter Abuse

**Remediation:** Validate all tool parameters against an allowlist. Reject dangerous parameter values (shell=True, --force, -rf /) and use safe defaults.

---

### 🟡 MEDIUM: SQP-1

**Location:** `SKILL.md:5–15`  
**Confidence:** 80%  

**Message:** Overly broad trigger phrases overlap with common everyday speech

**Remediation:** Narrow the trigger phrases to require more specific context (e.g., 'analyze logs using context-mode', 'run tests via ctx_execute'). Add explicit negative examples or exclusion conditions clarifying when context-mode should NOT activate. Consider scoping triggers to situations where output size is the driver, rather than the task type alone.

---

### 🟡 MEDIUM: SQP-1

**Location:** `SKILL.md:16`  
**Confidence:** 85%  

**Message:** Catch-all trigger 'ANY MCP tool output that may exceed 20 lines' is ambiguous and overly broad

**Remediation:** Replace the speculative 'may exceed' language with a concrete, measurable condition (e.g., 'output confirmed to exceed 20 lines in a previous call') or document explicit exclusion cases where this trigger does not apply.

---

### 🟡 MEDIUM: SDI-2

**Location:** `SKILL.md:30–35`  
**Confidence:** 94%  

**Message:** Unrelated destructive and publishing operations are authorized by the Bash whitelist

**Remediation:** Remove unrelated side-effect commands from the whitelist, or explicitly justify and declare them as part of the skill’s scope.

---

### 🟡 MEDIUM: SSRF2

**Location:** `SKILL.md:89`  
**Confidence:** 70%  

**Message:** Internal Network Request

**Remediation:** Avoid requests to loopback/link-local/private hosts from skill code. If internal access is intended, document it and validate the target against an allowlist.

---

### 🟡 MEDIUM: SSRF2

**Location:** `SKILL.md:175`  
**Confidence:** 70%  

**Message:** Internal Network Request

**Remediation:** Avoid requests to loopback/link-local/private hosts from skill code. If internal access is intended, document it and validate the target against an allowlist.

---

### 🟡 MEDIUM: SDI-2

**Location:** `SKILL.md:103`  
**Confidence:** 86%  

**Message:** Permanent deletion of indexed content is outside the stated skill purpose

**Remediation:** Remove the purge instruction, or clearly declare when and why indexed content may be permanently deleted and require explicit user authorization.

---

### 🟡 MEDIUM: MP2

**Location:** `SKILL.md:288`  
**Confidence:** 85%  

**Message:** Context Window Stuffing

**Remediation:** Implement context-window management that detects and rejects padding or stuffing attempts. Prioritize system instructions over user-injected content.

---

### 🟡 MEDIUM: E1

**Location:** `references/anti-patterns.md:198`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

### 🟡 MEDIUM: E1

**Location:** `references/anti-patterns.md:206`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

### 🟡 MEDIUM: E1

**Location:** `references/patterns-javascript.md:14`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

### 🟡 MEDIUM: E1

**Location:** `references/patterns-javascript.md:49`  
**Confidence:** 50%  

**Message:** External Transmission

**Remediation:** Verify the destination URL is trusted and necessary. Remove or replace with documented APIs. Ensure no secrets, tokens, or PII are transmitted.

---

### 🟡 MEDIUM: RP1

**Location:** `references/patterns-javascript.md:267`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx jest'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

### 🟡 MEDIUM: RP1

**Location:** `references/patterns-shell.md:79`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx jest'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

### 🟡 MEDIUM: RP1

**Location:** `references/patterns-shell.md:44`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx tsc'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

### 🟡 MEDIUM: SQP-2

**Location:** `references/patterns-shell.md:126–178`  
**Confidence:** 55%  

**Message:** Log File Analysis patterns extract and summarize potentially sensitive data (IP addresses, request paths, access patterns) without any user-facing privacy warning

**Remediation:** Add an explicit note in this reference doc (and the parent SKILL.md) that log analysis patterns may surface sensitive data such as client IP addresses and request details, and recommend redaction or confirmation before summarizing production logs externally.

---

### 🟢 LOW: SQP-2

**Location:** `references/patterns-javascript.md:263–270`  
**Confidence:** 35%  

**Message:** Example code executes shell commands (`execSync('npx jest...')`) without any documented warning about subprocess execution in this reference file

**Remediation:** Add a brief note near the top of the file (or in the parent SKILL.md) clarifying that `execute` with javascript can run subprocess commands like `execSync`, and that users should review generated code before execution.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 5 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| static_parse_limit | `SKILL.md` | A security-relevant expression exceeded a bounded static parser's span limit. |
| reference_missing | `SKILL.md:91-91` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:191-192` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:197-197` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:202-206` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/anti-patterns.md` | LLM analysis failed for this file range. |
| static_parse_limit | `references/anti-patterns.md` | A security-relevant expression exceeded a bounded static parser's span limit. |
| llm_batch_failed | `references/anti-patterns.md:38-49` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/anti-patterns.md:53-65` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/anti-patterns.md:77-85` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/anti-patterns.md:89-93` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/anti-patterns.md:160-168` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/anti-patterns.md:172-183` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md` | LLM analysis failed for this file range. |
| static_parse_limit | `references/patterns-javascript.md` | A security-relevant expression exceeded a bounded static parser's span limit. |
| llm_batch_failed | `references/patterns-javascript.md:13-34` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md:41-78` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md:90-111` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md:118-139` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md:150-179` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md:186-211` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md:222-252` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-javascript.md:263-295` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:13-43` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:50-79` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:90-118` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:125-159` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:170-203` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:210-240` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:251-270` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-python.md:277-302` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:13-36` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:44-67` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:79-97` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:105-119` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:131-146` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:153-176` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:187-213` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:220-246` | LLM analysis failed for this file range. |
| llm_batch_failed | `references/patterns-shell.md:257-275` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| degraded | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer static_patterns_tool_misuse status: degraded.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- ctx-doctor ---

# SkillSpector Security Report

**Skill:** ctx-doctor  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\ctx-doctor`  
**Scanned:** 2026-10-01 04:32:17 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 22 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- ctx-index ---

# SkillSpector Security Report

**Skill:** ctx-index  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\ctx-index`  
**Scanned:** 2026-10-01 04:32:18 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 4 of 4 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 46 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| llm_batch_failed | `SKILL.md:22-27` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:33-33` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:39-39` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- ctx-insight ---

# SkillSpector Security Report

**Skill:** ctx-insight  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\ctx-insight`  
**Scanned:** 2026-10-01 04:32:18 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 24 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- ctx-purge ---

# SkillSpector Security Report

**Skill:** ctx-purge  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\ctx-purge`  
**Scanned:** 2026-10-01 04:32:18 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 49 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- ctx-search ---

# SkillSpector Security Report

**Skill:** ctx-search  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\ctx-search`  
**Scanned:** 2026-10-01 04:32:18 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 4 of 4 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 35 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| llm_batch_failed | `SKILL.md:22-26` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:32-32` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- ctx-stats ---

# SkillSpector Security Report

**Skill:** ctx-stats  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\ctx-stats`  
**Scanned:** 2026-10-01 04:32:18 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 26 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- ctx-upgrade ---

# SkillSpector Security Report

**Skill:** ctx-upgrade  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\ctx-upgrade`  
**Scanned:** 2026-10-01 04:32:18 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 31 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- debugger ---

# SkillSpector Security Report

**Skill:** debugger  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\debugger`  
**Scanned:** 2026-10-01 04:32:19 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 53 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| reference_missing | `SKILL.md:28-28` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- design-md ---

# SkillSpector Security Report

**Skill:** design-md  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\design-md`  
**Scanned:** 2026-10-01 04:32:19 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 4 of 4 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 21/100 |
| Severity | MEDIUM |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 179 | No |

## Issues (1)

### 🔴 HIGH: P6

**Location:** `SKILL.md:95`  
**Confidence:** 85%  

**Message:** Direct Prompt Extraction

**Remediation:** Remove any instructions that reveal, print, or output system prompts or internal rules. System instructions should never be exposed to end users.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| reference_missing | `SKILL.md:11-11` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:24-24` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:34-34` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:55-55` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:56-56` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:61-61` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:62-62` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:152-152` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- docker-expert ---

# SkillSpector Security Report

**Skill:** docker-expert  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\docker-expert`  
**Scanned:** 2026-10-01 04:32:20 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 5 of 5 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 13/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 413 | No |

## Issues (2)

### 🟡 MEDIUM: RP1

**Location:** `SKILL.md:63`  
**Confidence:** 75%  

**Message:** Docker image referenced without tag or digest: 'docker run --rm'.

**Remediation:** Pin the image: image:tag or image@sha256:abc123

---

### 🟡 MEDIUM: TM3

**Location:** `SKILL.md:247`  
**Confidence:** 60%  

**Message:** Unsafe Defaults

**Remediation:** Override unsafe defaults with secure settings (verify=True, auth required, restrictive permissions). Review and harden all tool configurations.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| llm_batch_failed | `SKILL.md:30-42` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:57-68` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:99-99` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:100-100` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:106-106` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:141-141` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:162-162` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:165-165` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:223-223` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:269-269` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:272-272` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:285-288` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- drizzle-orm-expert ---

# SkillSpector Security Report

**Skill:** drizzle-orm-expert  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\drizzle-orm-expert`  
**Scanned:** 2026-10-01 04:32:21 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 5 of 5 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 12/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 363 | No |

## Issues (5)

### 🟡 MEDIUM: RP1

**Location:** `SKILL.md:208`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx drizzle-kit'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

### 🟡 MEDIUM: RP1

**Location:** `SKILL.md:211`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx drizzle-kit'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

### 🟡 MEDIUM: RP1

**Location:** `SKILL.md:214`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx drizzle-kit'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

### 🟡 MEDIUM: RP1

**Location:** `SKILL.md:217`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx drizzle-kit'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

### 🟡 MEDIUM: RP1

**Location:** `SKILL.md:360`  
**Confidence:** 70%  

**Message:** MCP server referenced without pinned version: 'npx drizzle-kit'.

**Remediation:** Pin the version: npx @scope/server@1.2.3

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| reference_missing | `SKILL.md:39-39` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:39-64` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:70-70` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:70-80` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:86-92` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:100-130` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:136-151` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:157-173` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:179-183` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:191-201` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:195-195` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:196-196` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:207-217` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:225-225` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:225-231` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:228-228` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:237-245` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:239-239` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:251-256` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:253-253` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:264-272` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:278-282` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:288-302` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:310-310` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:310-323` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:329-329` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:329-338` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:343-343` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:356-356` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- e2e-testing ---

# SkillSpector Security Report

**Skill:** e2e-testing  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\e2e-testing`  
**Scanned:** 2026-10-01 04:32:21 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 165 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- error-handling-patterns ---

# SkillSpector Security Report

**Skill:** error-handling-patterns  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\error-handling-patterns`  
**Scanned:** 2026-10-01 04:32:22 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 5 of 5 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 45/100 |
| Severity | MEDIUM |
| Recommendation | CAUTION |

## Components (2)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 38 | No |
| `resources/implementation-playbook.md` | markdown | 635 | No |

## Issues (3)

### 🔴 HIGH: AE1

**Location:** `SKILL.md:34`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:38`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🟡 MEDIUM: OH3

**Location:** `resources/implementation-playbook.md:567`  
**Confidence:** 80%  

**Message:** Unbounded Output

**Remediation:** Set explicit limits on output length, generation count, and rate. Use max_tokens and truncation to prevent unbounded output.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 2 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| llm_batch_failed | `resources/implementation-playbook.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md` | LLM analysis failed for this file range. |
| static_parse_limit | `resources/implementation-playbook.md` | A security-relevant expression exceeded a bounded static parser's span limit. |
| llm_batch_failed | `resources/implementation-playbook.md:54-85` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:90-108` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:113-148` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:155-193` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:198-236` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:241-273` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:280-324` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:331-387` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:397-457` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:465-514` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:522-559` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:574-615` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| degraded | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer static_patterns_tool_misuse status: degraded.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- favicon ---

# SkillSpector Security Report

**Skill:** favicon  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\favicon`  
**Scanned:** 2026-10-01 04:32:22 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 5 of 5 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 7/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 233 | No |

## Issues (1)

### 🟡 MEDIUM: PE2

**Location:** `SKILL.md:25`  
**Confidence:** 70%  

**Message:** Sudo/Root Execution

**Remediation:** Avoid sudo/root unless strictly required. Prefer least-privilege patterns. If elevation is needed, document the justification and scope.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| reference_missing | `SKILL.md:11-11` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:20-20` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:33-33` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:41-41` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:46-46` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:47-47` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:49-49` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:51-51` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:52-52` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:53-53` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:55-55` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:65-65` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:66-66` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:67-67` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:84-89` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:94-94` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:99-99` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:104-104` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:109-109` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:115-115` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:146-146` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:153-153` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:157-157` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:175-175` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:178-193` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:203-203` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- financial-engineering-principles ---

# SkillSpector Security Report

**Skill:** financial-engineering-principles  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\financial-engineering-principles`  
**Scanned:** 2026-10-01 04:32:24 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 4 of 4 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 430 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| reference_missing | `SKILL.md:79-79` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:80-80` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:89-95` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md:105-109` | LLM analysis failed for this file range. |
| reference_missing | `SKILL.md:427-427` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| reference_missing | `SKILL.md:429-429` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- find-bugs ---

# SkillSpector Security Report

**Skill:** find-bugs  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\find-bugs`  
**Scanned:** 2026-10-01 04:32:24 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 77 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| reference_missing | `SKILL.md:14-14` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- fixing-motion-performance ---

# SkillSpector Security Report

**Skill:** fixing-motion-performance  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\fixing-motion-performance`  
**Scanned:** 2026-10-01 04:32:25 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 4 of 4 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 152 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| llm_batch_failed | `SKILL.md:136-144` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- frontend-design ---

# SkillSpector Security Report

**Skill:** frontend-design  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\frontend-design`  
**Scanned:** 2026-10-01 04:32:25 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (2)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `LICENSE.txt` | text | 177 | No |
| `SKILL.md` | markdown | 277 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 2 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `LICENSE.txt` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- go-concurrency-patterns ---

# SkillSpector Security Report

**Skill:** go-concurrency-patterns  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\go-concurrency-patterns`  
**Scanned:** 2026-10-01 04:32:26 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 4 of 4 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 37/100 |
| Severity | MEDIUM |
| Recommendation | CAUTION |

## Components (2)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 36 | No |
| `resources/implementation-playbook.md` | markdown | 654 | No |

## Issues (2)

### 🔴 HIGH: AE1

**Location:** `SKILL.md:32`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🔴 HIGH: AE1

**Location:** `SKILL.md:36`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 2 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| llm_batch_failed | `resources/implementation-playbook.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:41-83` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:91-167` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:173-259` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:265-327` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:333-422` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:428-499` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:505-576` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:582-618` | LLM analysis failed for this file range. |
| llm_batch_failed | `resources/implementation-playbook.md:624-631` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- golang-pro ---

# SkillSpector Security Report

**Skill:** golang-pro  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\golang-pro`  
**Scanned:** 2026-10-01 04:32:26 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 176 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- graphql ---

# SkillSpector Security Report

**Skill:** graphql  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\graphql`  
**Scanned:** 2026-10-01 04:32:27 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 73 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- i18n-localization ---

# SkillSpector Security Report

**Skill:** i18n-localization  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\i18n-localization`  
**Scanned:** 2026-10-01 04:32:27 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 5 of 5 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 32/100 |
| Severity | MEDIUM |
| Recommendation | CAUTION |

## Components (2)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 159 | No |
| `scripts/i18n_checker.py` | python | 241 | Yes |

## Issues (2)

### 🔴 HIGH: AE1

**Location:** `SKILL.md:156`  
**Confidence:** 100%  

**Message:** Referenced artifact was not completely inspected

**Remediation:** Make the referenced artifact locally available and fully analyzable, or remove the reference.

---

### 🟡 MEDIUM: LP3

**Location:** `SKILL.md:1`  
**Confidence:** 70%  

**Message:** Skill declares no tool scope ('permissions' or 'allowed-tools') but code capabilities were detected: file_read.

**Remediation:** Declare the skill's tool scope: for Claude Code / Agent Skills SKILL.md, list the tools the skill may invoke in the 'allowed-tools' frontmatter field; for MCP server manifests, add a 'permissions' list naming the required capabilities.

---

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 2 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |
| reference_missing | `SKILL.md:47-47` | A local path-like reference does not match any bundled artifact, such as a file the skill writes at runtime. |
| llm_batch_failed | `SKILL.md:65-67` | LLM analysis failed for this file range. |
| llm_batch_failed | `scripts/i18n_checker.py` | LLM analysis failed for this file range. |
| llm_batch_failed | `scripts/i18n_checker.py:1-241` | LLM analysis failed for this file range. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer mcp_tool_poisoning status: failed.
- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.
- Analyzer meta_analyzer status: failed.

## Metadata

- **Executable Scripts:** Yes

*Generated by SkillSpector v2.11.2*

--- iconsax-library ---

# SkillSpector Security Report

**Skill:** iconsax-library  
**Source:** `C:\Users\App Jun Fro Dev SAU\.gemini\config\plugins\denycode-plugin\skills\iconsax-library`  
**Scanned:** 2026-10-01 04:32:27 UTC  

> ⚠️ **Degraded scan:** LLM analysis was requested but 3 of 3 LLM call(s) failed - results reflect STATIC analysis only for the affected batch(es).

## Risk Assessment

| Metric | Value |
|--------|-------|
| Score | 0/100 |
| Severity | LOW |
| Recommendation | CAUTION |

## Components (1)

| File | Type | Lines | Executable |
|------|------|-------|------------|
| `SKILL.md` | markdown | 38 | No |

## Issues (0)

No security issues detected.

## Inspection Completeness

| Metric | Value |
|--------|-------|
| Execution | failed |
| Status | failed |
| Coverage | 0.0% |
| Fully inspected | 0 |
| Partially inspected | 1 |
| Entirely uninspected | 0 |

### Ledger Exceptions

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| llm_batch_failed | `SKILL.md` | LLM analysis failed for this file range. |
| semantic_runtime_incomplete | `SKILL.md` | Requested semantic analysis did not produce complete per-source runtime telemetry. |

### Analyzer Statuses

| Reason / Status | Location | Details |
|-----------------|----------|---------|
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| completed | `` |  |
| completed | `` |  |
| no_applicable_files | `` | No files matched this analyzer's applicability contract. |
| failed | `` |  |
| failed | `` |  |
| failed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |
| completed | `` |  |

### Limitations

- Analyzer semantic_developer_intent status: failed.
- Analyzer semantic_quality_policy status: failed.
- Analyzer semantic_security_discovery status: failed.

## Metadata

- **Executable Scripts:** No

*Generated by SkillSpector v2.11.2*

--- Recursive Inspection Completeness ---

Status: partial

- recursive skill count budget 32 reached
- 27 recursive skill(s) omitted after an aggregate limit