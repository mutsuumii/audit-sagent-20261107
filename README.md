# Security audit: rekursiv-ai/sagent

Date: 2026-11-07 | Auditor: [mutsuumii](https://github.com/mutsuumii)

## Summary

Found 2 issue(s): 2 high.

## Findings

### 1. [HIGH] Hardcoded credentials

**CWE-798** | `sagent/providers/openai/compat_test.py` line 173

Credentials hardcoded in source. Anyone with repo access can extract them.

```
assert await _Vendor(api_key="sk-given").credentials() == {
```

**Fix:** Use os.environ.get('SECRET') or a secrets manager. Never commit credentials.
---

### 2. [HIGH] Hardcoded credentials

**CWE-798** | `sagent/providers/huggingface/api_test.py` line 23

Credentials hardcoded in source. Anyone with repo access can extract them.

```
explicit = HuggingFace(api_key="explicit", base_url="http://box/v1")
```

**Fix:** Use os.environ.get('SECRET') or a secrets manager. Never commit credentials.
---
