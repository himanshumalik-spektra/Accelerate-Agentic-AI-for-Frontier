# Usecase 08 - Safeguard your agents with AI Red Teaming Agent in Microsoft Foundry

## Scenario

Zava is a fast-growing technology and services company that manages large volumes of internal documentation, product manuals, training material, and customer-support knowledge. Employees frequently need quick, accurate responses without manually searching through dozens of files and knowledge repositories.

To improve efficiency, Zava wants to deploy an intelligent AI-powered assistant that can read, understand, and retrieve answers from its internal documents. The company chooses Azure AI Agent Service to build an interactive chat interface, where employees can simply ask a question and receive a precise, citation-supported answer grounded in Zava's internal knowledge.

![Architecture diagram showing that user input is provided to the Azure
Container App, which contains the app code. With user identity and
resource access through managed identity, the input is used to form a
response. The input and the Azure monitor are able to use the Azure
resources deployed in the solution: Application Insights, Microsoft
Foundry Project, Foundry Tools, Storage account, Azure Container App,
and Log Analytics Workspace.](./media/image1.png)

## Introduction

As organizations adopt AI agents to automate workflows, answer questions, and retrieve internal knowledge, ensuring these systems
behave safely and reliably becomes critical. Zava, a fast-growing technology company, is deploying an internal AI knowledge assistant to help employees quickly retrieve information from documents, manuals, and
training materials. To protect this AI agent against harmful behavior, security gaps, or unintended responses, Zava leverages Microsoft Foundry's AI Red Teaming capabilities.

This use case demonstrates how to build a secure end-to-end AI agent, evaluate its behavior, detect risks through automated red teaming, and monitor its performance using Azure's observability tools. Through guided steps, you will deploy the agent, test its retrieval capabilities, run red teaming evaluations, and enforce continuous monitoring to ensure safety, accuracy, and compliance.

## Objectives

- Understand how to build a document-aware AI knowledge assistant using Azure AI Agent Service.

- Deploy Azure resources and configure the full solution using Azure Developer CLI.

- Interact with the AI agent using predefined and custom prompts to validate retrieval accuracy.

- Execute built-in evaluators to measure agent quality, safety, intent resolution, and tool-call correctness.

- Run automated AI Red Teaming tests to identify vulnerabilities, harmful behaviors, or safety violations.

- Analyze red teaming results in Microsoft Foundry, including attack strategies and failure cases.

- Enable tracing, monitoring, and continuous evaluation to track real-time agent behavior in production.

- Learn best practices for securing AI agents through consistent testing, observability, and model governance.

## Task 1: Register Service provider

1. Navigate to https://portal.azure.com/ and if asked login with the credentials

1. In the Azure portal search bar, type **Subscriptions** (1), then select **Subscriptions (2)** from the list to open it.

    ![](../Usecase%2001/media/uc2-0.png)

1. On the **Subscriptions** page, select the required subscription (e.g., **Sandbox AI DS**) from the list to open its details.

    ![](../Usecase%2001/media/uc2-21.png)

1. In the selected subscription, navigate to **Settings (1)**, select **Resource providers (2)**, search for **Microsoft.CognitiveServices (3)**, and select it from the **list (4)** and verify that the status is registered with a green tick.

    ![](../Usecase%2001/media/rp0.png)

1. Similarly, search for **Microsoft.AlertsManagement** and verify that the status is registered with a green tick.

    ![](./media/image0.png)

## Task 2: Open Github Codespaces environment

> **Note:** You are expected to have your own GitHub login credentials. If you do not have an account, please create one by visiting below shared URL: 
   
   ```
   https://github.com/signup?user_email=&source=form-home-signup
   ```

1. In a new tab, enter the following URL to open the GitHub repository, then click on **fork** to fork the repo.

   ```
   https://github.com/technofocus-pte/ai-agent.git
   ```

    ![](./media/uc8-20.png)

1. On Create a new fork page, keep everything as default and click on **Create fork** button.

    ![](./media/uc8-21.png)

