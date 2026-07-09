Here's a complete, production-ready README.md for your AI email agent workflow. Everything is ready to copy-paste directly into GitHub:


# 📧 AI-Powered Email Agent

An intelligent n8n workflow that automatically generates and sends personalized emails to managers, stakeholders, and teams based on natural language prompts. Built with n8n's AI Agent node and OpenAI's GPT-4o-mini.

![n8n](https://img.shields.io/badge/n8n-0.238.0+-%23EA4B71)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-%23412991)
![Gmail](https://img.shields.io/badge/Gmail-API-%23EA4335)
![License](https://img.shields.io/badge/License-MIT-green)

---

## ✨ Features

- 🧠 **Natural Language Processing** – Accepts human prompts to understand email context and recipients
- 🤖 **AI-Generated Emails** – Uses OpenAI GPT-4o-mini to craft professional, context-aware messages
- 📤 **Automated Gmail Sending** – Seamlessly delivers emails through Gmail integration
- 💬 **Conversation Memory** – Maintains context using Simple Memory node for coherent multi-turn interactions
- ⚡ **Real-time Chat** – On Chat Message node enables interactive prompting
- 🔒 **Safe & Ethical** – Built-in guardrails prevent spam, phishing, and harmful content

---

## 🧩 Workflow Nodes

| Node | Purpose |
|------|---------|
| **On Chat Message** | Triggers workflow when user submits a prompt via chat |
| **AI Agent** | Orchestrates the email generation logic |
| **OpenAI Chat Model** | GPT-4o-mini for natural language understanding and generation |
| **Simple Memory** | Retains conversation history for context |
| **Gmail** | Sends generated emails to recipients |

---

## 🤖 System Prompt

The AI agent uses this system prompt to guide email generation:

<details>
<summary><b>Click to expand the full system prompt</b></summary>

```

You are an AI Email Assistant responsible for generating and sending professional emails.

Your Role:

· Analyze the user's request and any provided recipient data
· Draft clear, professional, and personalized emails
· Adapt tone based on context (business, sales, support, networking, recruitment, etc.)

Email Structure:

· Subject: Concise, compelling, and relevant
· Body: Friendly, professional, human-like, and action-oriented
· Signature: Include "Best Regards, <Sender Name>"

Key Rules:

· Always use the recipient's name when available
· Keep emails concise and focused on one main action
· Automatically correct grammar, spelling, and formatting
· Include a clear call-to-action when appropriate
· NEVER fabricate information not provided in the input
· Maintain professionalism at all times
· Do NOT send spam, phishing, misleading, or harmful content
· Ask for missing information if critical details are absent

Decision Logic:

· If recipient name is missing → Use "Dear Team" or "Hello"
· If context is unclear → Ask clarifying questions
· If email is urgent → Flag it with [URGENT] in subject

Success Criteria:

· Professionalism ✓
· Personalization ✓
· Clarity ✓
· Ethical communication ✓
· High response rates ✓

Output Format:

```
Subject: <Generated Subject>

<Generated Email Body>

Best Regards,
<Sender Name>
```

```
</details>

---

## 🚀 Prerequisites

Before you begin, ensure you have:

- [ ] n8n instance (self-hosted or cloud)
- [ ] OpenAI API key with GPT-4o-mini access ([Get API Key](https://platform.openai.com))
- [ ] Gmail account with API enabled
- [ ] Node.js 18+ (if self-hosting)

---

## 🔧 Setup Instructions

### Step 1: Clone the Repository

```bash
git clone https://github.com/narasimhaislavath09/EmailSender-AI Agent-n8n.git
cd your-repo-name
```

Step 2: Import Workflow to n8n

1. Open your n8n instance
2. Click the three dots (···) in the top-right corner
3. Select "Import from File"
4. Choose the workflow.json file from this repository
5. Review the nodes and connections

Step 3: Configure Credentials

OpenAI API

1. Navigate to n8n Credentials → OpenAI API
2. Click "Add New"
3. Enter your API key (get it from platform.openai.com)
4. Model: gpt-4o-mini (or your preferred model)
5. Click "Save"

Gmail

1. Navigate to n8n Credentials → Gmail OAuth2
2. Click "Add New"
3. Follow the OAuth authentication flow
4. Grant necessary permissions (sending emails)
5. Click "Save"

Step 4: Customize the Agent (Optional)

Update the System Prompt

1. Open the AI Agent node
2. Go to Options → System Prompt
3. Modify the prompt to match your tone, style, or instructions
4. Click "Save"

Set Default Recipients

· In the Gmail node, configure To, CC, or BCC fields
· Or pass them dynamically from user prompts

Step 5: Activate the Workflow

1. Toggle the Active switch in n8n
2. Send a test prompt via the chat interface
3. Verify email delivery

---

📖 Usage Examples

Prompt Agent Action
"Send a progress update to John about the Q3 project" Drafts and sends update email to John
"Remind the finance team about the budget deadline" Creates reminder email for the finance team
"Follow up with Sarah about her pending approval" Generates follow-up email to Sarah
"Send a thank you note to all Q3 contributors" Drafts appreciation email to multiple recipients
"Draft a meeting request for next Tuesday with the product team" Creates meeting invitation email

---

🛠️ Customization Tips

Change AI Model

· Open the OpenAI Chat Model node
· Change the model to gpt-4-turbo, gpt-3.5-turbo, or any other supported model
· Adjust temperature and max tokens as needed

Add Email Validation

· Insert an IF node before the Gmail node
· Validate recipient email format, subject length, or content
· Prevent accidental sending of incomplete emails

Log Activities

· Add an Execute Workflow node
· Connect to Airtable, Google Sheets, or a database
· Track email history and response rates

Improve Memory

· Replace Simple Memory with Window Buffer Memory
· Store more conversation history for complex multi-turn interactions

Add Attachments

· Insert a Binary Data node before the Gmail node
· Attach files dynamically based on user prompts

---

🔒 Security Notes

⚠️ Important: The workflow.json file exported from n8n contains credential names and may include sensitive headers.

Do Don't
✅ Store API keys in n8n credentials ❌ Hardcode keys in workflow nodes
✅ Review JSON before committing ❌ Push sensitive data to GitHub
✅ Use .gitignore for secrets ❌ Share your actual Gmail credentials
✅ Anonymize sample data ❌ Include real emails in examples

Recommended .gitignore

```
*.log
node_modules/
.env
*.pem
*.key
Thumbs.db
.DS_Store
```

---

📁 Repository Structure

```
your-repo/
├── README.md              # This file
├── workflow.json          # Exported n8n workflow
├── SYSTEM_PROMPT.md       # Full system prompt (optional)
├── assets/               # Screenshots and diagrams
│   ├── workflow-overview.png
│   └── sample-email.png
└── LICENSE               # MIT License
```

---

🐛 Troubleshooting

Common Issues

Problem Solution
"Invalid API Key" Check OpenAI credentials and billing
"Gmail authentication failed" Re-authenticate OAuth2 and check permissions
"No recipient specified" Ensure recipient name/email is in the prompt
"Email not sending" Check Gmail quota limits (500/day)
"Memory not working" Enable Simple Memory and check session ID

Testing Locally

```bash
# Run n8n locally with Docker
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

---

🤝 Contributing

Contributions are welcome! Here's how:

1. Fork the repository
2. Create your feature branch: git checkout -b feature/amazing-feature
3. Commit changes: git commit -m 'Add amazing feature'
4. Push: git push origin feature/amazing-feature
5. Open a Pull Request

---

📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

🙏 Acknowledgments

· Built with n8n.io - The workflow automation tool
· OpenAI GPT-4o-mini for natural language processing
· Gmail API for email delivery
· The open-source community for inspiration and support

---

📞 Support

· n8n Documentation: docs.n8n.io
· OpenAI Docs: platform.openai.com/docs
· Gmail API Docs: developers.google.com/gmail/api
· Issues: GitHub Issues



Made with ❤️ by [Narasimha Islavath]


