# Usecase 03 - Create a cross-department intelligent multi-agent automation solution

## Overview

Contoso, a growing global technology company, hires dozens of employees
every month across multiple regions. Their onboarding process involves
coordination between HR, IT, Facilities, Security, and Finance. Each
department uses different systems, and onboarding tasks are often
managed through email threads, spreadsheets, and manual follow-ups. This
leads to delays, missed steps, and a poor first-day experience for new
hires.

To modernize this process, Contoso adopts a **Multi-Agent AI Automation
framework** where specialized AI agents collaborate to orchestrate
onboarding tasks end-to-end.

**Solution architecture**

![A screenshot of a computer AI-generated content may be incorrect.](./media/a1.png)

**Agentic architecture**

![A screenshot of a computer AI-generated content may be incorrect.](./media/a2.png)

**Objective**

The objective of this use case is to demonstrate how a **multi-agent AI
system** can:

- Automate cross-department onboarding workflows

- Coordinate tasks between HR, IT, Facilities, and Finance systems

- Dynamically generate and execute task plans based on new hire details

- Reduce manual effort, delays, and human error

- Provide real-time visibility into onboarding progress

- Ensure a seamless and consistent first-day experience for employees

**Prerequisites**

- **GitHub Account**: You are expected to have your own GitHub login
  credentials. 
  If you do not have an account, please create one by visiting:  
  **<https://github.com/signup?user_email=&source=form-home-signup>**

## Lab Objective

- Task 1: Register Service provider
- Task 2: Open Github Codespaces environment
- Task 3: Provision Services and deploy application to Azure
- Task 4: Post-Deployment Configuration
- Task 5: Verify deployed resources in the Azure portal
- Task 6: Add Authentication in Azure App Service configuration
- Task 7: Review and Explore the Sample Questions for Your Copilot Application
- Task 8: Retail Scenario
- Task 9 :Product Marketing Scenario
- Task 10: HR Onboarding Scenario
- Task 11: RFP Analysis Scenario
- Task 12: Contract Compliance Review Scenario

## Task 1: Register Service provider

1. In the Azure portal search bar, type **Subscriptions (1)**, then select **Subscriptions (2)** from the Services list to open it.

    ![](../Usecase%2001/media/uc2-0.png)

1. On the **Subscriptions** page, select the required subscription (e.g., **Sandbox AI DS**) from the list to open its details.

    ![](../Usecase%2001/media/uc2-21.png)

1. In the selected subscription, navigate to **Settings (1)**, select **Resource providers (2)**, search for **Microsoft.CognitiveServices (3)**, and select it from the **list (4)** and verify that the status is registered with a green tick.

    ![](../Usecase%2001/media/rp0.png)

1. Similarly, search for **Microsoft.AlertsManagement** and verify that the status is registered with a green tick.

## Task 2: Open Github Codespaces environment

> **Note:** You are expected to have your own GitHub login credentials. If you do not have an account, please create one by visiting below shared URL: 
   
   ```
   https://github.com/signup?user_email=&source=form-home-signup
   ```

1. In a new tab, enter the following URL to open the GitHub repository.

    ```
    https://github.com/technofocus-pte/MultiAgentAccelerator/tree/main
    ```

     ![](./media/image12.png)

2. Click on **fork** and select **Create a new fork** to fork the repo. Give unique name to the repo and click on **Create fork** button.

    ![](./media/image13(a).png)
    ![](./media/image13(b).png)

1. Click on **Code (1)**, switch to the **Codespaces (2)** tab, and select **Create codespace on main (3)** to launch the development environment.

    ![](./media/image13(c).png) 

    > If the "This site is trying to open Visual Studio Code" pop-up appears, click **Cancel**.

1. Click the highlighted Back button to navigate back to the previous Github page.

    ![](./media/image13(d).png)

1. Select the **Code (1)** dropdown and navigate to the **Codespaces (2)** tab, select the **ellipsis menu(3)** and choose **Open in Browser (4)**

    ![](./media/image13(e).png)

1. Wait for the Codespaces environment to setup .It takes few minutes
    to setup completely

     ![](./media/image15.png)

     ![](./media/image16.png)

## Task 3: Provision Services and deploy application to Azure

1. Run the following command on the Terminal. It generates the code to copy. Copy the code and press Enter.

   ```
   azd auth login
   ```

    ![](./media/image17.png)

    ![](./media/image18.png)

