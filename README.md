# Customer-Support-Agent
📞 Customer Support Automation – n8n Workflow

This workflow automatically handles customer support messages, classifies them using AI, and logs every case into Google Sheets.

⭐ Overview

The workflow receives customer messages through a webhook, checks the data, processes it using AI (Google Gemini), and then stores the results in Google Sheets.
It can also detect whether a ticket is open or already solved using a Switch node.

🔄 Full Workflow Breakdown
1️⃣ Webhook → Receive Customer Message

The workflow starts when a message arrives from your chatbot / WhatsApp / support form.

The message is captured as JSON (name, email, message, ticket ID, etc.).

2️⃣ HTTP Request Nodes (API Calls)

You have two HTTP Request nodes:

One validates customer details

One fetches previous ticket info or any related data

This helps AI understand context better.

3️⃣ JavaScript Code Nodes (Data Cleaning)

Two Code nodes are used for:

Formatting the message

Removing unwanted fields

Preparing clean input for AI processing

These ensure the AI receives perfect structured data.

4️⃣ Switch Node — Ticket Routing

The Switch node checks:

Is this ticket already solved?

Is this a new ticket?

Then it sends the workflow down different paths.

🧠 Path A — Ticket Not Solved (Active Ticket)
5️⃣ AI Agent (Google Gemini)

This agent:

Reads the customer message

Understands intent

Generates an appropriate reply

Decides if follow-up actions are needed

6️⃣ JavaScript Node (Final Formatting)

Formats AI output into a clean JSON object.

7️⃣ HTTP Request (Send Back to Chat App)

Sends the AI-generated reply back to:

WhatsApp

Web chatbot

Email

Any system connected

8️⃣ Append Row in Google Sheet

Every interaction is saved with:

Customer name

Message

AI reply

Status

Timestamp

This creates a full conversation log.

🧠 Path B — Ticket Already Solved
5️⃣ AI Agent1 (Follow-up AI)

This AI responds differently:

A polite message saying the ticket is already resolved

Or a follow-up message (survey, feedback request, etc.)

6️⃣ Append Row in Google Sheet (Solved Log)

Logs solved ticket interactions in the sheet.

📊 Final Output

Your system now automatically:

✔ Reads customer messages
✔ Understands intent with AI
✔ Replies instantly
✔ Routes solved vs unsolved tickets
✔ Logs everything in Google Sheets

This makes it a fully automated AI customer support agent.
