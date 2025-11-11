# Challenge 2: Integrate IoT Telemetry and Automate Maintenance Workflows using Azure IoT Hub and Power Automate
  
## Problem Statement

Industrial equipment generates thousands of IoT signals daily, but without integration and automation, most of these insights are lost. In this challenge, you’ll integrate Azure IoT Hub with Power Automate to stream telemetry data, detect threshold breaches, and trigger automated maintenance actions through Teams and Dataverse.

## Goals

- Connect IoT devices to Azure IoT Hub for telemetry ingestion.  
- Trigger maintenance alerts and create work orders automatically using Power Automate.  
- Store and manage ticket data within Dataverse for future predictive analysis.

## Datasets  

- Use the provided IoT telemetry simulation file in `C:\datasets\iot_equipment_stream.csv`.  
- This dataset simulates real-time telemetry readings such as *temperature*, *vibration*, and *pressure* to represent sensor outputs from manufacturing equipment.

## Challenge Objectives  

1. **Azure IoT Hub Setup**
   - In the Azure portal, create an **IoT Hub** named `maintenance-iothub`.
   - Add a new **IoT Device** named `equipment-simulator-01`.
   - Note down the **Connection String (Primary key)** from the device’s properties — this will be used in your simulator script.
   - Open **Azure Cloud Shell** or use the **Device Explorer** tool to send sample telemetry data:
     ```json
     {
       "equipmentId": "EQP-12",
       "temperature": 84.2,
       "vibration": 0.09,
       "pressure": 112.5,
       "timestamp": "2025-11-10T15:05:00Z"
     }
     ```
   - Validate that messages are successfully reaching IoT Hub using **Metrics → Messages received** in the portal.

2. **Stream Data to Event Hub (Optional Enhancement)**
   - Add a **Built-in Event Hub Endpoint** under your IoT Hub.
   - Enable **Routing** to forward telemetry data to this endpoint.
   - This enables downstream systems like Azure Machine Learning or Power BI to subscribe to telemetry streams for analysis.

3. **Dataverse Configuration**
   - In your Power Platform environment, open **Dataverse** and create a new table called `EquipmentMaintenance`.
   - Add columns:
     - `EquipmentID` (Text)
     - `Temperature` (Decimal)
     - `Vibration` (Decimal)
     - `Pressure` (Decimal)
     - `Status` (Choice: Normal, Warning, Critical)
     - `AlertTime` (DateTime)
   - Save and publish the table.

4. **Power Automate Flow for Alert Generation**
   - Open **Power Automate** and create a **New Cloud Flow** named `IoTMaintenanceAlertFlow`.
   - Use **When an HTTP request is received** as a trigger.
   - Parse incoming telemetry JSON using a schema matching the IoT payload.
   - Add a **Condition** step:
     - If temperature > 80 OR vibration > 0.08 → set status as **Critical**.
   - Add actions:
     - **Add a new row** to the `EquipmentMaintenance` table.
     - If status = Critical → **Post adaptive card** to a Teams channel notifying maintenance staff.
       - Example Teams message:
         > ⚠️ **Critical Equipment Alert**  
         > Equipment ID: EQP-12  
         > Temperature: 84.2°C  
         > Action: Schedule immediate inspection.

5. **Copilot Studio Integration**
   - In **Copilot Studio**, open your agent and add a new topic called **EquipmentStatus**.
   - Add trigger phrases:
     - `Show latest maintenance alerts`
     - `Check equipment health`
   - Use an **Action Node** to call your Power Automate flow endpoint to fetch or log telemetry data.
   - Configure the response to display recent alerts in chat (e.g., last 3 alerts from Dataverse).

6. **IoT Data Simulation and Testing**
   - Use the sample file `C:\datasets\iot_equipment_stream.csv` or Azure CLI to simulate data every few seconds.
   - Verify Power Automate triggers and Teams notifications.
   - Ask Copilot:
     - `Show all critical alerts from last hour.`
     - `Which equipment has abnormal vibration levels?`

7. **Optional Enhancements**
   - Add a **Logic App** to consolidate multiple telemetry sources.
   - Integrate with **Power BI** to visualize temperature and vibration trends.
   - Set **threshold-based notifications** using Azure Monitor for real-time alerting.

## Success Criteria  

- IoT telemetry successfully streams into IoT Hub and triggers Power Automate flows.  
- Alerts and maintenance records are automatically stored in Dataverse.  
- Copilot retrieves and displays equipment health insights conversationally.  
- Teams notifications are sent automatically for critical events.

## Additional Resources

- [Azure IoT Hub Quickstart](https://learn.microsoft.com/en-us/azure/iot-hub/quickstart-send-telemetry-cli)  
- [Power Automate HTTP Trigger Setup](https://learn.microsoft.com/en-us/power-automate/http-connectors)  
- [Dataverse Tables Overview](https://learn.microsoft.com/en-us/power-apps/maker/data-platform/data-platform-tables-overview)  
- [Azure Event Hub Routing](https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-tutorial-create)  

## Conclusion  

You’ve now integrated IoT telemetry, automation, and alerting into your **Predictive Maintenance Copilot**. The system automatically logs sensor anomalies, notifies maintenance teams, and tracks alerts in Dataverse — setting the stage for AI-powered predictive maintenance in the next challenge.