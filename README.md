M Solutions – AI-Powered Email Automation
This project automates email replies to incoming leads based on their query (notes) and status using n8n and an AI model (via Groq, OpenAI, or Vapi). It personalizes each email using lead information and dynamically generates human-like responses.

🚀 Features
✅ Reads lead data from Google Sheets or Excel
✅ Uses AI to generate professional replies using user Notes & Status
✅ Sends dynamic emails to the lead's email address
✅ Clean, branded HTML email format
✅ Logs or updates the result (optional)

📦 Prerequisites
n8n installed (self-hosted or cloud)

An AI API key (Groq, OpenAI, or Vapi)

SMTP credentials (for sending email)

Google Sheets or Excel file with leads

[Optional] HTML email template (included)

🧾 Lead Sheet Format (Required Columns)
Name	Email	Notes	Status	…
Ravi	ravi@email.com	Interested in digital branding	New Lead	
Priya	priya@email.com	Asked about SEO packages	Chatted	

These fields will be passed into the AI prompt to generate the email.

⚙️ Workflow Components
Cron Trigger (optional): Runs every X minutes

Read Excel/Google Sheet

Function Node: Extracts Name, Email, Notes, Status

AI Agent (Groq or OpenAI): Uses systemPrompt with lead info

Set Node: Extracts email and message

Send Email Node:

To: {{$json.email}}

Subject: “Thank you for contacting IM Solutions”

Content Type: HTML

Body: uses {{$json.answer}} or formatted HTML template

🧠 Sample AI System Prompt
You are a professional assistant at IM Solutions, a full-service advertising and digital agency. Use the lead’s status and notes to generate a helpful, polite email. Only use relevant company information — avoid listing all services.

Example fields:

Name: Ravi

Status: Chatted

Notes: Interested in SEO for real estate projects

→ AI should respond accordingly with a clear and useful email.

📤 Email Subject Suggestions
“Thank you for contacting IM Solutions”

“Regarding your inquiry: {{$json.Notes}}”

“Helping you move forward with your marketing needs”

🧾 HTML Email Template
✔️ Responsive
✔️ Clean brand design
✔️ Injects: Name & AI-generated message
✔️ Footer with contact info

Available in: email_template.html

✅ How to Run
Import the provided workflow JSON into n8n

Connect your AI credentials

Set your email credentials (SMTP / Gmail / SendGrid)

Test on one row of your Google Sheet or Excel

Monitor results and update the workflow if needed

📝 Optional Enhancements
Update “EmailStatus” back in the sheet (e.g., Sent / Failed)

Add error handling for failed AI or email steps

Add webhook trigger for real-time chatbot-to-email
