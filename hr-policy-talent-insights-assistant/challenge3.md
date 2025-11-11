## Stage 3: Intelligence

# Challenge: Add Talent Insights with Azure AI Foundry & AI Search (Sentiment, Summaries, Trends)
  
## Problem Statement

HR analysts spend hours manually summarizing engagement survey responses and spotting sentiment trends. In this challenge, you'll connect **Azure AI Foundry** and **Azure AI Search** via an **Azure Function façade** to deliver on-demand summaries, sentiment insights, and trend highlights—plus dashboards for HR metrics.

## Goals

- Deploy a GPT-4o-class model in Azure AI Foundry for sentiment analysis and summarization.
- Build an Azure Function that authenticates calls from Copilot and returns intelligent insights.
- Use Azure AI Search to index and query employee engagement survey data.
- Visualize HR metrics via Azure Monitor dashboards.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\hr_engagement_survey.csv`.
- This dataset contains employee engagement survey responses with feedback text, ratings, and timestamps for sentiment analysis and trend detection.

## Challenge Objectives  

1. **Azure AI Foundry Setup**
   - In the Azure portal, create a new **Azure AI Foundry project** named `HRInsights-Foundry`.
   - Under **Language Models**, deploy:
     - **gpt-4o-mini** (for sentiment analysis and summarization).
     - **text-embedding-3-small** (for vector embeddings).
   - Note the endpoint and API key for later use.

2. **Azure AI Search Setup**
   - Create a **Standard (S1)** tier **Azure AI Search** resource.
   - Use the **Import Data Wizard** to index `C:\datasets\hr_engagement_survey.csv`.
   - Set index name as **hr-engagement-index**.
   - Ensure the CSV file has consistent column headers and proper formatting before importing.
   - Configure searchable and filterable fields (feedback text, rating, department, timestamp).
   - Validate that documents are properly indexed.

3. **Azure Function Connector**
   - Create an **Azure Function** named `hr-insights-func` using HTTP trigger (choose your preferred language).
   - Implement function endpoints:
     - `POST /sentiment-analysis` → Pull survey data from AI Search, call Foundry for sentiment classification (Positive/Neutral/Negative), return aggregated counts and sample quotes.
     - `POST /summarize-feedback` → Group feedback by department or policy topic, call Foundry for summary with key themes and recommendations.
     - `POST /detect-trends` → Query AI Search for recent survey responses, identify recurring keywords and sentiment shifts over time.
   - Configure authentication between the Function and Azure services (AI Search, AI Foundry).
   - Test each endpoint to ensure valid responses.

4. **Copilot Studio Integration**
   - In **Copilot Studio**, add a new topic named **TalentInsights**.
   - Define trigger phrases such as:
     - `Summarize employee sentiment this quarter`
     - `What are the top 3 HR pain points?`
     - `Any trends in feedback about benefits?`
   - Add an **Action Node** to call your Azure Function HTTP endpoint.
   - Configure authentication and pass query parameters from the conversation.
   - Parse the function response and display structured insights (sentiment breakdown, key themes, recommendations).
   - Test the integration end-to-end within the Copilot test panel.

5. **Telemetry and Observability**
   - Enable **Application Insights** for your Azure Function App.
   - Configure custom telemetry to track key metrics (sentiment query volume, response times, error rates).
   - Create an **Azure Monitor Dashboard** to visualize:
     - Daily sentiment distribution (Positive/Neutral/Negative percentages).
     - Top recurring themes from surveys.
     - Average function response time.
     - Copilot usage analytics (queries by topic category).
   - Set up alerts for critical thresholds (high error rates, performance degradation).

6. **Testing**
   - Ask Copilot:
     - `Summarize employee sentiment for remote work policy.`
     - `List top themes and recommendations from benefits feedback.`
     - `Highlight sentiment trends in engagement surveys this month.`
   - Verify that sentiment classifications, summaries, and trend insights are returned accurately.

7. **(Optional) Proactive Recommendations**
   - Extend the Azure Function to return a `RecommendedActions` list based on sentiment analysis (e.g., "Address concerns about remote work equipment", "Clarify benefits eligibility").
   - Display recommendations as a formatted section in Copilot responses.

## Success Criteria  

- Copilot returns readable **sentiment breakdowns**, **summaries**, and **trends** based on engagement survey data.
- Azure Function successfully authenticates and calls Foundry and AI Search.
- Azure Monitor dashboard displays live HR metrics.
- Validation passes successfully.

## Additional Resources

- [Azure AI Foundry (model deployments)](https://learn.microsoft.com/en-us/azure/ai-studio/)
- [Use Azure OpenAI with your data (RAG quickstart)](https://learn.microsoft.com/en-us/azure/ai-services/openai/use-your-data-quickstart)
- [Application Insights + Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)

## Conclusion  

You've delivered an **intelligent HR Policy & Talent Insights Assistant**: knowledge-grounded Q&A, Power Automate operational flows, and AI-powered analytics for sentiment and trends. This completes the HR automation loop from knowledge to action to insights, demonstrating how Foundry and Copilot Studio can transform HR operations.
