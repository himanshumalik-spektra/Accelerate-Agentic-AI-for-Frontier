# Use case 9 - Implement end to end agent operations for Zava's shopping assistant in Microsoft Foundry

## Introduction

This lab demonstrates how to implement **end-to-end agent operations** using Microsoft Foundry by building an intelligent retail assistant named **Cora** for Zava, a home improvement retailer. It walks through the complete lifecycle of an AI solution-from provisioning Azure resources and deploying applications to building, orchestrating, and evaluating AI agents.

You will gain hands-on experience with Azure services such as **Azure AI Search, Azure AI Agent Service, and model evaluation tools**, enabling you to design scalable, intelligent, and production-ready AI applications.

## Scenario

Zava is a fictional retail company that sells home improvement products such as paints, tools, and hardware. To enhance customer experience, Zava introduces **Cora**, an AI-powered shopping assistant.

Cora helps customers:

- Discover suitable products for their needs

- Compare prices and availability

- Get personalized recommendations (e.g., eco-friendly options)

- Answer product-related queries

As Zava grows, Cora evolves from a **single-agent system** into a
**multi-agent architecture**, incorporating specialized agents like:

- Product Inventory Agent

- Customer Service Agent

Additionally, the solution includes **evaluation pipelines** to ensure accuracy, quality, and safety before deployment.

## Objectives

By completing this lab, you will be able to:

- Register required Azure resource providers and set up the environment

- Deploy an AI-powered application using Azure and GitHub Codespaces

- Configure Azure AI Search and create a product index

- Build and interact with a retail AI agent (Cora)

- Implement vector search for product retrieval

- Develop a **multi-agent system** for advanced use cases

- Generate synthetic datasets for testing and evaluation

- Evaluate AI models for performance, quality, and safety

- Apply **GenAIOps practices** for reliable and secure AI deployment

## Task 1: Open Github Codespaces environment

> **Note:** You are expected to have your own GitHub login credentials. If you do not have an account, please create one by visiting below shared URL: 
   
   ```
   https://github.com/signup?user_email=&source=form-home-signup
   ```

1. In a new tab, enter the following URL to open the GitHub repository:

    ```
    https://github.com/technofocus-pte/observeManageScale-agentic-ai-appsFoundry/tree/feb-2026-refresh
    ```

1. Click on **fork** to fork the repo. 

    ![](./media/image11.png)

1. On Create a new fork page, uncheck **Copy the main branch only (1)**, then click **Create fork (2)** to create your repository copy.

    ![](./media/uc9-2.png)

1. Click on the **branch dropdown (main) (1)** and select the **feb-2026-refresh (2)** branch.

    ![](./media/uc9-3.png)

1. Click **Code**, go to the **Codespaces** tab, and select **Create codespace on feb-2026-refresh** to launch the environment.

    ![](./media/uc9-4.png)

1. Wait for the Codespace to finish building.

    ![](./media/image13.png)

    ![](./media/image14.png)

## Task 2: Provision Services and deploy application to Azure

1. In the LabVM search bar, type **Docker (1)** and select **Docker Desktop (2)** from the results to open the application.

    ![](../Usecase%2008/media/uc9-14.png)

    > **Note:** Before moving on to the next steps please make sure your Docker Desktop is up and running. It should not be in stopped state.

1. Click **Accept** to agree to the Docker Subscription Service Agreement and continue.

    ![](../Usecase%2008/media/uc8-23.png)

1. Click **Skip** to bypass the setup questionnaire and proceed.

    ![](../Usecase%2008/media/uc8-19.png)

1. Click **Continue without signing in** to proceed without logging into Docker.

    ![](../Usecase%2008/media/uc8-18.png)

1. Select **Use recommended settings** and click **Finish** to complete the Docker Desktop setup.

    ![](../Usecase%2008/media/uc8-24.png)  

1. Click the **Close (X)** button to exit the Windows Subsystem for Linux (WSL) welcome screen.

    ![](../Usecase%2008/media/uc8-17.png)

1. Wait for Docker Desktop to finish starting the Docker Engine before proceeding.

    ![](../Usecase%2008/media/uc8-16.png) 

