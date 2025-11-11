# Challenge 3: Add Intelligence with Azure AI Foundry & AI Search for Customer Sentiment Analytics
  
## Problem Statement

Customer experience teams need to go beyond data collection and basic sentiment analysis—they require intelligent insights from multi-channel feedback to drive strategic decisions. In this challenge, you'll connect Azure AI Foundry and Azure AI Search to create a unified intelligence layer that provides conversational analytics, trend detection, and executive summaries from customer feedback data.

## Goals

- Deploy Azure AI Foundry models for advanced sentiment analysis and trend detection.
- Build an Azure Function that authenticates calls from Copilot and returns intelligent customer insights.
- Use Azure AI Search to index and query customer feedback data for contextual responses.
- Visualize customer sentiment metrics via Azure Monitor dashboards.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\customer_feedback_history.csv`.
- This dataset contains historical customer feedback with sentiment labels and timestamps for trend analysis and insight generation.

## Challenge Objectives  

1. **Azure AI Foundry Setup**
   - In the Azure portal, create a new **Azure AI Foundry project** named `CustomerSentiment-Foundry`.
   - Under **Language Models**, deploy:
     - **gpt-4o-mini** (for summarization and trend analysis).
     - **text-embedding-3-small** (for similarity search and clustering).
   - Note the endpoint and API key for later use.

2. **Azure AI Search Setup**
   - Create a **Standard (S1)** tier **Azure AI Search** resource.
   - Use the **Import Data Wizard** to index `C:\datasets\customer_feedback_history.csv`.
   - Set index name as **customer-feedback-index**.
   - Configure searchable and filterable fields (feedback text, sentiment, channel, timestamp).
   - Validate that documents are properly indexed.

3. **Azure Function Connector**
   - Create an **Azure Function** named `customer-insights-func` using HTTP trigger.
   - Implement function endpoints:
     - `POST /sentiment-trends` → Query AI Search for feedback data, call Foundry for trend analysis, return insights.
     - `POST /feedback-summary` → Group feedback by categories, call Foundry for executive summary with recommendations.
     - `POST /sentiment-alerts` → Detect sentiment anomalies and generate proactive alerts.
   - Configure authentication between the Function and Azure services (AI Search, AI Foundry).
   - Test each endpoint to ensure valid responses.

4. **Copilot Studio Integration**
   - In **Copilot Studio**, add a new topic named **CustomerInsights**.
   - Define trigger phrases such as:
     - `Summarize customer sentiment this month`
     - `What are trending customer concerns?`
     - `Show me feedback analysis for support issues`
   - Add an **Action Node** to call your Azure Function HTTP endpoint.
   - Configure authentication and pass query parameters from the conversation.
   - Parse the function response and display structured insights.

5. **Telemetry and Observability**
   - Enable **Application Insights** for your Azure Function App.
   - Configure custom telemetry to track key metrics (query volume, response times, sentiment distribution).
   - Create an **Azure Monitor Dashboard** to visualize:
     - Daily sentiment trends across channels.
     - Top customer concerns and feedback themes.
     - Average function response time and success rates.
     - Copilot usage analytics by topic category.
   - Set up alerts for critical thresholds (negative sentiment spikes, performance issues).

6. **Testing**
   - Ask Copilot:
     - `Summarize customer sentiment trends for this quarter.`
     - `What are the top concerns from email feedback?`
     - `Show me sentiment analysis for social media mentions.`
   - Verify that insights, summaries, and trend analysis are returned accurately.

7. **(Optional) Proactive Recommendations**
   - Extend the Azure Function to return actionable recommendations based on sentiment patterns.
   - Display recommendations as a formatted section in Copilot responses.

## Success Criteria  

- Copilot returns readable **sentiment trends**, **summaries**, and **insights** based on customer feedback data.
- Azure Function successfully authenticates and calls Foundry and AI Search.
- Azure Monitor dashboard displays live customer sentiment metrics.
- Validation passes successfully.

## Additional Resources

- [Azure AI Foundry (model deployments)](https://learn.microsoft.com/en-us/azure/ai-studio/)
- [Use Azure OpenAI with your data (RAG quickstart)](https://learn.microsoft.com/en-us/azure/ai-services/openai/use-your-data-quickstart)
- [Application Insights + Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)

## Conclusion  

You've delivered an **intelligent Customer Feedback & Sentiment Intelligence Copilot**: knowledge-grounded Q&A, Power Automate operational flows, and AI-powered analytics for sentiment trends and customer insights. This completes the customer experience automation loop from feedback collection to action to strategic insights, demonstrating how Foundry and Copilot Studio can transform CX operations.