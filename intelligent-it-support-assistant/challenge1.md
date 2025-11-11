# Challenge 1: Build a Foundational IT Support Copilot Agent using Microsoft Copilot Studio
  
## Problem Statement

Enterprises face high volumes of repetitive IT support requests such as password resets, connectivity issues, or application access. Traditional manual triage results in longer response times and reduced productivity. This challenge focuses on building the foundation of an AI-powered IT Support Assistant capable of understanding user queries and responding with helpful information drawn from enterprise knowledge bases.

## Goals

- Create a Microsoft Copilot Studio agent capable of answering IT-related FAQs.
- Connect it with a local dataset (Excel or CSV) that contains IT support FAQs and resolution steps.
- Publish the Copilot as a web app and test sample queries.

## Datasets  

- Use the pre-provided dataset located in `C:\datasets\it_faq_data.xlsx`.
- This dataset contains sample IT support FAQs and troubleshooting steps.

## Challenge Objectives  

1. **Copilot Studio Access and Environment Setup**
   - Navigate to Power Platform portal and create a `developer` environment.
   - Login to Microsoft Copilot Studio portal and select the developer environment which is created earlier.

2. **Create a New Copilot Agent**
   - Click **+ New Agent**.
   - Name your agent: **ITSupportAssistant-Foundation**.
   - Choose the IT Operations category and proceed with default language and region.

3. **Topic Creation**
   - Add a new topic named **ITFAQs**.
   - Set trigger phrases such as:
     - `I forgot my password`
     - `I can't access my email`
     - `How do I install Teams?`
   - Add message nodes for sample responses.

4. **Knowledge Source Integration**
   - From the **Knowledge** section, choose **Add data source**.
   - Upload or connect the Excel file from `C:\datasets\it_faq_data.xlsx`.
   - Select relevant columns as the question and answer fields.

5. **Testing the Agent**
   - Use the built-in **Test Chat** panel in Copilot Studio.
   - Test queries such as:
     - `My laptop is not connecting to Wi-Fi.`
     - `How do I reset my password?`

6. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.
 
## Success Criteria  

- The agent successfully responds to IT-related queries using the dataset.
- The web app is accessible without authentication.
- Validation passes successfully.

## Additional Resources

- [Microsoft Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)
- [Connect knowledge sources in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge)
  
## Conclusion  

You have built the foundational layer of the IT Support Assistant Copilot that can answer FAQs intelligently using Copilot Studio. In the next challenge, you'll integrate Power Automate for ticket creation and escalation workflows.
