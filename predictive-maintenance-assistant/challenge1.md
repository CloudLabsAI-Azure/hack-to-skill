## Stage 1: Foundation

# Challenge: Build a Foundational Predictive Maintenance Copilot using Microsoft Copilot Studio
  
## Problem Statement

Industrial maintenance teams handle large volumes of equipment monitoring data, maintenance requests, and compliance reports spread across multiple systems. Manual tracking of equipment health and maintenance schedules consumes hours and risks equipment downtime. This challenge focuses on building the foundation of an AI-powered Predictive Maintenance Assistant capable of logging maintenance issues and providing equipment status information.

## Goals

- Create a Microsoft Copilot Studio agent capable of handling maintenance-related queries and ticket logging.
- Enable equipment status lookup and basic maintenance issue reporting.
- Publish the Copilot as a web app and test sample scenarios.

## Datasets  

- Use the pre-provided dataset located in `C:\datasets\maintenance_faq.xlsx`.
- This dataset contains sample maintenance procedures and equipment information.
- Optional maintenance samples available at `C:\datasets\maintenance_samples.txt` for reference.

## Challenge Objectives  

1. **Copilot Studio Access and Environment Setup**
   - Navigate to Power Platform portal and create a `developer` environment.
   - Login to Microsoft Copilot Studio portal and select the developer environment which is created earlier.

2. **Create a New Copilot Agent**
   - Click **+ New Agent**.
   - Name your agent: **MaintenanceAssistant-Foundation**.
   - Choose the Operations category and proceed with default language and region.

3. **Knowledge Source Integration**
   - From the **Knowledge** section, choose **Add data source**.
   - Upload or connect the Excel file from `C:\datasets\maintenance_faq.xlsx`.
   - Select relevant columns as the question and answer fields.
   - Set scope to **Only from this knowledge** to ensure grounded responses.

4. **Topic Creation for Maintenance FAQs**
   - Add a new topic named **MaintenanceFAQs**.
   - Set trigger phrases such as:
     - `What is the maintenance schedule?`
     - `How do I report equipment issues?`
     - `What are the safety procedures?`
   - Add message nodes with generative answers using your knowledge source.

5. **Equipment Status Topic Creation**
   - Add a new topic named **EquipmentStatus**.
   - Set trigger phrases such as:
     - `Check equipment status`
     - `Show me equipment health`
     - `Is equipment EQP-12 running?`
   - Add question nodes to collect equipment information and provide status responses.

6. **Maintenance Ticket Creation Topic**
   - Add a new topic named **CreateTicket**.
   - Set trigger phrases such as:
     - `Log maintenance issue`
     - `Create work order`
     - `Report equipment problem`
   - Add question nodes to collect issue details and provide confirmation.

7. **Testing the Agent**
   - Use the built-in **Test Chat** panel in Copilot Studio.
   - Test queries such as:
     - `What is our preventive maintenance schedule?`
     - `How do I create a maintenance ticket for equipment failure?`

8. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.
 
## Success Criteria  

- The agent successfully responds to maintenance-related queries using the FAQ dataset.
- Equipment status and ticket creation topics provide clear guidance for users.
- The web app is accessible without authentication.
- Validation passes successfully.

## Additional Resources

- [Microsoft Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)
- [Connect knowledge sources in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge)
  
## Conclusion  

You have built the foundational layer of the Predictive Maintenance Assistant that can answer maintenance FAQs and guide equipment management processes using Copilot Studio. In the next challenge, you'll integrate Power Automate and Azure IoT Hub for automated equipment monitoring and alert workflows.