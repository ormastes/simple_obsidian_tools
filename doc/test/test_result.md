# Test Results

**Generated:** 2026-03-16 01:32:18
**Total Tests:** 94
**Status:** ⚠️ 5 FAILED

## Summary

| Status | Count | Percentage |
|--------|-------|-----------|
| ✅ Passed | 89 | 94.7% |
| ❌ Failed | 5 | 5.3% |
| ⏭️ Skipped | 0 | 0.0% |
| 🔕 Ignored | 0 | 0.0% |
| 🔐 Qualified Ignore | 0 | 0.0% |

---

## 🔄 Recent Status Changes

| Test | Change | Run |
|------|--------|-----|
| extracts plain query | new_test |  |
| handles empty query | new_test |  |
| extracts tag operator | new_test |  |
| extracts path operator | new_test |  |
| extracts title operator | new_test |  |
| extracts multiple operators | new_test |  |
| extracts modified:recent | new_test |  |
| extracts linkto operator | new_test |  |
| extracts linkedfrom operator | new_test |  |
| returns false for plain query | new_test |  |
| returns true when tag filter present | new_test |  |
| returns true for modified:recent | new_test |  |
| extracts title from frontmatter | new_test |  |
| extracts tags from frontmatter list | new_test |  |
| extracts aliases from frontmatter | new_test |  |
| falls back to first heading when no title in frontmatter | new_test |  |
| handles empty content | new_test |  |
| extracts simple wikilinks | new_test |  |
| extracts wikilinks with aliases | new_test |  |
| extracts multiple wikilinks | new_test |  |

---

## ❌ Failed Tests (5)

### 🔴 finds notes by title

**File:** `test/unit/search_engine_spec.spl`
**Category:** Unit
**Failed:** 
**Flaky:** No (0.0% failure rate)

---

### 🔴 creates links table

**File:** `test/unit/indexer_spec.spl`
**Category:** Unit
**Failed:** 
**Flaky:** No (100.0% failure rate)

---

### 🔴 creates chunks table

**File:** `test/unit/indexer_spec.spl`
**Category:** Unit
**Failed:** 
**Flaky:** No (100.0% failure rate)

---

### 🔴 creates notes table

**File:** `test/unit/indexer_spec.spl`
**Category:** Unit
**Failed:** 
**Flaky:** No (100.0% failure rate)

---

### 🔴 creates tasks table

**File:** `test/unit/indexer_spec.spl`
**Category:** Unit
**Failed:** 
**Flaky:** No (100.0% failure rate)

---

---

## 📊 Timing Analysis

---

## 🎯 Action Items

### Priority 1: Fix Failing Tests (5)

1. **finds notes by title** - 
2. **creates links table** - 
3. **creates chunks table** - 
4. **creates notes table** - 
5. **creates tasks table** - 

### Priority 3: Stabilize Flaky Tests (25)

Tests with intermittent failures:
- detects stale notes (66.7% failure rate)
- finds all tasks matching query (66.7% failure rate)
- stores tags from frontmatter and inline (50.0% failure rate)
- indexes wikilinks (66.7% failure rate)
- indexes tasks (66.7% failure rate)

