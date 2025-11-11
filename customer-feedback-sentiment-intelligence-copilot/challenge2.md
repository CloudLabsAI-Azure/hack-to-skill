## Stage 2: Integration

# Challenge: Integrate Power Automate Tools within Copilot Studio for Customer Feedback Automation
  
## Problem Statement

While your foundational chatbot can collect feedback and answer FAQs, enterprise customer experience teams also require automated workflows to process multi-channel feedback efficiently. In this challenge, you will extend your Copilot agent to include sentiment analysis and alerting automation directly within the Copilot Studio portal using Power Automate connectors and Azure AI Language Services.

## Goals

- Automate customer feedback processing and sentiment analysis through Copilot Studio's integrated Power Automate tools.
- Enable Microsoft Teams based notifications for CX teams when negative sentiment is detected.
- Store and manage all feedback data within Dataverse in a structured format.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\customer_feedback_sample.csv`.
- This dataset contains sample feedback templates and metadata to simulate multi-channel customer feedback processing.

## Challenge Objectives  

1. **Set Up Azure AI Language Service**
   - Navigate to Azure portal and create a **Language Service** resource.
   - Complete the setup wizard and note down your **endpoint** and **API key**.
   - Enable **Sentiment Analysis** and **Key Phrase Extraction** features.
   - Familiarize yourself with the sentiment analysis API structure and response format.

2. **Open Copilot Studio and Access Power Automate Tools**
   - Launch **Microsoft Copilot Studio** from your Microsoft 365 portal.
   - Open the **CustomerFeedback-Foundation** agent you created in the previous challenge.
   - From the left navigation panel, go to **Tools → Power Automate** to view available connectors and builder options.

3. **Create a Power Automate Flow within Copilot Studio**
   - In Copilot Studio, navigate to **Tools → Power Automate → Create Flow**.
   - Name the flow **ProcessCustomerFeedback**.
   - Add the following steps:
     1. **Trigger:** Use **When a Copilot topic runs this flow**.
     2. **Action 1:** Add an **HTTP** action to call Azure AI Language Service for sentiment analysis.
     3. **Action 2:** Parse the sentiment response and extract sentiment score and classification.
     4. **Action 3:** Store the feedback and sentiment data in Dataverse.
     5. **Action 4:** Add a **Teams → Post message in a channel** action for negative sentiment alerts.

4. **Create Dataverse Table for Feedback Storage**
   - In your environment, create a new **Dataverse** table called **CustomerFeedback**.
   - Define columns for customer information, feedback text, sentiment analysis results, and timestamps.
   - Configure proper data types and relationships for efficient querying.

5. **Integrate the Flow into Your Copilot Agent**
   - In **Copilot Studio → Topics**, create or open a topic named **FeedbackProcessor**.
   - Add **Trigger phrases** like:
     - `Process my feedback`
     - `Analyze customer sentiment`
     - `Submit feedback for review`
   - Add a **Power Automate Action Node** to call the **ProcessCustomerFeedback** flow.
   - Map conversation variables to flow parameters and display confirmation messages.

6. **Testing the Agent**
   - Use the **Test your copilot** panel to simulate conversations such as:
     - `I had a terrible experience with your service today.`
     - `Process my feedback about the excellent support I received.`
   - Verify that sentiment analysis works correctly and Teams notifications are sent for negative feedback.

7. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.

## Success Criteria  

- The Copilot agent successfully triggers feedback processing flows within the Copilot Studio portal.
- Sentiment analysis correctly identifies positive, neutral, and negative feedback.
- Teams notifications are sent automatically when negative sentiment is detected.
- All feedback data is properly stored in Dataverse with sentiment labels.

## Additional Resources

- [Build flows directly in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/power-automate-integration)
- [Azure AI Language Service Documentation](https://learn.microsoft.com/en-us/azure/ai-services/language-service/overview)
- [Send messages to Teams channels using Power Automate](https://learn.microsoft.com/en-us/connectors/teams/)

## Conclusion  

You have enhanced your Copilot's functionality by integrating Power Automate connectors directly within Copilot Studio to automate customer feedback processing and sentiment analysis. Your Copilot is now capable of handling real-world CX automation workflows, paving the way for adding AI-driven insights and trend analysis in the next stage.