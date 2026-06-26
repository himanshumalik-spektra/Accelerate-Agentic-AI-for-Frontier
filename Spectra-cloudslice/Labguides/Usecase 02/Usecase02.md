# Usecase 2- Building multi agent AI solution for streamlining Healthcare prior authorization workflows 

## Overview

In today’s rapidly evolving digital landscape, enterprises like
**Contoso Ltd.** face increasing pressure to streamline operations,
improve decision-making, and scale intelligent automation across
departments. Traditional automation approaches often fall short when
dealing with **complex, cross-functional workflows**, where multiple
systems, teams, and data sources must be coordinated efficiently.

To address these challenges, Contoso adopts the **Multi-Agent Solution
Accelerator**, an advanced AI-driven framework that leverages multiple
specialized agents working collaboratively to execute business
processes.

This accelerator enables organizations to design **intelligent,
agent-based workflows**, where each AI agent is responsible for a
specific function—such as data retrieval, reasoning, validation, and
execution. These agents operate in a coordinated manner, orchestrated
through a central system that interprets user requests and dynamically
assigns tasks.

Built on modern cloud technologies like **Azure OpenAI Service**,
**Azure Cosmos DB**, and containerized microservices, the solution
provides a scalable and extensible foundation for enterprise AI
applications.

**Business Scenario**

Contoso operates across multiple business units including **supply
chain, finance, customer service, and compliance**. Each department
relies on different systems and processes, resulting in:

- Fragmented workflows across departments

- Manual coordination causing delays and inefficiencies

- High risk of human errors in decision-making

- Limited scalability of automation initiatives

To overcome these challenges, Contoso implements a **multi-agent AI system** where:

**Multi-Agent Workflow**

1. **User Request Intake Agent**  
    Captures business queries (e.g., "Approve supplier contract" or
    "Analyze sales performance").

2. **Planning Agent**  
    Breaks down the request into smaller executable tasks.

3. **Data Retrieval Agent**  
    Fetches relevant data from enterprise systems (ERP, CRM, data
    warehouses).

4. **Reasoning Agent**  
    Applies AI models to analyze data and generate insights.

5. **Validation Agent**  
    Ensures accuracy, compliance, and business rule alignment.

6. **Execution Agent**  
    Triggers actions such as approvals, notifications, or report
    generation.

**Prerequisites**

- **GitHub Account**: You are expected to have your own GitHub login credentials. If you do not have an account, please create one by visiting: <https://github.com/signup

## Lab Objective

- Task 1: Register Service provider
- Task 2: Retrieve resource group name and location
- Task 3: Open Github Codespaces environment
- Task 4: Provision Services and deploy application to Azure
- Task 5: Verify deployed resources in the Azure portal
- Task 6: Test the Application

## Task 1: Register Service provider

1. In the Azure portal search bar, type **Subscriptions (1)**, then select **Subscriptions (2)** from the Services list to open it.

    ![](../Usecase%2001/media/uc2-0.png)

1. On the **Subscriptions** page, select the required subscription (e.g., **Sandbox AI DS**) from the list to open its details.

    ![](../Usecase%2001/media/uc2-21.png)

1. In the selected subscription, navigate to **Settings (1)**, select **Resource providers (2)**, search for **Microsoft.CognitiveServices (3)**, and select it from the **list (4)** and verify that the status is registered with a green tick.

    ![](../Usecase%2001/media/rp0.png)

1. Similarly, search for the following resource providers and verify that the status is registered with a green tick.

    - **Microsoft.AlertsManagement**

    - **Microsoft.App**

    - **Microsoft.ContainerRegistry**

    - **Microsoft.OperationalInsights**

    - **Microsoft.Insights**

## Task 2: Retrieve resource group name and location

1. In the Azure portal search bar, type **Resource groups (1)**, then select **Resource groups (2)** from the Services list to open it.

    ![](./media/image17(a).png)