1. Default browser opens to enter the generated code to verify. Enter the code and click **Next**.

    ![](./media/image19.png)

1. Sign in with your Azure credentials.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image21.png)

    ![](./media/image22.png)

1. Run azd up - This will provision Azure resources

    ```
    azd up
    ```

    ![](./media/image23.png)

1. To create an environment for Azure resources, enter any name of your choice and press enter (eg :** macaedev[@lab.LabInstance.Id](mailto:Ontology@lab.LabInstance.Id)**)

    ![](./media/image24.png)

    ![](./media/image25.png)

1. Select below values.

    - **Select an Azure Subscription to use** : Select your subscription

    - **azureAiServiceLocation**: Sweden Central

    - **‘location' infrastructure parameter:** Central US

    - **Pick a resource group to use:** Existing resource group

      ![](./media/image26.png)

      ![](./media/image27.png)

      ![](./media/image28.png)

      ![](./media/image29.png)

1. This deployment will take *7-10 minutes* to provision the resources in your account and set up the solution with sample data.

    ![](./media/image30.png)

    ![](./media/image31.png)

    ![](./media/image32.png)

1. Now the deployment is complete

    ![](./media/image33.png)

1. After the application has been successfully deployed, you see a URL displayed in the terminal. Copy the **Frontend application URL**

    ![](./media/image34.png)

## Task 4: Post-Deployment Configuration

1. Run the sample data processing script by executing **bash infra/scripts/selecting_team_config_and_data.sh** from the project root to prepare and upload the required data.

   ```
   bash infra/scripts/selecting_team_config_and_data.sh
   ```

   ![](./media/image35.png)

1. After running the command **bash infra/scripts/selecting_team_config_and_data.sh**, authenticate in the browser by opening [**https://microsoft.com/devicelogin**](https://microsoft.com/devicelogin)and entering the **displayed code** to continue the script execution.

    ![](./media/image36.png)

    ![A screenshot of a computer error AI-generated content may be incorrect.](./media/image37.png)

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image38.png)

    ![](./media/image31(a).png)

1. Select your subscription

     ![](./media/image39.png)

1. After running the script, a list of available use case scenarios will appear for selection. You can choose specific scenarios or deploy all use cases at once. Based on your selection, the required datasets and configuration files for those use case(s) will be uploaded to your Azure environment. For this lab, select **6**    

    ![](./media/image40.png)

    ![](./media/image41.png)

    ![](./media/image42.png)

    ![](./media/image43.png)

    ![](./media/image44.png)

## Task 5: Verify deployed resources in the Azure portal

1. Navigate to **Azure portal** and select **Resource groups**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

1. Click on your assigned **Resource group**.

    ![](./media/image46.png)

1. Make sure the below resource got deployed successfully

    - Foundry

    - Foundry project

    - App Service

    - Container registry

    - Azure Cosmos DB account

    - Container App

    - SQL Database

    - Search service

    - Azure Storage account

      ![](./media/image47.png)

      ![](./media/image48.png)

1. On the resource group and click on **Azure Storage account.**

    ![](./media/image49.png)

1. From the left navigation menu, click on **Containers** , Make sure data should be deployed successfully

    ![](./media/image50.png)

1. Go back to resourcegroup and click on **Foundry Project.**

     ![](./media/image51.png)

1. Click **Go to Foundry portal** to verify that the model has been successfully deployed.    
    
    ![](./media/image52.png)

1. In the Foundry portal at the left click on **Models + endpoints** to see the **models** that have been deployed.

    ![](./media/image53.png)

   ### Congratulations!

   You’ve completed the task. Now let’s validate it:
     
   - Hit the **Validate** button for the corresponding task.
   - If successful, proceed to the next task.
   - If not, retry using the lab guide.
   - Need help? cloudlabs-support@spektrasystems.com
   <validation step="ae6ae3fc-c6f0-4b97-a951-0a96aa365c0e" />

## Task 6: Add Authentication in Azure App Service configuration

1. Go back to resourcegroup and click on **App Service(app-macaedevXXX).**

    ![](./media/image54.png)

1. On the web app home page, go to **Settings** and click **Authentication** from the left menu.

    ![](./media/image55.png)

1. Click on **Add identity provider** to see a list of identity providers.

    ![](./media/image56.png)

1. Click on Identity Provider dropdown to see a list of identity providers and select the first option **Microsoft** from the drop-down list.

    ![](./media/image57(a).png)

