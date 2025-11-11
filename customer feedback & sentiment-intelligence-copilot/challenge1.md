# Challenge 1: Build a Foundational Customer Feedback Copilot Agent using Microsoft Copilot Studio
  
## Problem Statement

CX teams collect vast volumes of unstructured feedback from emails, chat transcripts, and social media posts without the capacity to process and act on them quickly. Manual review delays issue detection and insights, while disconnected tools prevent sentiment tracking across channels. This challenge focuses on building the foundation of an AI-powered Customer Feedback Assistant capable of collecting structured feedback and responding with helpful information.

## Goals

- Create a Microsoft Copilot Studio agent capable of collecting structured customer feedback.
- Add a simple FAQ experience for common customer support questions.
- Publish the Copilot as a web app and test sample queries.

## Datasets

- No uploads are required in this challenge.
- Optional sample FAQ text is available locally at `C:\datasets\customer_faq_samples.txt` for reference only.

## Challenge Objectives  

1. **Copilot Studio Access and Environment Setup**
   - Navigate to Power Platform portal and create a `developer` environment.
   - Login to Microsoft Copilot Studio portal and select the developer environment which is created earlier.

2. **Create a New Copilot Agent**
   - Click **+ New Agent**.
   - Name your agent: **CustomerFeedback-Foundation**.
   - Choose the Customer Experience category and proceed with default language and region.

3. **Topic Creation for Feedback Collection**
   - Add a new topic named **CollectFeedback**.
   - Set trigger phrases such as:
     - `Submit feedback`
     - `Share my experience`
     - `I want to report an issue`
   - Add question nodes to collect customer information and feedback details.
   - Include confirmation and thank-you messaging with reference ID generation.

4. **FAQ Topic Creation**
   - Add a new topic named **CustomerFAQs**.
   - Set trigger phrases such as:
     - `How do I contact support?`
     - `Where can I track my order?`
     - `What are your business hours?`
   - Add message nodes for common customer service responses.

5. **Testing the Agent**
   - Use the built-in **Test Chat** panel in Copilot Studio.
   - Test queries such as:
     - `I want to submit feedback about my recent experience.`
     - `How can I contact customer support?`

6. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.
 
## Success Criteria  

- The agent successfully collects structured customer feedback with confirmation messaging.
- The FAQ topic responds correctly to common customer questions.
- The web app is accessible without authentication.
- Validation passes successfully.

## Additional Resources

- [Microsoft Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)
- [Topics and Variables in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-create-edit-topics)
  
## Conclusion  

You have built the foundational layer of the Customer Feedback & Sentiment Intelligence Copilot that can collect feedback and answer FAQs intelligently using Copilot Studio. In the next challenge, you'll integrate Power Automate and Logic Apps for multi-channel feedback processing and sentiment analysis.