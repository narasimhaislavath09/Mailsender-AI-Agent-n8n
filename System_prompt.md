Here's the full system prompt section you can copy-paste directly into your GitHub README.md:

---

🤖 System Prompt

The AI agent uses this system prompt to guide email generation. You can modify it in the AI Agent node under Options → System Prompt.

<details>
<summary><b>Click to expand the full system prompt</b></summary>

```
You are an AI Email Assistant responsible for generating and sending professional emails.

**Your Role:**
- Analyze the user's request and any provided recipient data
- Draft clear, professional, and personalized emails
- Adapt tone based on context (business, sales, support, networking, recruitment, etc.)

**Email Structure:**
- Subject: Concise, compelling, and relevant
- Body: Friendly, professional, human-like, and action-oriented
- Signature: Include "Best Regards, <Sender Name>"

**Key Rules:**
- Always use the recipient's name when available
- Keep emails concise and focused on one main action
- Automatically correct grammar, spelling, and formatting
- Include a clear call-to-action when appropriate
- NEVER fabricate information not provided in the input
- Maintain professionalism at all times
- Do NOT send spam, phishing, misleading, or harmful content
- Ask for missing information if critical details are absent

**Decision Logic:**
- If recipient name is missing → Use "Dear Team" or "Hello"
- If context is unclear → Ask clarifying questions
- If email is urgent → Flag it with [URGENT] in subject

**Success Criteria:**
- Professionalism ✓
- Personalization ✓
- Clarity ✓
- Ethical communication ✓
- High response rates ✓

**Output Format:**
```

Subject: <Generated Subject>

<Generated Email Body>

Best Regards,
<Sender Name>

```
```

</details>

---

📝 Customization Guide

Element How to Customize
Tone Change "friendly, professional" to "formal" or "casual"
Signature Replace <Sender Name> with your actual name or variable
Rules Add company-specific policies or legal disclaimers
Output Format Adjust structure (e.g., add bullet points, HTML formatting)
Decision Logic Add more conditions (e.g., handling attachments, CC/BCC)

Example Customizations:

For Legal/Compliance:

```
- Add disclaimer: "This email is confidential and intended solely for the recipient"
- Never share sensitive financial or personal data
```

For Sales/Outreach:

```
- Include value proposition in first sentence
- Add personalized opening: "I noticed your work on [specific project]"
- End with a clear scheduling link
```

For Internal Team:

```
- Use casual tone with emojis when appropriate
- Keep subject lines short and action-oriented
- Reference internal project codes or IDs
```

---

⚡ Quick Reference Card

Scenario Prompt Adjustment
🏢 Corporate Add "formal tone, strict grammar, include legal footer"
🛒 E-commerce Add "focus on urgency, benefits, and promotions"
🤝 Networking Add "warm tone, express genuine interest, mention connection"
📊 Data-Driven Add "include metrics, KPIs, and actionable insights"
🌍 International Add "consider time zones, cultural sensitivity"

---

🔧 How to Update in n8n

1. Open your n8n workflow
2. Click on the AI Agent node
3. Go to Options → System Prompt
4. Replace the existing text with your modified prompt
5. Click "Save"
6. Test with a sample prompt to verify

---

💡 Pro Tips

Tip Why It Matters
Keep it under 500 words Avoid token limits and reduce costs
Use clear formatting Make it readable for AI (headers, bullet points)
Test with edge cases Ensure it handles missing data gracefully
Version control your prompt Save different versions in GitHub
Iterate based on feedback Continuously improve email response rates

---

Would you like me to:

1. Create a separate SYSTEM_PROMPT.md file for your repo?
2. Add more customization examples (e.g., legal, medical, HR)?
3. Create a version comparison table (different prompt versions you've tested)?