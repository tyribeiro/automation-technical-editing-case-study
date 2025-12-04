# Before and After Comparisons

This document highlights the differences between the unedited SME notes and the edited SOP, demonstrating the technical editing decisions made.

---

## Example 1: Ambiguous Step

**Before:**  
"router but not sure if it should be before iterator"

**After:**  
"The Router module must be placed before the Iterator so that filtering occurs prior to row expansion. This reduces unnecessary processing."

---

## Example 2: Missing Preconditions

**Before:**  
"google sheet has list of ids"

**After:**  
"A Google Sheet must be prepared in advance with a dedicated column for `list_id`, which is required for duplicate detection."

---

## Example 3: Vague Troubleshooting Note

**Before:**  
"smartsheet module sometimes fails, maybe because of column type?"

**After:**  
"The Smartsheet module fails when column names are used instead of numeric column IDs. All mappings must reference numeric IDs to ensure reliability."

---

## Example 4: Unclear Logic

**Before:**  
"scenario should stop if id already exists"

**After:**  
"If the `list_id` is already present in the Google Sheet, the scenario terminates immediately to prevent duplicate rows."

---

These examples illustrate substantive editing, logical restructuring, and removal of ambiguity to create documentation suitable for technical and certification contexts.
