# Challenge 3: Add Intelligence with Azure AI Foundry & AI Search for Predictive Maintenance Analytics
  
## Problem Statement

Maintenance teams need to go beyond reactive monitoring—they require intelligent insights from equipment data to predict failures, optimize maintenance schedules, and reduce downtime proactively. In this challenge, you'll connect Azure AI Foundry and Azure AI Search to create a unified intelligence layer that provides conversational analytics, predictive insights, and maintenance optimization recommendations from equipment telemetry and historical data.

## Goals

- Deploy Azure AI Foundry models for advanced equipment analysis and failure prediction.
- Build an Azure Function that authenticates calls from Copilot and returns intelligent maintenance insights.
- Use Azure AI Search to index and query equipment data for contextual responses and trend analysis.
- Visualize equipment health metrics and predictive alerts via Azure Monitor dashboards.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\equipment_history.csv`.
- This dataset contains historical equipment performance data, maintenance records, and failure patterns for predictive analysis.

## Challenge Objectives  

1. **Azure AI Foundry Setup**
   - In the Azure portal, create a new **Azure AI Foundry project** named `MaintenanceInsights-Foundry`.
   - Under **Language Models**, deploy:
     - **gpt-4o-mini** (for failure prediction and maintenance recommendations).
     - **text-embedding-3-small** (for equipment similarity analysis and pattern recognition).
   - Note the endpoint and API key for later use.

2. **Azure AI Search Setup**
   - Create a **Standard (S1)** tier **Azure AI Search** resource.
   - Use the **Import Data Wizard** to index `C:\datasets\equipment_history.csv`.
   - Set index name as **maintenance-insights-index**.
   - Configure searchable and filterable fields (equipment ID, failure type, maintenance actions, timestamps).
   - Validate that documents are properly indexed.

3. **Azure Function Connector**
   - Create an **Azure Function** named `maintenance-insights-func` using HTTP trigger.
   - Implement function endpoints:
     - `POST /failure-prediction` → Query AI Search for equipment patterns, call Foundry for failure risk analysis, return predictions.
     - `POST /maintenance-optimization` → Analyze maintenance schedules and provide optimization recommendations.
     - `POST /equipment-insights` → Generate equipment health summaries and proactive maintenance suggestions.
   - Configure authentication between the Function and Azure services (AI Search, AI Foundry).
   - Test each endpoint to ensure valid responses.

4. **Copilot Studio Integration**
   - In **Copilot Studio**, add a new topic named **MaintenanceInsights**.
   - Define trigger phrases such as:
     - `Predict equipment failures this month`
     - `Show me maintenance optimization suggestions`
     - `Analyze equipment performance trends`
   - Add an **Action Node** to call your Azure Function HTTP endpoint.
   - Configure authentication and pass query parameters from the conversation.
   - Parse the function response and display structured insights and predictive recommendations.

5. **Telemetry and Observability**
   - Enable **Application Insights** for your Azure Function App.
   - Configure custom telemetry to track key metrics (prediction accuracy, query volume, response times).
   - Create an **Azure Monitor Dashboard** to visualize:
     - Equipment health trends and failure predictions.
     - Maintenance scheduling optimization metrics.
     - Average function response time and success rates.
     - Copilot usage analytics by maintenance topic category.
   - Set up alerts for critical thresholds (equipment failure predictions, performance degradation).

6. **Testing**
   - Ask Copilot:
     - `Predict which equipment needs maintenance this week.`
     - `What are the optimization recommendations for our maintenance schedule?`
     - `Show me equipment failure risk analysis.`
   - Verify that insights, predictions, and optimization recommendations are returned accurately.

7. **(Optional) Proactive Maintenance Scheduling**
   - Extend the Azure Function to return actionable maintenance schedules based on predictive insights.
   - Display scheduling recommendations as a formatted section in Copilot responses.

## Success Criteria  

- Copilot returns readable **failure predictions**, **maintenance optimization**, and **equipment insights** based on historical equipment data.
- Azure Function successfully authenticates and calls Foundry and AI Search.
- Azure Monitor dashboard displays live equipment metrics and predictive alerts.
- Validation passes successfully.

## Additional Resources

- [Azure AI Foundry (model deployments)](https://learn.microsoft.com/en-us/azure/ai-studio/)
- [Use Azure OpenAI with your data (RAG quickstart)](https://learn.microsoft.com/en-us/azure/ai-services/openai/use-your-data-quickstart)
- [Application Insights + Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)

## Conclusion  

You've delivered an **intelligent Predictive Maintenance Assistant**: knowledge-grounded Q&A, Power Automate operational flows, and AI-powered analytics for equipment insights and failure prediction. This completes the maintenance automation loop from monitoring to action to strategic insights, demonstrating how Foundry and Copilot Studio can transform industrial maintenance operations.