1. Select **client secret expiration** under App registration and click on **Add** button

    ![A screenshot of a computer AI-generated content may be
 incorrect.](./media/image58.png)

1. You have successfully added app authentication, and now required to log in to access the application.

    ![](./media/image59.png)

    ![](./media/image60.png)

1. On the web app home page, go to **Overview** and click **Browse**

    ![](./media/image61.png)

1. Wait for the web application deployment to complete and click on **Accept**

    ![](./media/image62.png)

    ![](./media/image63.png)

## Task 7: Review and Explore the Sample Questions for Your Copilot Application

1. Select the Team option from the top-left section and explore the different teams.

    ![](./media/image64.png)

    ![](./media/image65.png)

    ![](./media/image66.png)

## Task 8: Retail Scenario

In this Retail scenario, Contoso’s Retail Support Team uses a
multi-agent AI system to improve customer satisfaction. When a customer
shows signs of dissatisfaction - such as poor feedback, repeated
complaints, or low engagement - the system analyzes the situation and
automatically proposes a recovery plan.

This process is powered by multiple AI agents working together to
understand customer history, analyze sentiment, and recommend corrective
actions.

1. Select the Retail team, follow the prompts below.

   **Agents Used:** Customer, Order, Analysis Recommendation

   ![](./media/image67.png)

1. In the **Multi-Agent Planner**, under *Quick tasks*, select ***Satisfaction Plan* to generate an analysis of Emily Thompson’s satisfaction with Contoso along with recommended actions to improve it.**

    ![](./media/image68.png)

1. Click the **Submit** icon as shown in the image.

    ![](./media/image69.png)

    ![](./media/image70.png)

1. Click **"Approve Task Plan"** Button

    ![](./media/image71.png)

    **Observe**: *It goes into "Thinking Process", "Processing your plan"
    and "coordinating with AI Agents".* *Review the output.*

    ![](./media/image72.png)

## Task 9 :Product Marketing Scenario

In this scenario, Contoso’s Product Marketing Team uses a multi-agent AI
system to quickly generate a professional press release for a product
announcement. Instead of manually coordinating between product managers
and marketing writers, AI agents collaborate to gather product
information, shape the messaging, and produce a structured communication
plan.

This scenario demonstrates how AI agents streamline marketing content
creation while ensuring alignment with product details and brand voice.

1. Select the Marketing team, follow the prompts below. 

    Click on **Contoso** at the left side.

    ![](./media/image73.png)

1. Switch to **"Product Marketing Team"** from the top left section and click **"Continue"** button.

    **Agents Used:** Product, Marketing , Proxy

    ![](./media/image74.png)

1. From the Quick Tasks, select **"Draft a press release"** and submit it.

    ![](./media/image75.png)

1. Click the **Submit** icon as shown in the image.

    ![](./media/image76.png)

    >**Note:** Average response time is 15-20 seconds. 

    **Observe:** It will trigger the "Generating Plan Action" and give the
    Proposed Plan with 4 or more Steps.

1. Click on **"Approve Task Plan"** Button.

    ![](./media/image77.png)

    >**Note:** Average response time is around 01 minute.

    **Observe:** It goes into "Thinking Process" and observe a spinner
    "Processing your plan and coordinating with AI Agents". 
    Review the output.

    ![](./media/image78.png)

## Task 10: HR Onboarding Scenario

In this scenario, Contoso’s Human Resources Team uses a multi-agent AI
system to streamline the onboarding of a new employee. Instead of
manually coordinating with IT, facilities, and payroll teams, AI agents
collaborate to collect required details, plan onboarding tasks, and
prepare everything needed for the employee’s first day.

This demonstrates how AI agents can orchestrate cross-functional
onboarding activities efficiently and accurately

1. Select the HR team, follow the prompts below.

    Click on **Contoso** at the left side.

    ![](./media/image79.png)

1. Switch to **"Human Resources Team"** from the top left section and click **"Continue"** button.

    **Agents Used:** HR Helper, Technical support , Proxy

    ![](./media/image80.png)

1. From the Quick Tasks, select **"Onboard New Employee".**

    ![](./media/image81.png)

1. Click the **Submit** icon as shown in the image.

    ![](./media/image82.png)

    >**Note**: Average response time is 15-20 seconds.

     **Observe:** If it asks for additional clarification (Human in the loop) Please provide this information irrespective of what specific information is asked. This will prevent agent for asking for multiple clarifications

     **department**: hr, role: manager, start date: 11/23/2025, orientation date: 11/25/2025, location: onsite, email: js@contoso.com, mentor: Jim Shorts, benefits package: standard, ID Card: yes, salary: 70000, Laptop : Dell 14 Plus

     **Observe:** It will trigger "Generating Plan Action" and "Proposed Plan" with 4 or more Steps.