1. Navigate back to the Codespace in the in the browser, run the following command in the Terminal and press Enter.

    ```
    az login
    ```

    ![](./media/image16.png)

1. Enter the displayed code in the field and click **Next** to proceed with authentication.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](../Usecase%2008/media/image22new.png)

1. Select your account ODL user account to continue signing in to Azure CLI.

    ![A screenshot of a computer AI-generated content may be
incorrect.](../Usecase%2008/media/image23new.png)

1. Click **Continue** to confirm and complete the sign-in to Microsoft Azure CLI.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](../Usecase%2008/media/image24new.png)

    ![](./media/image20.png)

1. Run the following command in the terminal to navigate into the scripts directory and then start the setup script.

    ```
    cd scripts

    ./1-setup.sh
    ```

    ![](./media/image21.png)

1. Then complete the interactive steps providing responses like this:

    - Enter branch name: **for-release-1.0.4**

      ![](./media/image22.png)

    - Enter environment name: **Ignite-PREL13**

      ![](./media/image23.png)

    - Enter Azure region: **eastus**

      ![](./media/image24.png)

    - Enter Subscription ID: *your subscription id here*

      ![](./media/image25.png)

      - Navigate to https://portal.azure.com/ and if asked login with the credentials

      - In the Azure portal search bar, type **Subscriptions** (1), then select **Subscriptions (2)** from the list to open it.

        ![](../Usecase%2001/media/uc2-0.png)

      - On the **Subscriptions** page, select the required subscription (e.g., **Sandbox AI DS**) from the list to open its details.

        ![](../Usecase%2001/media/uc2-21.png)

      - Copy the Subscription ID from the overview section
        ![](./media/subs.png)

    - Do you want to activate Azure AI Search? (yes/no) [no]: yes

      ![](./media/image26new.png)

    - Press **Enter** for all other fields.

      ![](./media/image27new.png)

1. Run this script - it will create .env with values extracted by Azure CLI. By default it looks for an  resource group but you can override it.

    ```
    cd ForBeginners/.azd-setup

    azd up
    ```

    ![](./media/image28.png)

1. When prompted, type **Y** and press Enter to log in to Azure before continuing with the deployment.

    ![](./media/image29.png)

    ![](./media/image30.png)

1. Enter the displayed code in the field and click **Next** to proceed with authentication.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](../Usecase%2008/media/image22new.png)

1. Select your account ODL user account to continue signing in to Azure CLI.

    ![A screenshot of a computer AI-generated content may be
incorrect.](../Usecase%2008/media/image23new.png)

1. Click **Continue** to confirm and complete the sign-in to Microsoft Azure CLI.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](../Usecase%2008/media/image24new.png)

1. This deployment will take *12-15minutes* to provision the resources in your account and set up the solution with sample data.

    ![](./media/image32.png)

    ![](./media/image33.png)

    > **Note:** Check the deployment status in your resource group to ensure all resources are provisioned successfully.

    ![](./media/image34.png)

    ![](./media/image35.png)

    ![](./media/image36.png)

    ![](./media/image37.png)

## Task 3: Interact with Your AI Agent Using Predefined Questions

1. After the application has been successfully deployed, you see a **Endpoint URL** displayed in the terminal. Copy that **URL**.

    ![](./media/image38.png)

1. Click on **Open** button

    ![](./media/image39.png)

