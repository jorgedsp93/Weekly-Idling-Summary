# Weekly Idling Summary Email

This Google Apps Script automates a **weekly summary email** of employee idling times recorded in a Google Sheet.  
It compiles daily totals (Monday to Friday), aggregates weekly totals, and sends a formatted email with the results.

---

## Features
- Reads idling data from a Google Sheet named **`idle`**.
- Summarizes idle minutes **per user per day**.
- Includes:
  - Daily breakdown by employee
  - Daily total idle minutes
  - Weekly total idle minutes
- Sends the summary via email in **HTML format**.
- Runs automatically every **Friday at 5 PM** (configurable).

---

## Requirements
- Google Workspace account with:
  - Access to Google Sheets
  - Access to Gmail / MailApp
- A sheet named **`idle`** with the following columns (minimum):
  1. **User** – employee name  
  2. **Idle Time** – idle duration in minutes (e.g., `"15 minutes"`)  
  3. **Date** – the date of the idling event  

---

## Setup
1. Open [Google Apps Script](https://script.google.com/).
2. Paste the contents of `Code.gs` into the editor.
3. Adjust the **recipient email** if needed:
   ```javascript
   const emailAddress = "";
Save the script.

Running
To test manually, run:

javascript
Copy code
weeklyIdlingSummaryEmail();
To enable automation, run:

javascript
Copy code
setTriggerForWeeklyEmail();
This creates a time-based trigger to send the report every Friday at 5 PM.

Example Email Output
html
Copy code
<b>Idling Summary</b><br><br>
<b>Date: 08/25/25</b><br>
Alice idled for a total of 20 minutes<br>
Bob idled for a total of 15 minutes<br>
<b>Total Idle time for the day: 35 minutes</b><br><br>

<b>Date: 08/26/25</b><br>
Alice idled for a total of 10 minutes<br>
<b>Total Idle time for the day: 10 minutes</b><br><br>

<b>Total Idle for the week: 45 minutes</b><br>
Notes
Only Monday–Friday records are included. Weekend data is ignored.

Dates are formatted as MM/dd/yy.

The script expects idle times in the format:
"15 minutes", "30 minutes", etc. (first number is extracted).

If no idling data exists for the week, no email is sent.

Disclaimer
This script sends live emails. Test on a copy of your data or with a test email address before deploying in production.
