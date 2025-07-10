Overpass API Lead Extraction Workflow (n8n)
This workflow automatically extracts business emails using Overpass API and enriches them by visiting business websites when emails are not provided in the raw data.

📋 How it works step-by-step:
🧪 Trigger: Manual Execution

The flow starts when the "Execute workflow" button is clicked.

🌐 HTTP Request to Overpass API

Queries a specified region (for example, cafés in İzmir) and retrieves a list of businesses (nodes) with metadata like name, website, and possibly email.

🧠 Code Node

Processes the Overpass response, formats it into structured JSON with relevant fields like name, website, email, tags, etc.

🧹 Remove Duplicates

Filters out duplicate business entries (likely by name or coordinates).

🔀 Conditional Check (IF)

Checks: Does the business already have an email address?

✅ If yes, sends it directly to the merge step.

❌ If no, continues with a secondary process to try and extract email from website.

🌐 HTTP Request to Website

If email is missing but a website is available, sends an HTTP GET request to the website.

📤 Code Extraction

A script scans the HTML content of the website for an email pattern using regex (like info@business.com).

✏️ Edit Fields

Cleans and normalizes the data for final storage.

🧩 Merge

Merges both email sources (from Overpass + scraped from website).

🚫 Filter Irrelevant URLs

Removes entries with suspicious or irrelevant domains (e.g., social media, ad pages).

📄 Google Sheets

Appends the final data into a connected Google Sheet for further use.


<img width="1141" height="349" alt="Ekran Resmi 2025-07-10 14 16 43" src="https://github.com/user-attachments/assets/6593621f-e1cd-4c88-b236-cc4c71db648f" />
