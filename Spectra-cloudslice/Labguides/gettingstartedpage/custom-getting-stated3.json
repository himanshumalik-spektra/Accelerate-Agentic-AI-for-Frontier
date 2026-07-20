# Hands - on Labs - Day 3

# Manage, secure, and govern AI agents at scale

## Overall Estimated Duration: 4 Hours

## Overview

In this lab, you will design, deploy, and govern an end-to-end agentic AI solution using Microsoft Foundry. Working through a realistic retail scenario, you will build Cora, an intelligent customer service assistant for Zava, a home improvement retailer, and apply enterprise-grade observability and safety practices across the full agent lifecycle. Rather than treating AI agents as black boxes, you will instrument them with tracing, Application Insights integration, and structured evaluation frameworks to gain complete visibility into agent behavior. You will run quality and safety evaluations using Azure AI's built-in evaluators, test models for fitness, and validate agent responses against real-world criteria. To harden the solution against adversarial risks, you will leverage Microsoft Foundry's AI Red Teaming capabilities to detect harmful outputs, security gaps, and jailbreak vulnerabilities before they reach production. By combining Azure AI Agent Service, Azure AI Search, multi-agent orchestration, and centralized governance through the Foundry Control Plane, you will build an AI system that is transparent, secure, scalable, and production-ready.

## Objective

By the end of this lab, participants will be able to:

   - Building an Intelligent Retail Assistant Using Azure AI Agent Service and Azure AI Search

   - Orchestrating Multi-Agent Workflows with Microsoft Foundry Agent Framework

   - Evaluating AI Model Quality and Safety Using Microsoft Foundry Evaluation SDK

   - Implementing End-to-End Observability and Tracing with Application Insights and Microsoft Foundry

   - Hardening AI Agents Against Adversarial Risks Using Microsoft Foundry AI Red Teaming

   - Deploying and Governing Production-Ready AI Agents with Microsoft Foundry Control Plane

## Pre-requisites

Participants should have:

   - A working knowledge of Microsoft Azure services, including resource groups, Azure OpenAI, and Microsoft Foundry.

   - Basic experience with Python, including running scripts, working with virtual environments, and using Jupyter notebooks.

   - Familiarity with AI agent concepts such as retrieval-augmented generation (RAG), tool-calling, and multi-agent orchestration.

   - Understanding of Azure AI Search, including index creation, document ingestion, and semantic search configuration.

   - Awareness of AI evaluation concepts such as quality metrics (relevance, coherence, groundedness) and safety risk categories (violence, hate, self-harm, protected material).

   - General understanding of observability practices, including logging, distributed tracing, and monitoring with Application Insights.

   - Basic familiarity with Azure identity and authentication, including DefaultAzureCredential and role-based access control (RBAC).

## Explanation of Components

1. **Microsoft Foundry**: A unified platform for building, managing, and evaluating AI applications and agents on Azure. It provides tools for orchestration, model integration, monitoring, and governance across the AI lifecycle.

1. **Azure AI Agent Service**: A managed Azure service for creating AI-powered agents that can reason, use tools, retrieve data, and automate workflows. It simplifies deploying enterprise-grade conversational and autonomous AI experiences.

1. **Azure AI Search**: A cloud-based search and retrieval service that enables indexing, semantic search, vector search, and retrieval-augmented generation (RAG) for AI applications. It helps applications quickly find and rank relevant information from large datasets.

1. **Azure OpenAI Service**: A Microsoft Azure service that provides secure access to advanced OpenAI models such as GPT and embedding models. It enables organizations to build generative AI solutions with enterprise security, compliance, and scalability.

1. **Azure AI Evaluation SDK**: A software development kit used to assess the quality, safety, relevance, and performance of AI applications and models. It helps developers benchmark outputs and automate evaluation workflows.

1. **Azure Application Insights**: An application performance monitoring service that collects telemetry, logs, traces, and diagnostics from applications. It helps developers monitor reliability, performance, and user interactions in real time.

1. **Azure AI Tracing (OpenTelemetry)**: A tracing and observability capability that uses OpenTelemetry standards to capture AI workflow execution details, requests, and dependencies. It helps diagnose issues and analyze end-to-end AI application behavior.

1. **Microsoft Foundry AI Red Teaming**: A security testing approach within Microsoft AI ecosystems used to evaluate AI systems for vulnerabilities, harmful outputs, safety risks, and policy violations. It helps improve the robustness and trustworthiness of generative AI applications.
  
## Virtual Machine & Lab Guide

Your virtual machine is your workhorse throughout the workshop. The guide is your roadmap to success.

## Getting Started with the lab

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

3. Next, provide your**Temporary Access pass (1)** and select **Sign In (2)**:

   - Enter **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject>

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
