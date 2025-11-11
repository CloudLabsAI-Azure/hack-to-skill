## Stage 3: Intelligence

# Challenge: Add Intelligence with Azure AI Foundry & AI Search for Financial Document Analytics
  
## Problem Statement

Finance teams need to go beyond data extraction—they require intelligent insights from financial documents to drive strategic decisions and detect anomalies proactively. In this challenge, you'll connect Azure AI Foundry and Azure AI Search to create a unified intelligence layer that provides conversational analytics, spend trend detection, and executive summaries from financial document data.

## Goals

- Deploy Azure AI Foundry models for advanced financial document analysis and trend detection.
- Build an Azure Function that authenticates calls from Copilot and returns intelligent financial insights.
- Use Azure AI Search to index and query financial document data for contextual responses.
- Visualize financial metrics and anomalies via Azure Monitor dashboards.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\finance_records.csv`.
- This dataset contains historical financial transactions and extracted document data for analysis and insight generation.

## Challenge Objectives  

1. **Azure AI Foundry Setup**
   - In the Azure portal, create a new **Azure AI Foundry project** named `FinanceInsights-Foundry`.
   - Under **Language Models**, deploy:
     - **gpt-4o-mini** (for summarization and anomaly detection).
     - **text-embedding-3-small** (for similarity search and document clustering).
   - Note the endpoint and API key for later use.

2. **Azure AI Search Setup**
   - Create a **Standard (S1)** tier **Azure AI Search** resource.
   - Use the **Import Data Wizard** to index `C:\datasets\finance_records.csv`.
   - Set index name as **finance-insights-index**.
   - Configure searchable and filterable fields (vendor, amount, date, invoice number, payment status).
   - Validate that documents are properly indexed.

3. **Azure Function Connector**
   - Create an **Azure Function** named `finance-insights-func` using HTTP trigger.
   - Implement function endpoints:
     - `POST /spending-analysis` → Query AI Search for transaction data, call Foundry for spend analysis, return insights.
     - `POST /anomaly-detection` → Identify unusual transactions and generate alerts with explanations.
     - `POST /vendor-summary` → Group spending by vendor and provide executive summaries with recommendations.
   - Configure authentication between the Function and Azure services (AI Search, AI Foundry).
   - Test each endpoint to ensure valid responses.

4. **Copilot Studio Integration**
   - In **Copilot Studio**, add a new topic named **FinancialInsights**.
   - Define trigger phrases such as:
     - `Analyze spending trends this quarter`
     - `Show me vendor payment anomalies`
     - `Summarize invoice processing metrics`
   - Add an **Action Node** to call your Azure Function HTTP endpoint.
   - Configure authentication and pass query parameters from the conversation.
   - Parse the function response and display structured insights and recommendations.

5. **Telemetry and Observability**
   - Enable **Application Insights** for your Azure Function App.
   - Configure custom telemetry to track key metrics (query volume, response times, anomaly detection rates).
   - Create an **Azure Monitor Dashboard** to visualize:
     - Daily spending trends and vendor distributions.
     - Detected anomalies and their resolution status.
     - Average function response time and success rates.
     - Copilot usage analytics by financial topic category.
   - Set up alerts for critical thresholds (spending anomalies, performance issues).

6. **Testing**
   - Ask Copilot:
     - `Summarize spending patterns for this fiscal quarter.`
     - `What are the top 3 vendors by payment amount?`
     - `Detect any unusual invoice amounts this month.`
   - Verify that insights, summaries, and anomaly detection results are returned accurately.

7. **(Optional) Proactive Recommendations**
   - Extend the Azure Function to return actionable recommendations based on spending patterns.
   - Display recommendations as a formatted section in Copilot responses.

## Success Criteria  

- Copilot returns readable **spending analysis**, **anomaly detection**, and **vendor insights** based on financial document data.
- Azure Function successfully authenticates and calls Foundry and AI Search.
- Azure Monitor dashboard displays live financial metrics and anomaly alerts.
- Validation passes successfully.

## Additional Resources

- [Azure AI Foundry (model deployments)](https://learn.microsoft.com/en-us/azure/ai-studio/)
- [Use Azure OpenAI with your data (RAG quickstart)](https://learn.microsoft.com/en-us/azure/ai-services/openai/use-your-data-quickstart)
- [Application Insights + Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)

## Conclusion  

You've delivered an **intelligent Finance Document Insight Copilot**: knowledge-grounded Q&A, Power Automate operational flows, and AI-powered analytics for financial insights and anomaly detection. This completes the finance automation loop from document processing to action to strategic insights, demonstrating how Foundry and Copilot Studio can transform financial operations.