1. Click **Code (1)**, go to the **Codespaces (2)** tab, and select **Create codespace on main (3)** to launch the environment.

    ![](./media/aaau8t2s3.png)

1. Click the highlighted Back button to navigate back to the previous Github page.

    ![](./media/image17(d).png)

1. Select the **Code (1)** dropdown and navigate to the **Codespaces (2)** tab, select the **ellipsis menu(3)** and choose **Open in Browser (4)**.

    ![](./media/image17(e).png)

1. Wait for the Codespaces environment to setup .It takes few minutes to setup completely.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

    ![](./media/image19.png)

    > **Note:** It can take a few minutes for the codespace to spin up completely.

## Task 3: Provision Services and deploy application to Azure

1. Run the following command in the Terminal and press Enter.

   ```bash
   azd auth login
   ```

   ![A screenshot of a computer AI-generated content may be incorrect.](./media/aaau8t3s8.png)

2. Copy the displayed authentication code from the terminal, press **Enter**, and complete the Azure login in the browser.

   ![A screenshot of a computer AI-generated content may be incorrect.](./media/aaau8t3s9.png)

1. Enter the displayed code in the field and click **Next** to proceed with authentication.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image22new.png)

1. Select your account ODL user account to continue signing in to Azure CLI.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23new.png)

1. Click **Continue** to confirm and complete the sign-in to Microsoft Azure CLI.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image24new.png)

1. Verify that authentication is successful (logged in message appears), then proceed with the next command in the terminal.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t3s13.png)

1. Run the following command in the terminal to create a new environment.

   - Enter a unique environment name as **ai-agent-<inject key="DeploymentID" enableCopy="false"/>** and press **Enter**.

      ```
      azd env new
      ```

      ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc8-27.png)

1. Run azd up - This will provision Azure resources

    ```
    azd up
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

1. If prompted with **Would you like to check your Azure development tools?:**, type **Yes** and click on Enter.

     ![](./f30.png)
   
1. If prompted with any tools installations like Github & Azure tools, click on **Enter** to proceed with the installation.

     ![](./f31.png)

1. When prompted with the following, provide the below values:
   
    - Select an Azure subscription to use: Click on **Enter**
    - **AzureAiServiceLocation**: East US 2, East US, West US , West US 3 , Sweden Central.

1. This deployment will take *10-15 minutes* to provision the resources in your account and set up the solution with sample data.

1. You can monitor the deployment progress using the provided Azure Portal link until provisioning completes.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc8-31.png)

1. After the application has been successfully deployed, you see a URL displayed in the terminal. Copy the **Endpoint URL**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

## Task 4: Verify deployed resources in the Azure portal

1. In the Azure portal search bar, type **Resource groups** and select **Resource groups** from the results.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc8-15.png)

1. From the **Resource groups** list, select the newly created resource group with prefix **rg-ai-agent-<inject key="DeploymentID" enableCopy="false"/>** to open it.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc8-48.png)

1. Make sure the below resources got deployed successfully:

   - Foundry
   - Foundry project
   - Application Insights
   - Container App
   - Container Apps Environment
   - Container registry
   - Managed Identity
   - Log Analytics workspace
   - Storage account

   ![A screenshot of a computer AI-generated content may be incorrect.](./media/aaau8t4s3.png)

1. Select the **Azure Storage account** from the list.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t4s4.png)

1. Select the **Azure Storage account** that has been created. From the left navigation menu, click on **Data Storage (1)** > **Containers (2)** and **verify (3)** if all the containers have been deployed.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

1. Navigate back to the resource group and select the **Foundry Project.** Click on **Go to Foundry portal** to verify if all the models have been successfully deployed. 

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/aaau8t4s6.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

1. Click on **Build (1)** from the top menu and click on **Deployments (2)** from the left navigation menu to verify the **models (3)** that have been deployed.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/f400.png)

1. Navigate back by clicking on the **Microsoft Foundry (1)** option from the top left. Copy the **Project endpoint 
(2)** and save it in a notepad for future use.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t4s7.0-1.png)

## Task 5: Interact with Your AI Agent Using Predefined Questions

1. Navigate back to GitHub Codespaces and select the **Endpoint URL**.

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/image48.png)

1. Click on the **Open** button.

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/image49.png)

1. Wait for the web application deployment to complete.

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/aaau8t5s3.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image. Observe the response.

    ```
    What's the best tent under $200 for two people, and what features does it include?
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s4.png)

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/aaau8t5s4.0.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image. Observe the response.

   ```
   What has David Kim purchased in the past, and based on his buying patterns, what other products might interest him?
   ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s5.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s5.0.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image. Observe the response.

    ```
    Compare hiking boots from different brands in your inventory - which ones offer the best value for durability and comfort?
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s6.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s6.0.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image. Observe the response.

   ```
   How do I set up the Alpine Explorer Tent, and what should I know about its weather protection features?
   ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s7.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s7.0.png)

4. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image. Observe the response.

   ```
   I'm planning a 3-day camping trip for my family. What complete setup would you recommend under $500, and why?
   ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s8.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t5s8.0.png)

