## Stage 2: Integration

# Challenge: Integrate Power Automate Tools within Copilot Studio for IT Ticket Automation
  
## Problem Statement

While your foundational chatbot can answer FAQs, enterprise IT environments also require automated workflows to handle ticketing operations efficiently. In this challenge, you will extend your Copilot agent to include ticket automation directly within the Copilot Studio portal using Power Automate connectors and actions. You'll enable the bot to create, update, and escalate IT tickets while sending real-time notifications to support engineers all without leaving Copilot Studio.

## Goals

- Automate IT ticket creation and tracking directly through Copilot Studio's integrated Power Automate tools.
- Enable Microsoft Teams based notifications for support engineers.
- Store and manage all ticket data within Freshdesk in a structured format.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\tickets_template.csv`.
- This dataset contains sample ticket templates and metadata to simulate user issue tracking.

## Challenge Objectives  

1. **Set Up Freshdesk Free Trial Account**
   - Navigate to [Freshdesk Free Trial](https://freshdesk.com/signup) and create a free trial account.
   - Complete the setup wizard and note down your **Freshdesk domain** (e.g., `yourcompany.freshdesk.com`).
   - Navigate to **Profile Settings → API Key** and copy your API key for later use.
   - Familiarize yourself with the Freshdesk ticket structure (Subject, Description, Priority, Status).

2. **Open Copilot Studio and Access Power Automate Tools**
   - Launch **Microsoft Copilot Studio** from your Microsoft 365 portal.
   - Open the **ITSupportAssistant-Foundation** agent you created in the previous challenge.
   - From the left navigation panel, go to **Tools → Power Automate** to view available connectors and builder options.

3. **Create a Power Automate Flow within Copilot Studio**
   - In Copilot Studio, navigate to **Tools → Power Automate → Create Flow**.
   - Name the flow **CreateFreshdeskTicket**.
   - Add the following steps:
     1. **Trigger:** Use **When a Copilot topic runs this flow**.
     2. **Action 1:** Add an **HTTP** action to create a Freshdesk ticket.
        - Method: **POST**
        - URI: `https://yourcompany.freshdesk.com/api/v2/tickets`
        - Headers:
          - `Content-Type`: `application/json`
          - `Authorization`: `Basic <base64_encoded_api_key>`
        - Body (JSON):
          ```json
          {
            "subject": "@{triggerBody()?['ticketSubject']}",
            "description": "@{triggerBody()?['ticketDescription']}",
            "email": "@{triggerBody()?['userEmail']}",
            "priority": @{triggerBody()?['priority']},
            "status": 2
          }
          ```
     3. **Action 2:** Parse the response JSON to extract the **Ticket ID**.
     4. **Action 3:** Add a **Teams → Post message in a channel** action.
        - Channel: **IT Support Notifications** (create if needed).
        - Message: Include Ticket ID, User Name, and Issue Description.
   - Save and test the flow to ensure it successfully creates Freshdesk tickets and sends Teams messages.

4. **Integrate the Flow into Your Copilot Agent**
   - In **Copilot Studio → Topics**, create or open a topic named **TicketAutomation**.
   - Add **Trigger phrases** like:
     - `I want to raise a support ticket`
     - `Report an issue with my device`
     - `Create a ticket for my IT problem`
   - Add question nodes to collect:
     - User name
     - User email
     - Issue description
     - Priority (Low/Medium/High)
   - Add a **Power Automate Action Node** to call the **CreateFreshdeskTicket** flow.
   - Map conversation variables (e.g., username, issue description, priority) to flow parameters.
   - Display the returned Ticket ID to the user in a confirmation message.

5. **Test the Copilot Agent**
   - Use the **Test your copilot** panel to simulate conversations such as:
     - `My Outlook keeps crashing, please raise a ticket.`
     - `Create a high-priority ticket for my network issue.`
   - Verify that the flow executes, a Freshdesk ticket is created, and a Teams notification is received.
   - Login to your Freshdesk portal and confirm the ticket appears with correct details.

6. **Publish and Validate**
   - Publish your updated agent via the **Demo Web App** channel.
   - Confirm ticket creation and Teams notifications work seamlessly.

## Success Criteria  

- The Copilot agent successfully triggers ticket creation flows within the Copilot Studio portal.
- Tickets appear correctly in Freshdesk with assigned IDs and "Open" status.
- Teams notifications are sent automatically when tickets are created.
- Users receive ticket confirmation with Ticket ID in the chat.

## Additional Resources

- [Build flows directly in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/power-automate-integration)
- [Freshdesk API Documentation](https://developers.freshdesk.com/api/)
- [Send messages to Teams channels using Power Automate](https://learn.microsoft.com/en-us/connectors/teams/)

## Conclusion  

You have enhanced your Copilot's functionality by integrating Power Automate connectors directly within Copilot Studio to automate IT ticket creation in Freshdesk and notifications. Your Copilot is now capable of handling real-world service automation without requiring external Power Automate setup paving the way for adding AI-driven insights and recommendations in the next stage.
