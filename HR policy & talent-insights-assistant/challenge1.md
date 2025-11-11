# Challenge 1: Build a Foundational HR Policy Copilot Agent using Microsoft Copilot Studio
  
## Problem Statement

HR departments manage thousands of policy documents, FAQs, and benefits information scattered across emails and files. Employees face delays in finding accurate policy information leading to repeated questions and inconsistent guidance. This challenge focuses on building the foundation of an AI-powered HR Policy Assistant capable of answering employee queries using SharePoint as a centralized knowledge base.

## Goals

- Create a Microsoft Copilot Studio agent capable of answering HR policy related FAQs.
- Connect it with SharePoint pages/libraries as the assistant's knowledge source.
- Publish the Copilot as a web app and test common HR queries.

## Datasets / Prerequisites

- Use an existing SharePoint site in your tenant (e.g., **HR Hub**) or create a simple site with a few sample policy pages (Remote Work, Leave & Holidays, Benefits Overview).
- Optional sample text is available locally at `C:\datasets\hr_policies_samples\` for **copy-paste only** (no file uploads).

## Challenge Objectives  

1. **Copilot Studio Access and Environment Setup**
   - Navigate to Power Platform portal and create a `developer` environment.
   - Login to Microsoft Copilot Studio portal and select the developer environment which is created earlier.

2. **Create a New Copilot Agent**
   - Click **+ New Agent**.
   - Name your agent: **HRInsights-Foundation**.
   - Choose the HR category and proceed with default language and region.

3. **Prepare SharePoint Knowledge**
   - In SharePoint, ensure at least 3 pages exist with short content:
     - **Remote Work Policy** (eligibility, working hours, equipment reimbursement)
     - **Leave & Holidays** (annual leave, sick leave, public holidays)
     - **Benefits Overview** (health insurance, EAP, learning budget)
   - Tip: You may **copy small snippets** from `C:\datasets\hr_policies_samples\` into SharePoint pages (do **not** upload files).

4. **Knowledge Source Integration**
   - From the **Knowledge** section, choose **Add data source**.
   - Choose **SharePoint** and connect the **HR** site (pages/doc libraries).
   - Restrict to the HR policy pages you created/curated.
   - Set scope to **Only from this knowledge** to avoid web fallbacks.

5. **Topic Creation**
   - Add a new topic named **PolicyFAQs**.
   - Set trigger phrases such as:
     - `What is our remote work policy?`
     - `How much annual leave do I have?`
     - `What benefits are included?`
     - `Explain the sick leave policy`
   - Add a **Generative Answers** node configured to use **Knowledge** (SharePoint).

6. **Testing the Agent**
   - Use the built-in **Test Chat** panel in Copilot Studio.
   - Test queries such as:
     - `What's the new remote-work policy?`
     - `How many sick days do we get?`
     - `Summarize benefits for new hires.`

7. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.
 
## Success Criteria  

- The agent successfully responds to HR policy queries using SharePoint content only.
- The web app is accessible without authentication.
- Validation passes successfully.

## Additional Resources

- [Microsoft Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)
- [Connect knowledge sources in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge)
  
## Conclusion  


You have built the foundational layer of the HR Policy Copilot that can answer FAQs intelligently using Copilot Studio with SharePoint as the knowledge base. In the next challenge, you'll integrate Power Automate for feedback collection and compliance reminders.
