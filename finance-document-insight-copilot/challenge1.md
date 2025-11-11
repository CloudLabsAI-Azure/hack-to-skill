## Stage 1: Foundation

# Challenge: Build a Foundational Finance Document Insight Copilot using Microsoft Copilot Studio
  
## Problem Statement

Finance teams handle large volumes of invoices, statements, and audit reports spread across emails, PDFs, and spreadsheets. Manual extraction of key fields consumes hours and risks errors, while disconnected workflows limit visibility and data-driven financial decisions. This challenge focuses on building the foundation of an AI-powered Finance Document Assistant capable of answering finance-related queries and processing document uploads.

## Goals

- Create a Microsoft Copilot Studio agent capable of answering finance-related FAQs.
- Enable document upload and basic processing for invoices and financial documents.
- Publish the Copilot as a web app and test sample queries.

## Datasets  

- Use the pre-provided dataset located in `C:\datasets\finance_faq.xlsx`.
- This dataset contains sample finance FAQs and policy information.
- Optional invoice samples available at `C:\datasets\invoice_samples.pdf` for reference.

## Challenge Objectives  

1. **Copilot Studio Access and Environment Setup**
   - Navigate to Power Platform portal and create a `developer` environment.
   - Login to Microsoft Copilot Studio portal and select the developer environment which is created earlier.

2. **Create a New Copilot Agent**
   - Click **+ New Agent**.
   - Name your agent: **FinanceInsight-Foundation**.
   - Choose the Finance category and proceed with default language and region.

3. **Knowledge Source Integration**
   - From the **Knowledge** section, choose **Add data source**.
   - Upload or connect the Excel file from `C:\datasets\finance_faq.xlsx`.
   - Select relevant columns as the question and answer fields.
   - Set scope to **Only from this knowledge** to ensure grounded responses.

4. **Topic Creation for Finance FAQs**
   - Add a new topic named **FinanceFAQs**.
   - Set trigger phrases such as:
     - `What is the invoice deadline?`
     - `How do I submit expenses?`
     - `What are the payment terms?`
   - Add message nodes with generative answers using your knowledge source.

5. **Document Upload Topic Creation**
   - Add a new topic named **DocumentUpload**.
   - Set trigger phrases such as:
     - `Upload invoice`
     - `Submit financial document`
     - `Process receipt`
   - Add question nodes to collect document information and upload instructions.

6. **Testing the Agent**
   - Use the built-in **Test Chat** panel in Copilot Studio.
   - Test queries such as:
     - `What is our expense reimbursement policy?`
     - `How do I upload an invoice for processing?`

7. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.
 
## Success Criteria  

- The agent successfully responds to finance-related queries using the FAQ dataset.
- The document upload topic provides clear guidance for users.
- The web app is accessible without authentication.
- Validation passes successfully.

## Additional Resources

- [Microsoft Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)
- [Connect knowledge sources in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge)
  
## Conclusion  

You have built the foundational layer of the Finance Document Insight Copilot that can answer finance FAQs intelligently using Copilot Studio. In the next challenge, you'll integrate Power Automate and Azure Document Intelligence for automated document processing and approval workflows.