# Hands-on Labs - Day 2

# Extend, ground and orchestrate intelligent agents

## Overall Estimated Duration: 4 Hours

## Overview
 
In this lab, you will design and implement an AI-powered **customer resolution agent** for Contoso Electronics by integrating multiple Microsoft AI capabilities. The solution combines **Azure AI Search**, **Microsoft Fabric**, **Microsoft Foundry**, and intelligent data ontologies to create a unified, AI-driven customer support system.
 
This use case simulates a real-world operations and support environment where customer issues such as shipment delays, refunds, and escalations are handled using AI-driven insights. The agent leverages structured data (orders, inventory, support tickets), unstructured data (emails), and policy knowledge to provide accurate recommendations and automate responses. By integrating **Work IQ (email)**, **Foundry IQ (policies)**, and **Fabric IQ (data)**, you will create a unified Copilot-like experience that enhances operational efficiency and customer satisfaction.
 
## Objectives
 
By the end of this lab, participants will be able to:
 
- Create and configure an **Azure AI Search** service for indexing and retrieving enterprise documents.
 
- Set up a **storage account** and ingest policy and operational documents for knowledge grounding.
 
- Build a **Foundry Agent** that acts as a customer support and operations assistant.
 
- Create a **Microsoft Fabric workspace and lakehouse** for storing and managing business data such as customers, orders, and shipments.
 
- Design an **ontology model** that defines relationships between entities like Customers, Orders, Support Tickets, and Refund Claims.
 
- Develop a **Fabric Data Agent** that can interpret business data and provide insights.
 
- Integrate **Work IQ (email), Foundry IQ (policies), and Fabric IQ (data)** into a unified agent.
 
- Enable the agent to:
  - Analyze customer issues
  - Validate data across systems
  - Apply business policies
  - Recommend resolutions
  - Generate professional responses
 
## Pre-requisites
 
Participants should have:
 
- A working knowledge of Microsoft Azure services, including resource groups, virtual machines, Azure Storage, and Azure AI services.
 
- Basic familiarity with Microsoft Fabric, including workspace and lakehouse concepts.
 
- Understanding of AI concepts such as embeddings, ontologies, and Retrieval-Augmented Generation (RAG).
 
- Familiarity with data modeling and entity-relationship concepts.
 
- Knowledge of Azure role-based access control (RBAC) and authentication methods.
 
- General awareness of how AI services integrate with data platforms for intelligent decision-making.
 
- Basic understanding of email and communication workflows in enterprise environments.
 
## Explanation of Components
 
The architecture for this lab involves the following key components:
 
**Azure AI Search**: 
- Cloud-based service for searching privately curated enterprise data.
- Uses a combination of Microsoft's AI and JSON-based indexes to provide fast, relevant search results.
- Enables semantic search across policy documents and operational knowledge.
- Supports hybrid search (keyword + vector-based retrieval).
 
**Microsoft Foundry**:
- Central hub for building and managing AI agents.
- Provides the **Foundry Agent** that orchestrates customer resolution workflows.
- Integrates multiple **IQ** tools (Work IQ, Foundry IQ, Fabric IQ) into a unified interface.
- Manages agent instructions, tools, and knowledge bases.
 
**Microsoft Fabric**:
- Unified analytics platform for data engineering and data science.
- **Lakehouse**: Stores business data (customers, orders, shipments, support tickets, refunds).
- **Ontology (Preview)**: Defines entity types (Customer, Order, OrderItem, SupportTicket, RefundClaim, ShipmentTrackingEvent) and relationships (Places, Contains, hasSupportTicket, hasTrackingEvent, mayLeadTo).
- **Fabric Data Agent**: Interprets business data and answers questions about customer orders, shipments, refunds, and inventory.
 
**Azure Storage Account**:
- Blob storage for hosting policy documents, communication standards, and operational knowledge.
- Provides document indexing for **Azure AI Search**.
- Serves as the knowledge base for **Foundry IQ**.
 
