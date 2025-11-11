## Stage 2: Integration

# Challenge: Integrate Power Automate Tools within Copilot Studio for HR Feedback and Compliance
  
## Problem Statement

Policy answers alone aren't enough—HR also needs structured feedback, clarification requests, and automated reminders for compliance or training renewals. In this challenge, you'll integrate **Power Automate** with your Copilot to capture employee inputs and trigger proactive workflows directly within the Copilot Studio portal using Freshdesk for tracking and Teams for notifications.

## Goals

- Automate HR feedback collection and compliance tracking through Copilot Studio's integrated Power Automate tools.
- Enable Microsoft Teams based notifications for HR staff.
- Store and manage all feedback data within Freshdesk in a structured format.

## Datasets  

- Use the pre-provided dataset in `C:\datasets\hr_feedback_template.csv`.
- This dataset contains sample feedback templates and metadata to guide the feedback structure.

## Challenge Objectives  

1. **Set Up Freshdesk Free Trial Account**
   - Navigate to [Freshdesk Free Trial](https://freshdesk.com/signup) and create a free trial account.
   - Complete the setup wizard and note down your **Freshdesk domain** (e.g., `yourcompany.freshdesk.com`).
   - Navigate to **Profile Settings → API Key** and copy your API key for later use.
   - Create a custom ticket category for **HR Feedback** in Freshdesk settings.

2. **Open Copilot Studio and Access Power Automate Tools**
   - Launch **Microsoft Copilot Studio** from your Microsoft 365 portal.
   - Open the **HRInsights-Foundation** agent you created in the previous challenge.
   - From the left navigation panel, go to **Tools → Power Automate** to view available connectors and builder options.

3. **Create a Power Automate Flow for Feedback Submission**
   - In Copilot Studio, navigate to **Tools → Power Automate → Create Flow**.
   - Name the flow **SubmitHRFeedback**.
   - Add the following steps:
     1. **Trigger:** Use **When a Copilot topic runs this flow**.
     2. **Action 1:** Add an **HTTP** action to create a Freshdesk ticket for feedback.
        - Method: **POST**
        - URI: `https://yourcompany.freshdesk.com/api/v2/tickets`
        - Headers:
          - `Content-Type`: `application/json`
          - `Authorization`: `Basic <base64_encoded_api_key>`
        - Body (JSON):
          ```json
          {
            "subject": "HR Feedback: @{triggerBody()?['policyTopic']}",
            "description": "@{triggerBody()?['feedbackText']}",
            "email": "@{triggerBody()?['employeeEmail']}",
            "priority": 2,
            "status": 2,
            "type": "Question",
            "tags": ["hr-feedback"]
          }
          ```
     3. **Action 2:** Parse the response JSON to extract the **Ticket ID**.
     4. **Action 3:** Add a **Teams → Post message in a channel** action.
        - Channel: **HR Feedback** (create if needed).
        - Message: Include Feedback Topic, Employee Email, and Ticket ID.
   - Save and test the flow to ensure it successfully creates Freshdesk tickets and sends Teams messages.

4. **Create a Power Automate Flow for Policy Clarification Requests**
   - In Copilot Studio, create a second flow named **RequestPolicyClarification**.
   - Add the following steps:
     1. **Trigger:** Use **When a Copilot topic runs this flow**.
     2. **Action 1:** Create a Freshdesk ticket with type "Problem" and tag "clarification-needed".
     3. **Action 2:** Send an email to the HR mailbox with the employee's question and policy reference.
     4. **Action 3:** Return ticket confirmation to Copilot.

5. **Create a Power Automate Flow for Compliance Reminders**
   - Create a third flow named **ComplianceReminders**.
   - Configure as a **Scheduled** flow (daily at 9 AM).
   - Add logic to:
     - Query a list of compliance tasks (can be maintained in a SharePoint list or use sample data).
     - Send **Teams** messages to employees with upcoming compliance deadlines (within 7 days).
     - Include "Acknowledge" adaptive card buttons for user confirmation.

6. **Integrate the Flows into Your Copilot Agent**
   - In **Copilot Studio → Topics**, create or open a topic named **Feedback-and-Compliance**.
   - Add **Trigger phrases** like:
     - `I want to give feedback on HR policies`
     - `Request clarification about benefits`
     - `Need help understanding leave policy`
   - Add question nodes to collect:
     - Employee email
     - Policy topic
     - Feedback or question text
   - Add a **Power Automate Action Node** to call the appropriate flow based on user intent.
   - Map conversation variables to flow parameters.
   - Display the returned Ticket ID to the user in a confirmation message.

6. **Testing the Agent**
   - Use the **Test your copilot** panel to simulate conversations such as:
     - `I want to give feedback on the remote work policy.`
     - `Raise a clarification on sick leave eligibility.`
   - Verify that the flow executes, a Freshdesk ticket is created, and a Teams notification is received.
   - Login to your Freshdesk portal and confirm the ticket appears with correct details.

7. **Publishing the Agent**
   - Navigate to **Settings → Channels**.
   - Enable **Demo Web App** channel.
   - Disable authentication for ease of access.
   - Publish and test the agent in the browser.

## Success Criteria  

- The Copilot agent successfully triggers feedback collection flows within the Copilot Studio portal.
- Tickets appear correctly in Freshdesk with assigned IDs and proper categorization.
- Teams notifications are sent automatically when feedback is submitted.
- Users receive confirmation messages with Ticket ID in the chat.

## Additional Resources

- [Build flows directly in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/power-automate-integration)
- [Freshdesk API Documentation](https://developers.freshdesk.com/api/)
- [Send messages to Teams channels using Power Automate](https://learn.microsoft.com/en-us/connectors/teams/)

## Conclusion  

You have enhanced your HR Copilot's functionality by integrating Power Automate connectors directly within Copilot Studio to automate feedback collection and compliance reminders. Your Copilot is now capable of handling real-world HR workflow automation paving the way for adding AI-driven sentiment analysis and talent insights in the next stage.