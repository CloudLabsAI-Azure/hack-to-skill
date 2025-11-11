## Stage 3: Intelligence

# Challenge: Add Intelligence to the IT Support Assistant using Azure AI Foundry and Azure AI Search
  
## Problem Statement

Modern IT assistants must go beyond automation they should understand, analyze, and recommend. In this challenge, you'll integrate Azure AI Foundry, Azure AI Search, and Azure Monitor with your Copilot to enable contextual reasoning, intelligent ticket analysis, and support trend insights.

## Goals

- Connect Azure AI Foundry model to analyze IT tickets.
- Build a retrieval-augmented response system for intelligent troubleshooting.
- Visualize telemetry insights using Azure Monitor dashboards.

## Datasets  

- Use the dataset in `C:\datasets\it_tickets_history.csv` to simulate ticket logs and support cases.
- This will be used for AI Search indexing and analysis.

## Challenge Objectives  

1. **Azure AI Foundry Setup**
   - In the Azure portal, create a new **Azure AI Foundry project** named `ITSupport-Foundry`.
   - Under **Language Models**, deploy:
     - **GPT-4-turbo** (for reasoning and summarization).
     - **Text-Embedding-3-small** (for vector creation).

2. **Azure AI Search Setup**
   - Create a **Standard (S1)** tier **Azure AI Search** resource.
   - Use the **Import Data Wizard** to index `C:\datasets\it_tickets_history.csv`.
   - Set index name as **it-support-index**.
   - Ensure the CSV file is properly formatted with consistent column headers and data types before importing.
   - Configure appropriate field mappings for searchable and filterable fields.
   - Validate that documents and fields are properly indexed.

3. **Azure Function Connector**
   - Create an **Azure Function** named `ticket-analyzer-func` using HTTP trigger (choose your preferred language).
   - Implement the function logic to:
     - Accept user query as input parameter.
     - Query Azure AI Search to retrieve similar historical tickets.
     - Call Azure AI Foundry model endpoint for analysis and summarization.
     - Return recommended resolution with confidence scores.
   - Configure authentication between the Function and Azure services (AI Search, AI Foundry).
   - Test the function endpoint to ensure it returns valid responses.

4. **Copilot Studio Integration**
   - In **Copilot Studio**, add a new topic named **IntelligentAnalysis**.
   - Define appropriate trigger phrases for intelligent analysis requests.
   - Add an **Action Node** to call your Azure Function HTTP endpoint.
   - Configure authentication and pass required parameters (user query, context) from the conversation to the function.
   - Parse the function response and display the AI-generated insights and recommendations in a user-friendly format.
   - Test the integration end-to-end within the Copilot test panel.

5. **Telemetry and Observability**
   - Enable **Application Insights** for your Azure Function App.
   - Configure custom telemetry to capture relevant metrics (request counts, response times, errors).
   - Create an **Azure Monitor Dashboard** to visualize:
     - Daily tickets analyzed and resolved.
     - Average AI function response time.
     - Common recurring issue categories.
     - Success and failure rates.
   - Set up alerts for critical thresholds (high error rates, performance degradation).

6. **Testing**
   - Ask Copilot:
     - `Analyze recent network issues and suggest top 3 causes.`
     - `Summarize high-priority issues from last week.`
     - `Recommend preventive actions for repeated VPN failures.`

## Success Criteria  

- The Copilot provides intelligent recommendations using AI Foundry and AI Search.
- Azure Function returns summarized ticket analysis.
- Azure Monitor dashboard displays metrics successfully.

## Additional Resources

- [Azure AI Foundry Overview](https://learn.microsoft.com/en-us/azure/ai-studio/)
- [Use your data with Azure OpenAI](https://learn.microsoft.com/en-us/azure/ai-services/openai/use-your-data-quickstart)
- [Azure Monitor Dashboards](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)

## Conclusion  

You have successfully built an intelligent IT Support Copilot capable of reasoning over historical tickets, providing AI-driven insights, and surfacing analytics dashboards for support trends. Your assistant now combines conversational AI, automation, and observability completing the Intelligent IT Support lifecycle.
