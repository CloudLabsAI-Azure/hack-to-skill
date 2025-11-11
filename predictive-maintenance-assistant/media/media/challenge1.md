# Challenge 1: Build a Maintenance Operations Copilot with Copilot Studio (Foundation)

## Problem Statement

Maintenance teams need a fast, consistent way to **log issues** and **check equipment status** without bouncing across tools. In this foundation stage, you’ll build a Copilot Studio chatbot that lets technicians **create maintenance tickets**, **view/update equipment status**, and **confirm actions** — all backed by **Dataverse** and accessible from **Teams** (or Demo Web App).

## Goals

- Create a Copilot Studio agent for **manual ticket logging** and **equipment status lookups**.  
- Store and retrieve records using **Dataverse** tables.  
- Publish the Copilot to **Teams** (or Demo Web App) for quick field access.

## Datasets

- No uploads required in this challenge.  
- (Optional) You may copy sample descriptions from `C:\datasets\maintenance_samples.txt` into topic prompts/messages for testing.

## Challenge Objectives

1. **Create the Copilot Agent**
   - Open **Microsoft Copilot Studio**.
   - Click **+ New agent** and name it **PM-Foundation** (Category: Operations / Manufacturing).
   - Keep default language/region and create the agent.

2. **Dataverse Tables**
   - In your Power Platform environment, create two tables:

     **a) MaintenanceTickets**  
     - `TicketId` (Auto-number or Text; Primary)  
     - `EquipmentID` (Text)  
     - `IssueCategory` (Choice: Electrical, Mechanical, Sensors, Network, Other)  
     - `Severity` (Choice: Low, Medium, High, Critical)  
     - `Description` (Multiline Text)  
     - `Status` (Choice: New, In Progress, On Hold, Resolved, Closed)  
     - `CreatedOn` (DateTime)  
     - `AssignedTo` (Text or Lookup if you have users)

     **b) EquipmentStatus**  
     - `EquipmentID` (Text; Primary)  
     - `Name` (Text)  
     - `Location` (Text)  
     - `HealthState` (Choice: Normal, Warning, Critical, Offline)  
     - `LastInspection` (Date)  
     - `Notes` (Multiline Text)

   - Save and publish both table schemas.

3. **Topic: Log Maintenance Ticket**
   - Create a **Topic** named **LogTicket** with trigger phrases:
     - `Log a maintenance issue`
     - `Create a maintenance ticket`
     - `Report a problem for equipment`
   - Add **Question** nodes to capture:
     - `EquipmentID` (text)
     - `IssueCategory` (choice)
     - `Severity` (choice)
     - `Description` (long text)
   - Add a **Message** node summarizing the inputs and ask for **confirmation (Yes/No)**.
   - On **Yes**:
     - Use an **Action** to **Create row in Dataverse → MaintenanceTickets** (map fields).
     - Generate/display a `TicketId` (use auto-number or returned ID) and a friendly confirmation.
   - On **No**:
     - Offer to edit key fields (Severity/Description) and re-confirm.

4. **Topic: View Equipment Status**
   - Create a **Topic** named **EquipmentStatusLookup** with trigger phrases:
     - `Check equipment status`
     - `Show status for EQP-##`
     - `Is compressor online`
   - Ask for `EquipmentID` if not provided in the utterance.
   - Add an **Action** to **List/Get row(s) from Dataverse → EquipmentStatus** by `EquipmentID`.
   - Display:
     - **Name**, **Location**, **HealthState**, **LastInspection**, **Notes**.
   - If not found, guide the user to log a ticket via **LogTicket**.

5. **Topic: Update Equipment Health (Optional)**
   - Create **Topic**: **UpdateEquipmentHealth** with trigger phrases:
     - `Update EQP-## health`
     - `Set compressor health to warning`
   - Ask for `EquipmentID` and `HealthState` (choice).
   - **Update row in Dataverse → EquipmentStatus**.
   - Confirm the update back to the user.

6. **Agent Variables & Formatting**
   - Create variables:
     - `CurrentEquipmentID` (Text)
     - `CurrentTicketId` (Text)
   - Use short **bullet summaries** and **bold labels** in messages for clarity.
   - Provide quick tips (e.g., “Say *check equipment status* to view current health.”).

7. **Publish to Teams (or Demo Web App)**
   - Go to **Channels**:
     - Preferred: **Microsoft Teams** → enable and add to a team or chat.
     - Alternative: **Demo Web App** → enable and copy URL.  
   - (Lab convenience) If using Demo Web App, **disable authentication** for testing.

8. **Test End-to-End**
   - Try:
     - `Create a maintenance ticket for EQP-12 – mechanical, severity high, belt slippage noise.`
     - `Check equipment status for EQP-12.`
     - *(Optional)* `Update EQP-12 health to Warning.`
   - Verify new ticket rows appear in **MaintenanceTickets** and lookups work for **EquipmentStatus**.

## Success Criteria

- Technicians can **log tickets** with EquipmentID, Category, Severity, and Description, and receive a **TicketId**.  
- Users can **retrieve equipment status** from Dataverse by EquipmentID.  
- Copilot is **published** (Teams or Demo Web App) and works end-to-end.

## Additional Resources

- Microsoft Copilot Studio Documentation  
- Dataverse Tables Overview  
- Copilot Studio: Actions (Dataverse connectors) and Publishing Channels

## Conclusion

You’ve created the foundation of the **Predictive Maintenance Assistant**: a Copilot that logs maintenance issues and surfaces equipment status from Dataverse. In **Challenge 2**, you’ll integrate **IoT Hub** and **Power Automate** to trigger real-time alerts and work orders from telemetry.