**Work IQ (Email Integration)**:
- Provides email analysis and context extraction.
- Allows the agent to review customer and internal communications.
- Extracts key information about customer issues, complaints, and urgency.
 
**Foundry IQ (Policy Knowledge)**:
- Knowledge base connected to policy documents stored in Azure Storage.
- Enables the agent to apply business rules, SLA guidance, escalation criteria, and communication standards.
- Ensures consistent, policy-compliant decision-making.
 
**Fabric IQ (Data Intelligence)**:
- Ontology-based data interpretation layer.
- Provides business-context-aware responses by understanding entity relationships.
- Enables the agent to validate customer facts, order details, inventory status, and shipment history.
 
**Integration Flow**:
1. **Issue Intake**: Work IQ analyzes incoming customer emails to understand the issue and urgency.
2. **Data Validation**: Fabric IQ queries the lakehouse to validate customer, order, inventory, shipment, and support facts.
3. **Policy Application**: Foundry IQ applies internal policies and SLA guidance to determine eligibility for replacements, refunds, or escalations.
4. **Recommendation**: The Foundry Agent synthesizes all information to recommend the best resolution.
5. **Response Generation**: The agent drafts clear, professional customer-facing or internal responses based on the analysis.

## Getting Started with the lab

Welcome to your Accelerate Agentic AI for Frontier Workshop, Let's begin by making the most of this experience.

## Virtual Machine & Lab Guide

Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.

## Accessing Your Lab Environment

Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.

![Access Your VM and Lab Guide](media/gs0.png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![](./media/gs1.png)

## Exploring Your Lab Resources

To get a better understanding of your lab resources and credentials, navigate to the **Environment** tab.

![Explore Lab Resources](./media/gs1.1.png)

## Utilizing the Split Window Feature

For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.

![Use the Split Window Feature](./media/gs1.2.png)

## Managing Your Virtual Machine

Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!

![Manage Your Virtual Machine](media/VMSS.png)

## Let's Get Started with Azure Portal

1. On your virtual machine, click on the Azure Portal icon.

2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your **credentials (1)** and select **Next (2)**:

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

     ![Enter Your Username](media/odlusr.png)

3. Next, provide your **Temporary Access pass (1)**, enter the the password and select **Sign In (2)**:

    - Enter **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject> **(1)**

      ![](./media/image.png)

4. If **Action required** pop-up window appears, click on **Ask later**.
5. If prompted to **stay signed in**, you can click **No**.
6. If a **Welcome to Microsoft Azure** pop-up window appears, simply click **"Cancel"** to skip the tour.

## Steps to Proceed with MFA Setup if "Ask Later" Option is Not Visible

1. At the **"More information required"** prompt, select **Next**.

1. On the **"Keep your account secure"** page, select **Next** twice.

1. **Note:** If you don’t have the Microsoft Authenticator app installed on your mobile device:

   - Open **Google Play Store** (Android) or **App Store** (iOS).
   - Search for **Microsoft Authenticator** and tap **Install**.
   - Open the **Microsoft Authenticator** app, select **Add account**, then choose **Work or school account**.

1. A **QR code** will be displayed on your computer screen.

1. In the Authenticator app, select **Scan a QR code** and scan the code displayed on your screen.

1. After scanning, click **Next** to proceed.

1. On your phone, enter the number shown on your computer screen in the Authenticator app and select **Next**.
1. If prompted to stay signed in, you can click "No."

1. If a **Welcome to Microsoft Azure** pop-up window appears, simply click "Maybe Later" to skip the tour.

## Support Contact

The CloudLabs support team is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:

- Email Support: [cloudlabs-support@spektrasystems.com](mailto:cloudlabs-support@spektrasystems.com)
- Live Chat Support: https://cloudlabs.ai/labs-support

Click **Next** from the bottom right corner to embark on your Lab journey!

![Start Your Azure Journey](./media/PageNo.png)

Now you're all set to explore the powerful world of technology. Feel free to reach out if you have any questions along the way. Enjoy your workshop!