1. In **Resource group** page, copy **resource group name and location** and paste them in a notepad, then **Save** the notepad to use the information in the upcoming tasks.

    ![](./media/image17(b).png)

## Task 3: Open Github Codespaces environment

> **Note:** You are expected to have your own GitHub login credentials. If you do not have an account, please create one by visiting below shared URL: 
   
   ```
   https://github.com/signup?user_email=&source=form-home-signup
   ```
   
1. Open your browser, navigate to the address bar, type or paste the following URL: 

    ```
    https://github.com/technofocus-pte/MultiAIAgentAccelerator
    ```

1. Click on **Fork** (top-right corner) and select **Create a new fork** to create your own copy of the repository.

    ![](./media/image17(c).png)

1. And give a unique name to the repo and click on **Create fork** button.

    ![](./media/uc2-23.png) 

1. Click on **Code (1)**, switch to the **Codespaces (2)** tab, and select **Create codespace on main (3)** to launch the development environment.

    ![](./media/uc2-26.png) 

    > If the "This site is trying to open Visual Studio Code" pop-up appears, click **Cancel**.

1. Click the highlighted Back button to navigate back to the previous Github page.

    ![](./media/image17(d).png)

1. Select the **Code (1)** dropdown and navigate to the **Codespaces (2)** tab, select the **ellipsis menu(3)** and choose **Open in Browser (4)**

    ![](./media/image17(e).png)

1. Wait for the Codespaces environment to setup. It takes few minutes to setup completely.

    ![](./media/image24.png)

    ![](./media/image25.png)

1. The environment is now ready for resource deployment.

    ![](./media/image26.png)

## Task 4: Provision Services and deploy application to Azure

 1. Run the following command on the terminal:

    ```
    azd auth login
    ```

    ![](./media/image27.png)

1. Run the azd auth login command, copy the displayed authentication code, and click on **Enter**.

    ![](./media/image28.png)

1. Default browser opens to enter the generated code to verify. Enter the code and click **Next**.

     ![](./media/image29.png)

1. Select the existing ODL account and click on **Continue**.

    ![](./media/image30.png)

    ![](./media/image31.png)

    ![](./media/image32.png)

1. Navigate back to the terminal and run the following command on the Terminal

    ```
    az login
    ```

    ![](./media/image33.png)

1. Copy the displayed authentication code and complete the sign-in process in your browser to authenticate your environment by clicking on the link.

    ![](./media/image34.png)

    ![](./media/image30.png)

    ![](./media/image31(a).png)

1. Navigate back and type 1 for **Select a subscription or Tenant** and click on Enter.

    ![](./media/image35.png)

1. Run the following command to provision Azure resources.

    ```
    azd up
    ```

    ![](./media/image36.png)

1. Enter any name of your choice and press enter (eg: **prior-auth-devXXXX**)

    ![](./media/image37.png)

    ![](./media/image38.png)

1. Select below values.

    - **Select an Azure Subscription to use** : Press Enter to select your subscription

    - **Enter a value for existingResourceGroup Name:** AgenticAI

    - **Enter location**: Sweden Central

      ![](./media/image39.png)

      ![](./media/image40.png)

      ![](./media/image41.png)

1. Enter **Y** to proceed with the deployment.

    ![](./media/image42.png)

    ![](./media/image43.png)

    ![](./media/image44.png)

    ![](./media/image45.png)

1. The deployment process is currently building container images using a remote Azure Container Registry (ACR) build.

    ![](./media/image46.png)

    ![](./media/image47.png)

1. The frontend container image has been built successfully, and the agent-clinical image build process has started in Azure Container Registry (ACR).

    ![](./media/image48.png)

1. Agent-clinical image build process completed and building agent-coverage build process has started in Azure Container Registry (ACR).

    ![](./media/image49.png)

1. Agent-coverage image build process completed and building agent-compliance build process has started in Azure Container Registry (ACR).

     ![](./media/image50.png)