1. Click on **"Approve Task Plan"** Button.

      ![](./media/image83.png)

    >**Note:** Average response time is around 01 minute 15 seconds. 
    
     **Observe:** It goes into "Thinking Process", "Processing your plan" and "coordinating with AI Agents" Review the output.

      ![](./media/image84.png)

## Task 11: RFP Analysis Scenario

In this scenario, Contoso’s RFP Team uses a multi-agent AI system to
analyze Request for Proposal (RFP) and contract documents. Reviewing
RFPs manually can take days and involves multiple stakeholders such as
legal, compliance, and business teams. With AI agents working together,
the system summarizes the document, identifies risks, and checks
compliance requirements - helping teams respond faster and more
accurately

1. Select the RFP team, follow the prompts below.

    Click on **Contoso** at the left side.

    ![](./media/image85.png)

1. Switch to **"RFP Team"** from the top left section and click **"Continue"** button.

    **Agents Used:** RFP Summary, RFP Risk, RFP Compliance

    ![](./media/image86.png)

    The RFP Analysis Scenario allows users to explore and analyze Request
    for Proposal (RFP) and contract documents.

1. From the Quick Tasks, select **"RFP Document Summary".**

    ![](./media/image87.png)

1. Click the **Submit** icon as shown in the image.

    ![](./media/image88.png)

    >**Note:** Average response time is 10-15 seconds.

    **Observe**: It will trigger the "Generating Plan Action" and give the
    Proposed Plan with 5 or more Steps.

1. Click on **"Approve Task Plan"** Button.

    ![](./media/image89.png)

    ![](./media/image90.png)

## Task 12: Contract Compliance Review Scenario

In this scenario, Contoso’s Contract Compliance Review Team uses a
multi-agent AI system to analyze Non-Disclosure Agreements (NDAs) and
other contract documents. Legal and compliance teams often spend
significant time reviewing contracts for risks, missing clauses, and
policy alignment. With AI agents collaborating, the system can quickly
summarize contracts, identify risks, and verify compliance with internal
standards.

This scenario highlights how AI supports faster, more consistent
contract reviews while keeping humans in control of final decisions.

1. Select the Contract Compliance team, follow the prompts below.

    Click on **Contoso** at the left side.

    ![](./media/image91.png)

1. Switch to the **"Contract Compliance Review Team"** from the
    top left section and click **"Continue"** button.

    **Agents Used:** Contract Summary, Contract Risk, Contract Compliance

    ![](./media/image92.png)

    The Contract Compliance Review Scenario allows users to explore and
    analyze NDA and contract documents for compliance and risk assessment.

1. From the Quick Tasks, select **"NDA Contract Review".**

     ![](./media/image93.png)

1. Click the **Submit** icon as shown in the image.

    ![](./media/image94.png)

    >**Note:** Average response time is 10-15 minutes.

     **Observe**: It will trigger the "Generating Plan Action" and give the
    Proposed Plan with 4 or more Steps

1. Click on **"Approve Task Plan"** Button.

    ![](./media/image95.png)

     >**Note:** Average response time is around 01 minute. 

      **Observe** : It goes into "Thinking Process", "Processing your plan" and"coordinating with AI Agents". 

      **Review the output.**

      This structured approach ensures that users receive automated AI-coordinated task execution and intelligent responses from specialized agents.

      ![](./media/image96.png)    

## Summary

In this use case, Contoso leverages a Multi-Agent Accelerator solution
deployed on Azure to orchestrate employee onboarding. When HR initiates
a new hire request, AI agents collaborate to analyze requirements,
create a task plan, and coordinate actions across enterprise systems.

Specialized agents handle responsibilities such as account provisioning,
hardware allocation, access control, payroll setup, and compliance
verification. A planner agent breaks the goal into structured steps,
executor agents perform actions, and validation agents ensure
completeness and policy alignment - all while keeping humans in the loop
for approvals.

This implementation highlights how multi-agent AI orchestration
transforms a traditionally manual, error-prone HR process into an
intelligent, automated, and scalable workflow. The result is faster
onboarding, improved operational efficiency, and a better experience for
both employees and internal teams.
