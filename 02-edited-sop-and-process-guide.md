# Edited SOP and Process Guide  
Automation Workflow: ClickUp → Make.com → Google Sheets → Smartsheet

This document provides a clear, structured description of the automation workflow based on the unedited notes in `01-original-workflow-notes.md`.  
It uses technical accuracy, consistent terminology, and global English best practices.

---

## 1. Purpose

This automation workflow processes incoming ClickUp tasks and synchronizes them with a Google Sheet and a Smartsheet. The system ensures that:

1. New ClickUp tasks are captured through a webhook.  
2. Google Sheets is checked for existing entries to prevent duplicates.  
3. New records are added to Google Sheets as needed.  
4. Smartsheet rows are retrieved, updated, or inserted based on the task data.

---

## 2. Preconditions

Before implementing this workflow, the following must be configured:

- A ClickUp webhook or form trigger that sends task data to Make.com  
- A Google Sheet containing a dedicated column for `list_id`  
- A Smartsheet with known numeric column IDs  
- Make.com modules authenticated with ClickUp, Google Sheets, and Smartsheet  
- A clear understanding of which ClickUp fields will be required for row creation or updates

---

## 3. Workflow Steps

### Step 1: Receive Event from ClickUp
- Use a Webhook module in Make.com to capture data from ClickUp.
- Collect fields such as:
  - Task name  
  - Task description  
  - List ID  
  - Assignee information (if present)

### Step 2: Store Key Values in Variables
Use a variable module to store the following:
- `list_id`
- `smartsheet_id`  
This ensures consistent mapping across subsequent modules.

---

### Step 3: Check Google Sheet for Existing ID
1. Use the "Search Rows" module to look for the `list_id`.  
2. Decision logic:
   - If a row exists: terminate the scenario.  
   - If no row exists: continue processing.

This prevents duplicate records and unnecessary API usage.

---

### Step 4: Add Row to Google Sheet
Insert a new row containing:
- `list_id`
- Timestamp or creation date
- Additional metadata from ClickUp as needed

---

### Step 5: Retrieve Smartsheet
1. Use the Smartsheet "Get Sheet" module with `smartsheet_id`.  
2. Identify whether a row for the given `list_id` exists.

---

### Step 6: Update or Insert Smartsheet Row
- If the row exists: use the "Update Row" module.  
- If the row does not exist: use the "Add Row" module.

All mappings must reference **numeric** Smartsheet column IDs, not column names.

---

### Step 7: Complete Scenario
Perform any cleanup actions such as resetting variables or logging status information.

---

## Editorial Improvements Applied

- Reordered steps into a logical, sequential workflow  
- Replaced ambiguous verbs and unclear references  
- Added missing context, dependencies, and preconditions  
- Standardized terminology for consistency  
- Eliminated vague speculation from original notes  
- Created a structured document that can serve as an SOP or training guide