## Task 6: Sample Prompts for Azure AI Search

1. In the **agent-template-assistant** web app page, select **New Chat.**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t6s1.png)

2. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image. Observe the response.

   ```
   Which products have wireless charging capabilities and what are their battery life specifications?
   ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t6s2.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t6s2.0.png)

1. In the **agent-template-assistant** web app page, enter the following prompts and review the response. 

    ```
    Find products designed for comfort and temperature control - what features do they offer?
    ```

    ```
    What care and maintenance instructions are available for electronic products with waterproof features?
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t6s3.png)

## Task 7: Agent Evaluation

Microsoft Foundry offers a number of built-in evaluators to measure the quality, efficiency, risk and safety of your agents. For example, intent resolution, tool call accuracy, and task adherence evaluators are
targeted to assess the end-to-end and tool call process quality of agent workflow, while content safety evaluator checks for inappropriate content in the responses such as violence or hate. You can also create custom evaluators tailored to your specific requirements, including custom prompt-based evaluators or code-based evaluators that implement your unique assessment criteria.

1. Go back to **GitHub Codespaces**, open the terminal, and run the Python requirements script below to set up your environment.

   ```bash
   python -m pip install -r src/requirements.txt
   ```

   ![A screenshot of a computer AI-generated content may be incorrect.](./media/image65.png)

   ![A screenshot of a computer AI-generated content may be incorrect.](./media/image66.png)

   > **Note:** If you encounter dependency conflict errors during installation, run the following commands to remove the conflicting package and reinstall the required dependencies:
   >
   > ```bash
   > pip uninstall api -y
   > python -m pip install -r src/requirements.txt
   > ```

2. Run the following script to set the environment variables.

   ```bash
   export AZURE_AI_AGENT_DEPLOYMENT_NAME="gpt-5-mini"

   export AZURE_EXISTING_AGENT_ID="agent-template-assistant:1"

   export AZURE_AI_AGENT_NAME="agent-template-assistant"
   ```

1. Select the **tests (1)** folder from the left hand panel and select the **test_utils.py (2)** file. **Paste (3)** the endpoint that you copied in **Task 4 and Step 8** between the empty double quotes **""** on line 40 after **AZURE_EXISTING_AIPROJECT_ENDPOINT**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/f401.png)

1. Run the following script:

    ```
    export AZURE_EXISTING_AIPROJECT_ENDPOINT="Paste you AZURE_EXISTING_AIPROJECT_ENDPOINT here"
    ```
    > **Note**- Don't forget to paste your endpoints in the command before running it.

1. Press `Ctrl+S` to save the file.

