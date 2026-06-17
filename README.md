#QA Auto-Tracker

An automated CI/QA pipeline built with n8n that acts as a smart proxy between end-users and the QA/Development team. It parses unstructured user feedback from Telegram, classifies the intent, and automatically formats valid issues into standardized bug reports within a Notion database.

Built to minimize the time QA engineers spend deciphering incomplete descriptions and manually logging tickets.

![Workflow Architecture](скріншот_твого_воркфлоу.jpg) *(Заміни це посилання на назву твого файлу зі скріншотом)*

## Features

* **Smart Intent Classification:** Uses a lightweight LLM to distinguish between casual conversation/greetings and actual technical issues (handling negative testing scenarios).
* **Automated QA Formatting:** Converts raw, messy user text into a strict, standardized QA format.
* **Intelligent Extraction:** Automatically identifies and categorizes properties such as *Severity*, *Environment*, *Expected Result*, and *Steps to Reproduce*.
* **Database Synchronization:** Seamlessly pushes parsed JSON payloads directly into a Notion tracking board via API.

## Tech Stack

* **Automation Engine:** n8n (Docker / Self-hosted)
* **LLM / AI:** Google Gemini API (3.1 Flash-Lite for routing, 3.5 Flash for data extraction)
* **Integrations:** Telegram Bot API, Notion API
* **Data Processing:** JavaScript (Custom Code Nodes for JSON sanitation)

## Workflow Architecture

1. **Ingestion:** Telegram Trigger receives incoming messages.
2. **Intent Analysis:** Gemini 3.1 Flash-Lite analyzes the text. If the message is non-technical, the bot replies politely and asks for bug details.
3. **Data Extraction:** If an issue is detected, Gemini 3.5 Flash acts as a QA Engineer, extracting testing parameters and forming a structured JSON object.
4. **Sanitation:** A custom JavaScript node cleans the LLM output, ensuring strict JSON compliance.
5. **Storage:** The formatted data is mapped and pushed to a connected Notion Database as a new structured page.

## Setup Instructions

### Prerequisites
* An active n8n instance.
* A Telegram Bot Token (via BotFather).
* A Google Gemini API Key.
* A Notion Integration Secret.

### Installation
1. Clone this repository or download the `qa_tg_automation.json` file.
2. In your n8n workspace, click **Import from File** and select the JSON.
3. Set up your Credentials in n8n for:
   * `Telegram API`
   * `Google Gemini(PaLM) API`
   * `Notion API`
4. **Notion Setup:** Create a Notion database with the following properties (case-sensitive mapping):
   * `Bug title` (Title)
   * `Environment` (Select)
   * `Expected result` (Rich text)
   * `Severity` (Select)
   * `Steps to Reproduce` (Rich text)
5. Update the Notion node in n8n with your specific Database ID.
6. Click **Activate** (or Publish) to set the workflow live!

## 🎥 Demo
<img width="1087" height="554" alt="{52C26466-777F-4C5B-94AD-E3D8975DA647}" src="https://github.com/user-attachments/assets/01a94cdb-6ee9-4a1a-8fc7-9a0e06aa633b" />
<img width="905" height="215" alt="{5F22C4FD-074F-4AA6-A682-DE77078EF425}" src="https://github.com/user-attachments/assets/1cdd1176-8886-4f30-b533-21b49b1297db" />
<img width="1570" height="329" alt="{DC70FE88-4483-4906-85EF-DA1BBC5C5F77}" src="https://github.com/user-attachments/assets/a4d3cd88-12fc-4be9-90f4-f0c57c8fc70e" />


## Setup
1. Import `workflow.json` into your n8n instance.
2. Configure Telegram and Google Gemini API credentials.
3. Activate the workflow.
