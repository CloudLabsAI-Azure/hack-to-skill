# Challenge 2: Integrate Power Automate Tools within Copilot Studio for Predictive Maintenance Automation
  
## Problem Statement

While your foundational chatbot can answer maintenance FAQs and guide ticket creation, enterprise maintenance environments also require automated workflows to handle equipment monitoring and alert processing efficiently. In this challenge, you will extend your Copilot agent to include maintenance automation directly within the Copilot Studio portal using Power Automate connectors and Azure IoT Hub integration.

## Goals

- Automate equipment monitoring and alert processing through Copilot Studio's integrated Power Automate tools.
- Enable Microsoft Teams based notifications for maintenance engineers when equipment thresholds are exceeded.
- Store and manage all equipment telemetry data within Dataverse in a structured format.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\iot_equipment_stream.csv`.
- This dataset contains sample IoT telemetry data from industrial equipment for testing monitoring workflows.

## Challenge Objectives  

1. **Set Up Azure IoT Hub Service**
   - Navigate to Azure portal and create an **Azure IoT Hub** resource.
   - Complete the setup wizard and note down your **connection string** and **device keys**.
   - Navigate to **IoT Hub** and familiarize yourself with device management and telemetry monitoring capabilities.
   - Test the connection with sample telemetry data to understand data flow.

2. **Open Copilot Studio and Access Power Automate Tools**
   - Launch **Microsoft Copilot Studio** from your Microsoft 365 portal.
   - Open the **MaintenanceAssistant-Foundation** agent you created in the previous challenge.
   - From the left navigation panel, go to **Tools → Power Automate** to view available connectors and builder options.

3. **Create a Power Automate Flow within Copilot Studio**
   - In Copilot Studio, navigate to **Tools → Power Automate → Create Flow**.
   - Name the flow **ProcessEquipmentAlert**.
   - Add the following steps:
     1. **Trigger:** Use **When a Copilot topic runs this flow**.
     2. **Action 1:** Add an **Azure IoT Hub** action to check equipment telemetry data.
     3. **Action 2:** Parse the telemetry data and evaluate against threshold values.
     4. **Action 3:** Store the alert data in Dataverse for tracking and analysis.
     5. **Action 4:** Add a **Teams → Post message in a channel** action for maintenance team notifications.

4. **Create Dataverse Table for Equipment Monitoring**
   - In your environment, create a new **Dataverse** table called **EquipmentAlerts**.
   - Define columns for equipment ID, alert type, telemetry values, timestamps, and resolution status.
   - Configure proper data types and relationships for efficient querying and reporting.

5. **Integrate the Flow into Your Copilot Agent**
   - In **Copilot Studio → Topics**, create or open a topic named **EquipmentMonitor**.
   - Add **Trigger phrases** like:
     - `Check equipment alerts`
     - `Monitor equipment status`
     - `Process equipment telemetry`
   - Add a **Power Automate Action Node** to call the **ProcessEquipmentAlert** flow.
   - Map conversation variables to flow parameters and display equipment status information.

6. **Testing the Agent**
   - Use the **Test your copilot** panel to simulate conversations such as:
     - `Check alerts for equipment EQP-12.`
     - `Monitor telemetry data from manufacturing line.`
   - Verify that equipment monitoring works correctly and Teams notifications are sent for critical alerts.

7. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.

## Success Criteria  

- The Copilot agent successfully triggers equipment monitoring flows within the Copilot Studio portal.
- IoT Hub correctly processes telemetry data and identifies threshold violations.
- Teams notifications are sent automatically when critical equipment alerts are detected.
- All telemetry and alert data is properly stored in Dataverse with relevant metadata.

## Additional Resources

- [Build flows directly in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/power-automate-integration)
- [Azure IoT Hub Documentation](https://learn.microsoft.com/en-us/azure/iot-hub/)
- [Send messages to Teams channels using Power Automate](https://learn.microsoft.com/en-us/connectors/teams/)

## Conclusion  

You have enhanced your Copilot's functionality by integrating Power Automate connectors directly within Copilot Studio to automate predictive maintenance workflows and equipment monitoring. Your Copilot is now capable of handling real-world maintenance automation scenarios, paving the way for adding AI-driven predictive analytics and insights in the next stage.