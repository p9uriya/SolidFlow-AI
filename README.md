# 🚀 SolidFlow AI — Telegram Engineering Hub

**An AI-powered engineering assistant for mechanical design teams, built with n8n, Telegram, and OpenAI.**

SolidFlow AI transforms Telegram into a centralized interface for engineering questions, drawing analysis, task management, approval workflows, and engineering activity tracking.

The project combines AI-assisted analysis with structured data management and role-based controls to create a more organized and traceable engineering workflow.

## ✨ Key Features

- **🔐 Access Control:** Restricts bot access to registered Telegram users and supports user roles.
- **💬 AI Engineering Assistant:** Answers engineering questions using an AI agent with conversational memory.
- **📐 Drawing Inspector:** Processes image attachments through vision-based AI analysis.
- **📄 PDF Analysis:** Extracts available text from PDF files before sending it for analysis.
- **📋 Structured Engineering Reports:** Organizes analysis results using a defined output schema.
- **⚙️ Job Management:** Creates and tracks engineering jobs with identifiable statuses.
- **✅ Approval Workflow:** Supports job approval and rejection with permission and transition checks.
- **🕘 Job History:** Retrieves jobs and their associated event timelines.
- **🛠️ Admin Tools:** Supports administrative statistics and user management.
- **🧾 Audit Logging:** Records important job events and operational errors.
- **📱 Interactive Telegram UI:** Uses inline keyboards for navigation and job actions.

## 🧩 Engineering Modules

The bot interface is organized around eight engineering modules:

1. Assembly Automation
2. AI Drawing Inspector
3. 2D-to-3D Workflow
4. Sheet Metal
5. BOM & Cost
6. Parametric Part
7. Export & Convert
8. Design Revision

These modules define the engineering service interface. Actual CAD generation and file conversion require additional CAD-agent integration.

## 🏗️ Architecture

```text
Telegram User
     |
     v
Telegram Trigger
     |
     v
Normalize Incoming Update
     |
     v
User Lookup & Authorization
     |
     +---- Unauthorized --> Access Denied
     |
     v
Session & Action Routing
     |
     +---- AI Engineering Chat
     |
     +---- Image / PDF Analysis
     |
     +---- Job Approval / Rejection
     |
     +---- Job History
     |
     +---- Admin Operations
     |
     v
Data Persistence & Event Logging
     |
     v
Telegram Response
```

## 🗄️ Data Model

SolidFlow AI uses four n8n Data Tables:

| Table | Purpose |
|---|---|
| `Users` | Registered users, roles, and access control |
| `Sessions` | Current page and interaction state |
| `Jobs` | Engineering requests, reports, and statuses |
| `Job Events` | Job actions, approvals, rejections, and events |

## 🧰 Technology Stack

- **Workflow Automation:** n8n
- **User Interface:** Telegram Bot API
- **AI Processing:** OpenAI API
- **Vision Analysis:** Vision-capable OpenAI model
- **Document Processing:** PDF text extraction
- **Data Persistence:** n8n Data Tables
- **Workflow Controls:** Role checks, job-state validation, and event logging

## ⚙️ Setup

### Prerequisites

- An n8n Cloud or self-hosted instance
- A Telegram bot created through BotFather
- An OpenAI API key and access to a compatible model
- The required n8n Data Tables
- The workflow JSON file included in this repository

### Installation

1. Import the workflow JSON into n8n.
2. Configure Telegram and OpenAI credentials.
3. Create the `Users`, `Sessions`, `Jobs`, and `Job Events` tables.
4. Configure the Data Table nodes to match your table names and fields.
5. Add your Telegram user ID to `Users` with the `admin` role.
6. Review node configuration, permissions, and AI model settings.
7. Publish or activate the workflow according to your n8n version.
8. Send `/start` to your Telegram bot and test each workflow branch.

> **Important:** Exact table fields and node settings must match the imported workflow. Validate credentials and configuration before production use.

## 🧪 Recommended Tests

- Authorized and unauthorized Telegram users
- Text-based engineering questions
- Image attachments and supported PDF documents
- Missing or invalid job IDs
- Approval attempts by unauthorized users
- Admin-only operations
- API failures and error logging
- Job history and event consistency

## 🛣️ Roadmap

- Windows-based CAD Agent
- SOLIDWORKS integration
- Automated CAD model and assembly generation
- Engineering drawing and report exports
- STEP export where supported by the CAD workflow
- Web dashboard for job monitoring and administration
- Human approval checkpoints for sensitive engineering operations

## 🔒 Security Notes

- Store API keys and bot tokens in n8n Credentials.
- Never commit secrets, tokens, or private user data.
- Apply least-privilege access to administrative operations.
- Validate incoming files and user inputs.
- Test authorization and job-state transitions before deployment.

## 📌 Project Status

**MVP Plus — AI-assisted engineering workflow hub**

The current scope focuses on Telegram interaction, AI-assisted analysis, structured job tracking, authorization, and auditability. Direct SOLIDWORKS automation and actual CAD file generation are planned extensions, not guaranteed features of the current workflow.

## 📄 License

MIT — include the corresponding `LICENSE` file in this repository if you distribute the project under the MIT License.

---

**Built for smarter engineering workflows.**
