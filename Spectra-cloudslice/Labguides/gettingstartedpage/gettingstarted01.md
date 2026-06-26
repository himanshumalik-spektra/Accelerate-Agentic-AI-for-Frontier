# Hands-on Labs - Day 1

# Architect intelligent agents with Microsoft IQ and Foundry

## Overall Estimated Duration: 4 Hours

## Overview

This lab demonstrates how Azure AI services can be combined to build enterprise AI solutions across multiple business scenarios. It covers three patterns: a HR knowledge assistant for policy retrieval, a multi-agent solution for healthcare prior authorization, and an enterprise automation framework for cross-functional workflows.

In the first scenario, you will build a Copilot Studio knowledge assistant that uses Azure AI Search and Azure OpenAI to retrieve information from HR documents through semantic and vector-based search. In the second, you will deploy a multi-agent AI solution that coordinates specialized agents to automate a healthcare prior authorization workflow. In the third, you will explore a broader orchestration framework designed for business processes such as onboarding, support, marketing, RFP analysis, and compliance review.

Across these scenarios, the lab shows how Azure AI Search, Azure OpenAI Service, Microsoft Copilot Studio, Azure Container Apps, Azure Cosmos DB, Azure App Service, Azure Storage, GitHub Codespaces, and Microsoft Foundry can be used together to build scalable, enterprise-ready AI applications.

## Objective

By the end of this lab, participants will be able to:

- Create and configure Azure AI Search, Azure Storage, and Azure OpenAI resources for AI-powered applications,

- Build a Copilot Studio knowledge assistant and connect it to Azure AI Search,

- Create a vector index and enable retrieval-augmented generation over enterprise documents,

- Deploy and validate a containerized multi-agent workflow using GitHub Codespaces and Azure Developer CLI,

- Provision and verify the Azure resources required for enterprise AI automation,

- Configure post-deployment settings such as authentication and sample data,

- Test AI-driven scenarios to observe how specialized agents work together to complete business tasks.

## Pre-requisites

Participants should have:

- An active Azure subscription with permission to create and manage resources,

- A valid GitHub account to fork the repository and use GitHub Codespaces,

- Access to Microsoft Copilot Studio and Microsoft Foundry,

- The required Azure resource providers registered in the subscription,

- Access to Azure and GitHub credentials for authentication during setup and deployment.

## Explanation of Components

The architecture for this lab involves the following key components:

1. **Azure AI Search:** A cloud-based search service that enables intelligent search experiences over structured and unstructured data.

   - Supports semantic and vector-based search capabilities.
   - Enables fast retrieval of indexed enterprise data.

1. **Azure OpenAI Service:** Provides access to advanced AI models for natural language processing and generative AI capabilities.

   - Supports text generation, embeddings, and reasoning tasks.
   - Enables AI-powered conversational and analytical solutions.

1. **Microsoft Copilot Studio:** A low-code platform used to create and manage AI-powered copilots and virtual assistants.

   - Supports conversational AI development.
   - Enables integration with enterprise data sources and services.

1. **Azure Storage Account:** A scalable cloud storage service used to securely store different types of data.

   - Supports blob, file, queue, and table storage services.
   - Provides durable and highly available data storage.

1. **Azure Container Apps:** A managed service for running containerized applications and microservices.

   - Supports scalable container deployment.
   - Simplifies container orchestration and management.

1. **Azure Container Registry:** A private container registry service for storing and managing container images.

   - Enables secure storage of container
   - Supports container-based application deployment workflows.

1. **Azure Cosmos DB:** A globally distributed NoSQL database service designed for high scalability and low latency.
 
   - Supports multiple data models and APIs.
   - Provides high availability and elastic scalability.

1. **Azure App Service:** A fully managed platform for hosting web applications, APIs, and backend services.

   - Supports scalable application hosting.
   - Enables secure and efficient web application deployment.

1. **GitHub Codespaces:** A cloud-based development environment integrated with GitHub repositories.

   - Provides ready-to-use development workspaces.
   - Supports collaborative and remote development workflows.

1. **Microsoft Foundry:** A platform used for managing AI models, deployments, and related AI resources.

   - Supports AI model deployment and monitoring.
   - Provides centralized access to AI assets and services.

1. **Multi-Agent Framework:** A framework that enables multiple AI agents to collaborate and coordinate tasks within intelligent systems.

   - Supports distributed task execution and decision-making.
   - Enables automation across complex workflows and processes.

1. **Vector Index:** A data structure used to store and retrieve vector embeddings for similarity-based search operations.

   - Supports semantic and nearest-neighbor search.
   - Improves retrieval accuracy for AI-powered applications.

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

    ![](./media/94.png)

2. You'll see the **Sign into Microsoft Azure** tab. Here, enter your **credentials (1)** and select **Next (2)**:

   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

     ![Enter Your Username](media/odlusr.png)

3. Next, provide **Temporary Access pass**, and select **Sign In (2)**:

   - Enter **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject> **(1)**

        ![](./media/image.png)

4. If **Action required** pop-up window appears, click on **Ask later**.
5. If prompted to **stay signed in**, you can click **No**.

    ![](./media/97.png)

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