1. Wait for the web application deployment to complete.

    ![](./media/image40.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image.

    ```
    Can you help me choose the best tools for painting my house?
    ```

    ![](./media/image41.png)

    ![](./media/image42.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image.

    ```
    What are the cheapest products available?
    ```

    ![](./media/image43.png)

    ![](./media/image44.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image.

    ```
    Suggest eco-friendly paint options?
    ```

    ![](./media/image45.png)

    ![](./media/image46.png)

1. In the **agent-template-assistant** web app page, enter the following prompt and click on the **Submit icon** as shown in the below image.

    ```
    How much does the Synthetic Brush set cost and do you have it in stock?
    ```

    ![](./media/image47.png)

    ![](./media/image48.png)

## Task 4: Set up .env variables

1. Make sure you are authenticated with Azure CLI. We will use this to retrieve and create a .env file based on the scripts/.env.sample format

    ```
    az login
    ```

1. Run this script from root of repo - it will create .env with values extracted by Azure CLI. By default it looks for an **rg-Ignite-XXX** resource group but you can override it.

    ```
    cd ../..
    
    ./scripts/1-update-env-selfguided.sh
    ```

1. Press enter to continue with the resource group name starting **rg-Ignite-XXX**

    ![](./media/image49new.png)

1. When prompted to **Enter agent name**, press **Enter** to use the default value (`agent-template-assistant`).

    ![](./media/image51.png)

4. We have Zava data in scripts/customization. Let's create a product index in Azure AI Search. Switch to the scripts/ folder and run the command:

    ```
    cd scripts/

    python 2-add-product-index.py
    ```

    ![](./media/image52.png)

    ![](./media/image53.png)

1. This will first run an RBAC update script to give this user the right roles and access to make updates.

1. Then it should upload 49 products to a zava-products index with semantic search, in Azure AI Search.

    ![](./media/image54.png)

    > **Note:** If you get any error while runnnig 2-add-product-index.py file, from the left navigation pane open the .env file and look for the missing variable.

## Task 5: Environment Setup & Validation

In this task, you will configure and validate your development environment. This includes selecting the appropriate Python environment, installing dependencies, and verifying connectivity to Azure services and the Foundry project.

1. Navigate to the **labs/0-setup/** folder and open the **00-validate-setup.ipynb** notebook to begin the environment setup lab.

    ![](./media/image55.png)

1. Click **Select Kernel** in the top-right corner of the notebook and choose the appropriate **Python Environment** to run the lab.

    ![](./media/image56.png)

1. If prompted to select the path, then select the **Python** version i.e **3.12.11**

    ![](./media/image57.png)

1. To import required libraries , run the first cell in the notebook

    ![](./media/image58.png)

1. To import required environment variables , run the Validate Azure Environment Variables cell

    ![](./media/image59.png)

1. Click the **Run (▶)** button to execute the cell and verify that all required Microsoft Foundry environment variables are properly set.

    ![](./media/image60.png)

1. Click the **Run (▶)** button to execute the cell and validate that all required Azure AI Search configuration variables are correctly set.

    ![](./media/image61.png)

    ![](./media/image62.png)

1. Click the **Run (▶)** button to execute the cell and confirm that all embedding model configuration variables are properly set.

    ![](./media/img64.png)

1. Click the **Run (▶)** button to execute the cell and confirm that all Container Apps and registry configuration variables are properly set.

    ![](./media/img65.png)

1. Click the **Run (▶)** button to execute the cell and confirm that all Monitoring and Tracing configuration variables are properly set.

    ![](./media/img66.png)

1. Click the **Run (▶)** button to execute the cell and confirm that all Tracing configuration variables are properly set.

    ![](./media/img67.png)

1. Click the **Run (▶)** button to execute the cell to see the Validation summary.

    ![](./media/img68.png)


## Task 6: Build "Cora for Zava" - An AI-Powered Retail Shopping Assistant Using Azure AI Agent Service

**Cora** is a customer service chatbot for **Zava** - a fictitious retailer of home improvement goods for DIY enthusiasts. Zava offers a wide range of products including paint, power tools, hand tools, hardware, electrical supplies, and plumbing materials. Cora helps customers find products, check inventory, and provides personalized assistance for home improvement projects.

1. Navigate to the **labs/1-agents/** folder and open the **11-build-cora-retail-agent.ipynb** notebook to begin the environment setup lab.

    ![](./media/image64.png)

1. Click **Select Kernel** in the top-right corner of the notebook and select the appropriate **Python** version i.e **3.12.11** to run the lab.

1. Click the **Run (▶)** button to execute the cell and verify that all required Python packages are installed successfully.

    ![](./media/image65.png)

1. Click the **Run (▶)** button to execute the cell and load environment variables from the .env file into your notebook.

    ![](./media/image66.png)

1. Click the **Run (▶)** button to execute the cell and establish a connection to Microsoft Foundry using the configured credentials.

    ![](./media/image68.png)

1. Click the **Run (▶)** button to execute the cell to create Cora agent     
    
    ![](./media/image69.png)

    ![](./media/image70.png)

1. The notebook cell successfully uploads paint product files from the specified folder, showing a confirmation message that 10 files were uploaded after execution.

    ![](./media/image71.png)

1. The notebook cell reads and displays the uploaded paint product files, listing each file name along with its product title and price extracted from the file content.

    ![](./media/image72.png)

1. The cell executes successfully, creating a vector store named **"Zava-Paint-Products"** using the uploaded files, and confirms that the vector store was created with 10 files.

    ![](./media/image73.png)

1. Run the cell to update the agent by attaching the file search tool, enabling it to query and retrieve information from the created vector store of uploaded product files.

    ![](./media/image74.png)

1. Run the cell to create a new conversation thread and display a confirmation message indicating that the thread has been successfully created.

    ![](./media/image75.png)

1. Run the cell to create a user message in the conversation thread and display a confirmation message indicating that the message has been successfully sent to Cora.

    ![](./media/image76.png)

1. Run the cell to execute the agent, allowing it to process the user message using the file search tool, and display a confirmation message indicating that the agent run has completed successfully.

    ![](./media/image77.png)

1. Run the cell to retrieve all messages from the conversation thread and display Cora's response along with the user's message in a
    formatted conversation view.

    ![](./media/image78.png)

    ![](./media/image79.png)

1. Run the cell to define a helper function that sends a message to Cora, processes it using the agent, and retrieves the assistant's response from the conversation thread.

    ![](./media/image80.png)

    ![](./media/image81.png)

1. Run the cell to test Cora with Paint related questions

    ![](./media/image82.png)

    ![](./media/img82.png)

    ![](./media/image83.png)

    ![](./media/image84.png)

    ![](./media/image85.png)

    ![](./media/image86.png)

1. Run the cell to view full conversation history

    ![](./media/image87.png)

    ![](./media/image88.png)

## Task 7: Cora-For-Zava: Building a Multi-Agent Retail Assistant System

**Cora** is a customer service chatbot for **Zava** - a fictitious retailer of home improvement goods for DIY enthusiasts. As Zava retail stores grow, Cora needs to handle more complex customer needs. This notebook shows you how to evolve from a single agent to a multi-agent system, with specialized agents for inventory management and customer service. You'll learn to orchestrate multiple agents working together to provide sophisticated and role-specific assistance.

1. Navigate to the **labs/1-agents/** folder and open the **12-agent-framework-orchestration.ipynb** notebook to begin the environment setup lab.

    ![](./media/image89.png)

1. Click **Select Kernel**, then choose the **Python 3.12.11** environment to run the notebook.

    ![](./media/image90.png)

1. Click the **Run (▶)** button to execute the cell and verify that all required Python packages are installed successfully.

    ![](./media/image91.png)

1. Click the **Run (▶)** button to execute the cell and import all Python libraries .

    ![](./media/image92.png)

1. Click the **Run (▶)** button to execute the cell and load configurations .

    ![](./media/image93.png)

1. Run the cell to verify your Azure login by creating Azure CLI credentials and confirming that a token is successfully retrieved.

    ![](./media/image94.png)

1. Run the cell to connect to the Azure AI Project, retrieve the Azure AI Search connection, and confirm that the project client has been successfully created.

    ![](./media/image95.png)

1. Run the cell to define the Product Inventory Agent instructions and display a confirmation message along with the instruction length.

    ![](./media/image96.png)

1. Run the cell to define the Product Inventory Agent instructions and display a confirmation message along with the instruction length.

    ![](./media/image97.png)

1. Run the cell to create the customer service Agent with Azure AI Search capabilities and display a confirmation message indicating that the agent has been successfully created.

    ![](./media/image98.png)

    ![](./media/image99.png)

1. Run the cell to test the Product Inventory Agent by sending a sample query, processing it with Azure AI Search, and displaying the agent's response along with relevant citations.

    ![](./media/image100.png)

    ![](./media/image101.png)

1. Run the cell to test the Customer Service Agent by sending the same query, processing it with Azure AI Search, and displaying the agent's response along with relevant citations.

    ![](./media/image102.png)

    ![](./media/image103.png)

1. Run the cell to build the smart router that automatically sends request to right agent based on the question.

    ![](./media/image104.png)

1. Run the cell to test the smart router.

    ![](./media/image105.png)

    ![](./media/image106.png)

1. Run the cell to clean-up the resources.

    ![](./media/image107.png)

## Task 8: Cora-For-Zava: Generating Synthetic Test Datasets for Evaluation

**Cora** is a customer service chatbot for **Zava** - a fictitious retailer of home improvement goods for DIY enthusiasts. To ensure Cora provides accurate and helpful responses about hardware and home improvement products, you need quality test data. This notebook helps you generate synthetic query-response pairs based on your product catalog, creating a robust evaluation dataset to measure Cora's performance before deployment.

1. Navigate to the **labs/2-models/** folder and open the **21-simulated-dataset.ipynb** notebook to begin the environment setup lab.

    ![](./media/image108.png)

1. Click **Select Kernel**, then choose the **Python 3.12.11** environment to run the Lab 02 notebook

    ![](./media/image109.png)

1. Run the cell to **load environment variables** from the .env file and validate that all required Azure OpenAI and Azure AI Search credentials are present before proceeding.

    ![](./media/image111.png)

1. Run the cell to read the Azure AI Search connection parameters (endpoint, API key, and index name) from environment variables and confirm the index is configured.

    ![](./media/image112.png)

1. Run the cell to create an **AzureOpenAIModelConfiguration** object using your environment credentials, which the simulator will use to generate synthetic queries and responses.

    ![](./media/image113.png)

1. Run the cell to instantiate the **Azure AI Evaluation Simulator** with the model configuration, making it ready to produce synthetic dataset entries.

    ![](./media/image114.png)

1. Run the cell to define the **search_index_for_content function**, which queries your Azure AI Search index via REST API and returns the top matching product content for a given search query.

    ![](./media/image115.png)

1. Run the cell to **test the search function** with a sample query ("eggshell paint") and verify that content is successfully retrieved from the Azure AI Search index.

    ![](./media/image116.png)

1. Run the cell to define the **rag_application_callback async function**, which extracts the user query from a message, retrieves relevant context from Azure AI Search, and generates a grounded response using Azure OpenAI.

    ![](./media/image117.png)

1. Run the cell to confirm that retrieved content is available and non-empty, ensuring the simulator has valid product catalog text to work with before generating data.

    ![](./media/image118.png)

1. Run the cell to execute the simulator against the RAG callback, **generating 10 synthetic single-turn query-response pairs** grounded in your product catalog content.

    ![](./media/image119.png)

1. Run the cell to serialize all **generated simulator outputs** to a 21-simulate-datasets.jsonl file in JSON Lines format, ready for use in downstream evaluation workflows.

    ![](./media/image120.png)

1. Run the cell to **load the saved .jsonl dataset** into a pandas DataFrame and display a preview of the generated query-response-context triples to verify structure and data quality.

    ![](./media/image121.png)

## Task 9: Cora-For-Zava: Evaluating and Selecting the Best AI Model

**Cora** is a customer service chatbot for **Zava** - a fictitious retailer of home improvement goods for DIY enthusiasts. To ensure Cora provides the best customer experience, you need to select the right foundation model. With multiple Azure OpenAI models available (GPT-4o, GPT-4o-mini, GPT-4), you need to evaluate which model delivers the best balance of quality, safety, and performance for your retail use case.

1. Navigate to the **labs/2-models/** folder and open the **22-evaluate-models.ipynb** notebook to begin the environment setup lab.

    ![](./media/image123.png)

1. Click **Select Kernel**, then choose the **Python 3.12.11** environment to run the Lab 02 notebook

    ![](./media/image124.png)

1. Click **Run All** to execute all the cells in the notebook and observe the outputs.

    ![](./media/image110.png)

    ![](./media/image125.png)

    ![](./media/image126.png)

    ![](./media/image127.png)

    ![](./media/image128.png)

    ![](./media/image129.png)

    ![](./media/image130.png)

    ![](./media/image131.png)

    ![](./media/image132.png)

    ![](./media/image133.png)

    ![](./media/image134.png)

    ![](./media/image135.png)

    ![](./media/image136.png)

    ![](./media/image137.png) 

## Task 10: Cora-For-Zava: Getting Started with Your First AI Evaluation Flow

**Cora** is a customer service chatbot for **Zava** - a fictitious retailer of home improvement goods for DIY enthusiasts. Before deploying
Cora to help customers, you need to ensure it provides accurate, safe, and helpful responses. Evaluation is the foundation of trust in AI
applications, making it a critical part of the Generative AI Ops (GenAIOps) lifecycle. Without rigorous evaluation, Cora could produce content that is fabricated, irrelevant, harmful, or vulnerable to adversarial attacks.

1. Navigate to the **labs/** **4-evaluation/** folder and open the **41-first-evaluation-run.ipynb** notebook to begin the environment setup lab.

    ![](./media/image138.png)

1. Click **Select Kernel**, then choose the **Python 3.12.11** environment to run the Lab 02 notebook

    ![](./media/image139.png)

1. Click **Run All** to execute all the cells in the notebook and observe the outputs.

    ![](./media/image110.png)

    ![](./media/image140.png)

    ![](./media/image141.png)

    ![](./media/image142.png)

    ![](./media/image143.png)

    ![](./media/image144.png)

    ![](./media/image145.png)

    ![](./media/image146.png)

    ![](./media/image147.png)

    ![](./media/image148.png)

    ![](./media/image149.png)

    ![](./media/image150.png)

    ![](./media/image151.png)

    ![](./media/image152.png)

    ![](./media/image153.png)

## Task 11: Cora-For-Zava: Exploring AI Response Quality Evaluators

**Cora** is a customer service chatbot for **Zava** - a fictitious retailer of home improvement goods for DIY enthusiasts. Cora must provide accurate, relevant, and coherent responses about hardware and
home improvement products to Zava customers. This notebook helps you assess response quality using specialized evaluators for groundedness, relevance, coherence, fluency, and similarity-ensuring Cora meets the high standards expected in a production retail environment.

1. Navigate to the **labs/** **4-evaluation/** folder and open the **42-evaluate-quality.ipynb** notebook to begin the environment setup lab.

    ![](./media/image154.png)

1. Click **Select Kernel**, then choose the **Python 3.12.11** environment to run the Lab 02 notebook.

    ![](./media/image155.png)

1. Run the cell to verify you are authenticated with Azure by displaying the currently signed-in user's account details..

    ![](./media/image156.png)

1. Run the cell to create a **DefaultAzureCredential** object that will be used to authenticate all subsequent SDK calls against Azure services.

    ![](./media/image157.png)

1. Run the cell to read Azure subscription, resource group, project, and Foundry service name from environment variables and construct both the project dictionary and the project URL needed for portal integration.

    ![](./media/image158.png)

1. Run the cell to **load environment variables** from the .env file and create an AzureOpenAIModelConfiguration object that points to the judge model used by all AI-assisted evaluators.

    ![](./media/image159.png)

1. Coherence: Run the cell to instantiate the **CoherenceEvaluator** and score a sample Cora response on how logically connected and easy to follow it reads (scale 1–5).

    ![](./media/image160.png)

1. Fluency: Run the cell to instantiate the **FluencyEvaluator** and score a sample Cora response on grammatical accuracy, vocabulary range, and overall readability (scale 1–5).

    ![](./media/image161.png)

1. Composite QA: Run the cell to instantiate the **QAEvaluator** and score a single Cora response across six quality dimensions — Relevance, Groundedness, Fluency, Coherence, Similarity, and F1 — in one call.

    ![](./media/image162.png)

1. Retrieval: Run the cell to instantiate the **RetrievalEvaluator** and score how well the retrieved context chunks address the query and rank the most relevant chunks at the top.

    ![](./media/image163.png)

1. Groundedness: Run the cell to instantiate the **GroundednessEvaluator** and verify that Cora's response stays within the bounds of the provided product context without fabricating information.

    ![](./media/image164.png)

1. Coherence (pprint): Run the cell to run the **CoherenceEvaluator** on a screwdriver-related query and display the full structured result dictionary including score, reasoning, and pass/fail threshold.

    ![](./media/image166.png)

1. Response Completeness: Run the cell to instantiate the **ResponseCompletenessEvaluator** and measure how much of the expected ground truth information is covered in Cora's response.

    ![](./media/image167.png)

1. Similarity: Run the cell to instantiate the **SimilarityEvaluator** and score the semantic closeness between Cora's response and the ground truth using an LLM-as-judge approach (scale 1–5).

    ![](./media/image168.png)

1. F1 Score: Run the cell to instantiate the **F1ScoreEvaluator** and measure the token-overlap precision and recall between Cora's response and the ground truth as a 0–1 score.

    ![](./media/image169.png)

1. BLEU Score: Run the cell to instantiate the **BleuScoreEvaluator** and score the n-gram overlap between Cora's response and the ground truth using the standard BLEU metric.

    ![](./media/image170.png)

1. GLEU Score: Run the cell to instantiate the **GleuScoreEvaluator** and compute the Google-BLEU score, which improves on BLEU by applying a per-sentence reward objective for both precision and recall.

    ![](./media/image171.png)

1. ROUGE Score: Run the cell to instantiate the **RougeScoreEvaluator** and measure recall-oriented n-gram overlap between the response and ground truth using ROUGE-L, returning precision, recall, and F1 scores.

    ![](./media/image172.png)

1. METEOR Score: Run the cell to instantiate the **MeteorScoreEvaluator** and score response similarity against the ground truth while accounting for synonyms, stemming, and paraphrasing beyond simple token overlap.

    ![](./media/image173.png)

1. Custom Evaluators: Run the cell to define and test two **custom evaluators** — a function-based response_length evaluator that counts characters, and a class-based BlocklistEvaluator that flags responses containing restricted words.

    ![](./media/image174.png)

1. Run All Evaluators: Run the cell to execute a full **multi-evaluator run** using evaluate() against the 42-evaluate-quality.jsonl dataset, scoring every row across Content Safety, Coherence, Relevance, Groundedness, Fluency, and Similarity, then publishing results to both the Microsoft Foundry portal and a local JSON file.

    ![](./media/image175.png)

    ![](./media/image176.png)

    ![](./media/image177.png)

## Task 12: Cora-For-Zava: Exploring AI Safety Evaluators for Secure Responses

**Cora** is a customer service chatbot for **Zava** - a fictitious retailer of home improvement goods for DIY enthusiasts. Before deploying Cora to serve Zava customers, you must ensure it generates safe, appropriate content and is protected against adversarial attacks. This notebook guides you through Microsoft Foundry's safety evaluators, helping you identify and mitigate risks like harmful content, jailbreak attempts, and protected material violations to maintain a secure and trustworthy customer experience.

1. Navigate to the **labs/** **4-evaluation/** folder and open the **43-evaluate-safety.ipynb** notebook to begin the environment setup lab.

1. Click **Select Kernel**, then choose the **Python 3.12.11** environment to run the Lab 02 notebook

    ![](./media/image178.png)

1. Click **Run All** to execute all the cells in the notebook and observe the outputs.

    ![](./media/image110.png)

    ![](./media/image179.png)

    ![](./media/image180.png)

    ![](./media/image181.png)

    ![](./media/image182.png)

    ![](./media/image183.png)

## Summary

In this lab, you implemented a complete **end-to-end AI solution** for a retail assistant using Microsoft Foundry. Starting from environment setup and deployment, you built Cora, enhanced it with search capabilities, and evolved it into a multi-agent system.

You also explored critical aspects of production AI systems, including:

- Data indexing and retrieval

- Agent orchestration

- Model evaluation and selection

- Safety and quality validation

By the end of this exercise, you gained practical experience in designing, deploying, and managing **scalable, intelligent AI applications** that deliver real-world business value.