1. Run the following script:

    ```
    pytest tests/test_evaluation.py -s
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t7s10.png)

1. Upon completion, the test will display an URL in the output where you can review the detailed evaluation results in the Microsoft Foundry UI, including individual evaluator passing scores and explanations. Select the **URL**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image69.png)

1. Click on **Open**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t7s10.0.png)

## Task 8: AI Red Teaming Agent

The AI Red Teaming Agent is a powerful tool designed to help organizations proactively find security and safety risks associated with
generative AI systems during design and development of generative AI models and applications.

In the red teaming test script, you will be able to set up an AI Red Teaming Agent to run an automated scan of your agent in this sample. The test demonstrates how to:

- Create a red-teaming evaluation

- Generate taxonomies for risk categories (e.g., prohibited actions)

- Configure attack strategies (Flip, Base64) with multi-turn
  conversations

- Retrieve and analyze red teaming results

No test dataset or adversarial LLM is needed as the AI Red Teaming Agent
will generate all the attack prompts for you.

1. Navigate back to the Codespaces tab and run the following script to set the variable.

    ```
    export AZURE_EXISTING_AGENT_ID="agent-template-assistant:1"
    ```

1. Run the red teaming test in your local development environment:

    ```
    pytest tests/test_red_teaming.py -s
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image72.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

1. Upon completion, the test will display an URL in the output where you can review the detailed red teaming evaluation results in the Microsoft Foundry UI, including attack inputs, outcomes, and reasons.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image74.png)

1. Click on **Open** button

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

## Task 9: Tracing and monitoring

1. Enable tracing by setting the environment variable

    ```
    azd env set ENABLE_AZURE_MONITOR_TRACING true
    ```

1. Deploy the resources

    ```
    azd deploy
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image77.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image78.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image79.png)

## Task 10: Console traces

1. You can view console traces in the Azure portal by executing the below command. You can get the link to the resource group with the azd tool:

    ```
    azd show
    ```

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image80.png)

    >**Note:** Choose your container app from the list of resources in the resource group. Then open 'Monitoring' and 'Log Stream'. Choose the 'Application' radio button to view application logs. You can choose between real-time and historical using the corresponding radio buttons. Note that it may take some time for the historical view to be updated with the latest logs.

## Task 11: Agent traces and Monitor

You can view both the server-side and client-side traces, cost and
evaluation data in Microsoft Foundry.

1. navigate back to the Microsoft Foundry, from the top navigation, select **Build** again and from the left menu, click **Agents (1)**, then select the **agent-template-assistant (2)** agent from the list to open it.

1. Select the **Traces**

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/aaau8t11s2.png)

    ![Tracing Tab](./media/aaau8t11s2.0.png)

1. Click on the **Monitor** tab to view the agent’s performance metrics and activity.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t11s3.png)

1. Scroll down in the **Monitor tab**, and check the **Operational metrics** section.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/aaau8t11s4.png)

    ![Monitor Dashboard](./media/image86.png)

## Task 12: Continuous Evaluation

Continuous evaluation is an automated monitoring capability that continuously assesses your agent's quality, performance, and safety as it handles real user interactions in production.

During container startup, continuous evaluation is enabled by default and pre-configured with a sample evaluator set to evaluate up to 5 agent responses per hour. Continuous evaluation does not generate test
inputs-instead, it evaluates real user conversations as they occur. This means evaluation runs are triggered only when actual users interact with your agent, and if there are no user interactions, there will be no evaluation entries.

To customize continuous evaluation from the Microsoft Foundry:

1. Select **Monitor(1)** Choose the agent you want to enable continuous evaluation for from the agent list and click on **Settings (2)**

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/aaau8t12s1.png)

1. In the **Monitor settings** pane, enable **Continuous evaluation (1)**, set **Maximum runs per hour** to **1** **(2)**, and then click **Submit (3)**.
    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/uc8-52new.png)

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/image89new.png)

## Summary

In this use case, you built and secured an AI agent capable of retrieving information from Zava's internal documents using Azure AI Agent Service. After deploying the environment and verifying key resources-including Container Apps, Azure Cosmos DB, Storage, Search, and Foundry-you interacted with the agent to test its ability to answer operational and product-related queries. You then performed automated evaluations using Microsoft Foundry's assessment tools and executed comprehensive AI Red Teaming scans to uncover potential risks. Finally, you enabled tracing, logging, and continuous evaluation to monitor real-world usage and ongoing model safety. This end-to-end workflow equips Zava with a reliable, secure, and scalable AI assistant that provides accurate information while meeting enterprise-grade safety and governance standards.