1. Agent-compliance image build process completed and building agent-synthesis build process has started in Azure Container Registry (ACR).

    ![](./media/image51.png)

1. Agent-synthesis image build process completed

    ![](./media/image52.png)

1. Backend and frontend container app updated successfully

     ![](./media/image53.png)

1. The agent-synthesis image has been built successfully, container apps have been updated, required roles have been ensured, and Foundry MCP tool connections have been created successfully.

     ![](./media/image54.png)

1. The deployment has completed successfully, and the frontend and backend application URLs, along with the backend health check endpoint, are now available for access.

     ![](./media/image55.png)

## Task 5: Verify deployed resources in the Azure portal

1. Navigate back to the portal and select **Resource groups**

    ![](./media/image56.png)

1. Select the **rg-AgenticAI** rg that's created.

1. Make sure the below resource got deployed successfully

    - Foundry

    - Foundry project

    - Container App

    - Container registry

    - Container App Environment     

   ### Congratulations!

   You’ve completed the task. Now let’s validate it:
     
   - Hit the **Validate** button for the corresponding task.
   - If successful, proceed to the next task.
   - If not, retry using the lab guide.
   - Need help? cloudlabs-support@spektrasystems.com
   <validation step="7a657a19-9fda-4427-bf5b-4929e924c67c" />

## Task 6: Test the Application

1. Go back to the codespace and run the following command to verify agent connections and application health status.

    ```
    python scripts/check_agents.py
    ```

    ![](./media/image71.png)

    ![](./media/image72.png)

1. Run the check_agents.py script to verify agent registration, backend health, frontend availability, and tool connections, ensuring all checks pass successfully before proceeding with PA request submission.

    ```
    python scripts/check_agents.py --version 1
    ```

    ![](./media/image73.png)

1. Run the check_agents.py --poll command to continuously monitor agent status, ensuring all components like registration, tool connections, backend health, and frontend availability remain healthy before submitting PA requests.

    ```
    python scripts/check_agents.py --poll
    ```

    ![](./media/image74.png)

1. Click on **Frontend**

    ![](./media/image74.png)

1. Click on **Open** button

    ![](./media/image75.png)

    ![](./media/image76.png)

1. Click **"Load Sample Case"** to populate the form with demo data

    ![](./media/image77.png)

1. Scroll down and click on **"Submit for Review"**

    ![](./media/image78.png)

1. Monitor the progress tracker — you should see all 5 phases complete

    ![](./media/image79.png)

    ![](./media/image80.png)

1. Review the agent results in the dashboard tabs (Compliance, Clinical, Coverage)

    ![](./media/image81.png)

1. Provide any reviewer name and click on **Accept Recommendation**

    ![](./media/image82.png)

    ![](./media/image83.png)   

## Important

   > **Note**: Please delete the resources that you have created in the **AgenticAI** resource group. 

   ![](./media/f13.png) 


   ### Congratulations!

   You’ve completed the task. Now let’s validate it:
     
   - Hit the **Validate** button for the corresponding task.
   - If successful, proceed to the next task.
   - If not, retry using the lab guide.
   - Need help? cloudlabs-support@spektrasystems.com
   <validation step="0cd5f7a0-43ba-4390-88dd-e8f7a18e6a7e" />

## Summary

In this usecase, you successfully built and deployed a **multi-agent
AI-powered healthcare solution** that automates prior authorization
workflows. By integrating multiple intelligent agents, the system
reduces manual intervention, improves operational efficiency, and
ensures accurate, compliant decision-making.

The hands-on experience covered:

- Setting up Azure resources and permissions

- Deploying containerized AI agents

- Orchestrating agent collaboration

- Testing the application with real scenarios

Overall, this use case demonstrates how **multi-agent AI systems can
transform complex healthcare processes** into efficient, scalable, and
intelligent workflows, providing a strong foundation for enterprise AI
adoption.
