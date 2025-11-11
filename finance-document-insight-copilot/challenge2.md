## Stage 2: Integration

# Challenge: Integrate Power Automate Tools within Copilot Studio for Finance Document Automation
  
## Problem Statement

While your foundational chatbot can answer FAQs and guide document uploads, enterprise finance environments also require automated workflows to handle document processing and approval efficiently. In this challenge, you will extend your Copilot agent to include document processing automation directly within the Copilot Studio portal using Power Automate connectors and Azure Document Intelligence.

## Goals

- Automate finance document processing and field extraction through Copilot Studio's integrated Power Automate tools.
- Enable Microsoft Teams based notifications for finance managers during approval workflows.
- Store and manage all extracted document data within Dataverse in a structured format.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\invoices_sample_set.pdf`.
- This dataset contains sample invoices and financial documents for testing extraction workflows.

## Challenge Objectives  

1. **Set Up Azure Document Intelligence Service**
   - Navigate to Azure portal and create an **Azure AI Document Intelligence** resource.
   - Complete the setup wizard and note down your **endpoint** and **API key**.
   - Navigate to **Document Intelligence Studio** and familiarize yourself with prebuilt models for invoices.
   - Test the prebuilt invoice model with sample documents to understand field extraction capabilities.

2. **Open Copilot Studio and Access Power Automate Tools**
   - Launch **Microsoft Copilot Studio** from your Microsoft 365 portal.
   - Open the **FinanceInsight-Foundation** agent you created in the previous challenge.
   - From the left navigation panel, go to **Tools → Power Automate** to view available connectors and builder options.

3. **Create a Power Automate Flow within Copilot Studio**
   - In Copilot Studio, navigate to **Tools → Power Automate → Create Flow**.
   - Name the flow **ProcessFinanceDocument**.
   - Add the following steps:
     1. **Trigger:** Use **When a Copilot topic runs this flow**.
     2. **Action 1:** Add an **Azure AI Document Intelligence** action to analyze the uploaded document.
     3. **Action 2:** Parse the extracted fields (vendor, amount, date, invoice number).
     4. **Action 3:** Store the extracted data in Dataverse for tracking and analytics.
     5. **Action 4:** Add a **Teams → Post message in a channel** action for approval notifications.

4. **Create Dataverse Table for Document Storage**
   - In your environment, create a new **Dataverse** table called **FinanceDocuments**.
   - Define columns for vendor information, amounts, dates, approval status, and document metadata.
   - Configure proper data types and relationships for efficient querying and reporting.

5. **Integrate the Flow into Your Copilot Agent**
   - In **Copilot Studio → Topics**, create or open a topic named **DocumentProcessor**.
   - Add **Trigger phrases** like:
     - `Process my invoice`
     - `Extract document data`
     - `Submit for approval`
   - Add a **Power Automate Action Node** to call the **ProcessFinanceDocument** flow.
   - Map conversation variables to flow parameters and display extracted information for user confirmation.

6. **Testing the Agent**
   - Use the **Test your copilot** panel to simulate conversations such as:
     - `Process this invoice for vendor ABC Corp.`
     - `Extract data from my uploaded receipt.`
   - Verify that document processing works correctly and Teams notifications are sent for approval.

7. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.

## Success Criteria  

- The Copilot agent successfully triggers document processing flows within the Copilot Studio portal.
- Document Intelligence correctly extracts key fields (vendor, amount, date, invoice number).
- Teams notifications are sent automatically when documents require approval.
- All extracted data is properly stored in Dataverse with relevant metadata.

## Additional Resources

- [Build flows directly in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/power-automate-integration)
- [Azure AI Document Intelligence Documentation](https://learn.microsoft.com/en-us/azure/ai-services/document-intelligence/)
- [Send messages to Teams channels using Power Automate](https://learn.microsoft.com/en-us/connectors/teams/)

## Conclusion  

You have enhanced your Copilot's functionality by integrating Power Automate connectors directly within Copilot Studio to automate finance document processing and approval workflows. Your Copilot is now capable of handling real-world finance automation workflows, paving the way for adding AI-driven insights and analytics in the next stage.