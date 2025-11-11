## Stage 1: Foundation

# Challenge: Build a Cross-Domain FAQ Copilot with Microsoft Copilot Studio

## Problem Statement

Modern enterprises struggle with fragmented knowledge across HR, Finance, and IT departments, creating information silos that slow decision-making and reduce productivity. Employees waste time searching multiple systems for basic information that should be easily accessible through a unified interface.

## Challenge Objectives

In this challenge, you'll create a foundational **Unified Enterprise Copilot** using Microsoft Copilot Studio to answer cross-domain FAQs and provide a centralized knowledge interface for your organization.

### Step 1: Environment Setup and Copilot Creation

- Access Microsoft Copilot Studio from your Azure environment
- Create a new Copilot named `UnifiedEnterpriseBot`
- Verify your Power Platform environment configuration and permissions

### Step 2: Configure Cross-Domain Knowledge Sources

- Navigate to **Knowledge** section in Copilot Studio
- Set up three department-specific knowledge sources:
  - **HR Knowledge Base**: Employee policies, benefits, and procedures
  - **Finance Knowledge Base**: Expense policies, budget processes, and financial procedures  
  - **IT Support Knowledge Base**: Hardware support, software issues, and IT policies
- Configure appropriate access controls and filtering for each knowledge source

### Step 3: Create Intelligent Topic Routing

- Design system topics for cross-domain query handling
- Implement department identification logic to route queries appropriately
- Configure fallback handling for unresolved inquiries
- Set up escalation paths to human agents when needed

### Step 4: Test Cross-Domain Conversations

- Use the Test bot feature to validate responses across departments
- Test HR queries: leave policies, benefits enrollment, employee procedures
- Test Finance queries: expense approvals, reimbursement processes, budget information
- Test IT queries: password resets, hardware requests, software support
- Validate cross-domain scenarios requiring multiple department information

### Step 5: Optimize Response Quality

- Fine-tune knowledge base responses for accuracy and helpfulness
- Configure response formats to include relevant department contacts
- Implement consistent tone and branding across all responses
- Ensure proper handling of sensitive or confidential information

### Step 6: Deploy and Publish the Copilot

- Navigate to **Publish** in Copilot Studio
- Deploy the Copilot to Microsoft Teams for organization-wide access
- Configure user permissions and access controls
- Test end-to-end functionality in the Teams environment

## Success Criteria

- Functional Unified Enterprise Copilot created in Microsoft Copilot Studio  
- Successfully integrated knowledge sources for HR, Finance, and IT departments  
- Cross-domain queries properly routed to appropriate knowledge sources  
- Graceful handling of scenarios where information cannot be found  
- Copilot successfully deployed and accessible via Microsoft Teams  

## Next Steps

After completing this foundation, proceed to **Challenge 2** where you'll integrate Power Automate and Dataverse to enable real-time data access and automated actions across departments.