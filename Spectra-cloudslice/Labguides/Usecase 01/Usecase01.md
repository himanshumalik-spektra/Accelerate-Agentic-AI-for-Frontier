# Usecase 01 - Create a Knowledge Assistant agent for HR in Copilot Studio  that leverages Azure AI Search

## Overview

A large enterprise wants to reduce the time employees spend searching
for HR-related information (policies, benefits, leave guidelines, etc.)
spread across SharePoint, PDFs, internal wikis, and documents.

To overcome this issue, in this lab, you will build a **Knowledge
assistant** **agent** in **Copilot Studio** that uses **Azure AI
Search**, to index and semantically search across enterprise HR
documents.

## Lab Objective

- Exercise 1: Create an Azure AI Search resource
- Exercise 2: Create a Storage account
- Exercise 3: Create an Azure OpenAI Service and deploy a model
- Exercise 4: Create a vector index
- Exercise 5: Create a knowledge assistant agent
- Exercise 6: Add the Azure AI Search as a knowledge source

## Exercise 1: Create an Azure AI Search resource

In this exercise, you will create an Azure AI Search resource from the
Azure portal. This will be used to search the documents using AI
capability.

**Azure AI Search** is a cloud-based service for searching within your
privately curated data. It uses a combination of Microsoft’s AI and
JSON-based indexes to provide fast, relevant search results.

1. In the Azure portal, go to the **top search bar**, enter **Microsoft Foundry (1)**, and from the results, choose **Microsoft Foundry (2)** under the **Services**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc1-0.png)

1. In the **Microsoft Foundry** page, expand **Use with Foundry (1)**, select **AI Search (2)**, and then click **+ Create (3)** to begin creating a new AI Search resource.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc1-1.png)

1. On the **Create a search service** page under the **Basics** tab, provide the following details:

     - Select the **Resource group** as **AgenticAI (1)** from the dropdown.
     - Enter **Service name**  as **searchleaves-<inject key="DeploymentID" enableCopy="false"/> (2)**.
     - Choose the appropriate **Location (3)** based on your region or lab requirement.
     - Verify that the **Pricing tier (4)** is set to **Standard** (default selection).
     - Click on **Review + create (5)** to validate the configuration and proceed with deployment.

       ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc1-2.png) 

1. On the **Review + create** tab, verify all the configured settings and then click **Create** to deploy the AI Search service.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc1-3.png) 

1. Once the deployment is complete, click on **Go to resource** to navigate to the newly created AI Search service.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc1-4.png) 

1. On the AI Search service **Overview** page, locate the **URL** under the **Essentials** section and click the **copy icon** next to it to copy the service endpoint in a notepad for later use.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/uc1-5.png) 

1. In the AI Search service, navigate to **Security + networking**, select **Keys (1)**, and under **Manage admin keys**, click the **copy icon (2)** next to the **Primary admin key** to copy it in a notepad for later use.

    ![A](./media/f1.png) 

1. Under the same drop-down, select **Identity (1)**, switch the **Status** to **On (2)** to enable the system-assigned managed identity, and then click **Save (3)** to apply the changes. 

    ![A](./media/f14.png) 

1. In the confirmation dialog to enable the system-assigned managed identity, click **Yes** to proceed and register the identity with Microsoft Entra ID.

    ![image](./media/uc1-8.png)

## Exercise 2: Create a Storage account

1. In the Azure portal , enter **Storage accounts (1)** in the **top search bar**, and from the results, choose **Storage accounts (2)** under the **Services**.

    ![image](./media/uc1-9.png)

1. On the **Storage accounts** page, click **+ Create** to begin creating a new storage account.

    ![image](./media/uc1-10.png)

1. On the **Create a storage account** page under the **Basics** tab, configure the required settings as follows:

    - Select **Resource group**: **AgenticAI (1)**
    - Enter **Storage account name** as **leavepolicystg <inject key="DeploymentID" enableCopy="false"/> (2)**
    - Choose **Region (3)**
    - Set **Preferred storage type**: **Azure Blob Storage or Azure Data Lake Storage (4)**
    - Keep **Performance**: **Standard (5)**
    - Set **Redundancy**: **LRS (6)**
    - Click **Review + create (7)**

         ![image](./media/f15.png)

1. On the **Review + create** tab, verify all the configured storage account settings and click **Create** to deploy the storage account.

    ![image](./media/uc1-12.png)

1. Once the deployment is complete, click **Go to resource** to open the newly created storage account.

    ![image](./media/uc1-13.png)

1. In the storage account, navigate to **Data storage (1)** from the left navigation pane, select **Containers (2)**, and then click **+ Add container (3)** to create a new container.

    ![image](./media/uc1-14.png)

1. In the **New container** pane, enter **document (1)** as the **Name**, keep the access level as **Private**, and click **Create (2)** to create the container.

    ![image](./media/uc1-15.png)

1. After the container is created, locate and select the **document** container from the list to open it.

    ![image](./media/uc1-16.png)

1. In the **document** container, click **Upload (1)**, then in the upload pane select **Browse for files (2)**, navigate to **C:\LabFiles\lab file**, select the **LeavePolicy.docx**  and then click on **Upload**..

    ![image](./media/uc1-17.png)

1. Navigate back to the storage account, select **Access Control (IAM) (1)** from the left navigation pane, click **+ Add (2)**, and select **Add role assignment (3)** to begin assigning permissions.

    ![image](./media/uc1-18.png)

1. In the **Add role assignment** pane, search for **Storage Blob Data Reader (1)**, select the **role (2)** from the list, and click **Next (3)** to proceed.

    ![image](./media/uc1-19.png)

1. In the **Members** tab, keep **Assign access to** as **User, group, or service principal (1)**, click **Select members (2)**, **search for **<inject key="AzureAdUserEmail"></inject>** (3)** and **choose (4)** the ODL user , and click **Select (5)**.

    ![image](./media/uc1-20.png)

1. On the same page, in the **Members** tab, select **Managed identity (1)**, click **Select members(2)**, choose **Search service (Foundry IQ) (3)** from the managed identity dropdown, select your **AI Search service instance (4)**, and click on **Select (4)**.

    ![image](./media/f16.png)

1. In the **Add role assignment** pane, verify that both the required user and the **Search service managed identity** are listed under **Members (1)**, then click **Review + assign (2)** twice to complete the role assignment.

    ![image](./media/uc1-24.png)

In this exercise, we have created a Storage account and added the
document and required Role permissions to it.

## Exercise 3: Create an Azure OpenAI Service and deploy a model

1. In the Azure portal search bar, type **Azure OpenAI (1)**, then select **Azure OpenAI (2)** from the **Services** list to open it.

    ![image](./media/uc1-25.png)

1. In the **Azure OpenAI** page, click **+ Create (1)** and then select **Azure OpenAI (2)** from the dropdown to begin creating a new resource.

    ![image](./media/uc1-26.png)

1. In the **Create Azure OpenAI** page, select **Resource group** as **AgenticAI (1)**, choose the **Region (2)**, enter **Name** as **openaiservice-<inject key="DeploymentID" enableCopy="false"/> (3)**, keep the **Pricing tier** as **Standard S0 (4)**, and click **Next (5)** option **thrice** to proceed.

    ![image](./media/uc1-27.png)

1. On the **Review + submit** tab, verify all the configured details and click **Create** to deploy the Azure OpenAI resource.

    ![image](./media/uc1-28.png)

1. Once the deployment is complete, click **Go to resource** to open the Azure OpenAI resource.

    ![image](./media/uc1-29.png)

1. In the Azure OpenAI resource, navigate to **Access control (IAM) (1)**, click **+ Add (2)**, and select **Add role assignment (3)** to assign permissions.

    ![image](./media/uc1-30.png)

1. In the **Add role assignment** pane, search for **Cognitive Services OpenAI User (1)**, select the role from the **list (2)**, and click **Next (3)** to continue.

    ![image](./media/uc1-31.png)

1. In the **Members** tab, keep **Assign access to** as **User, group, or service principal (1)**, click **Select members (2)**, **search **<inject key="AzureAdUserEmail"></inject>** (3)** and **choose (4)** the ODL user , then click **Select (5)** and proceed.

    ![image](./media/uc1-32.png)

1. In the **Members** tab, select **Managed identity (1)**, click **Select members (2)**, choose **Search service (3)** from the managed identity dropdown, select your **AI Search service instance (4)**, and proceed.

    ![image](./media/f17.png)

1. In the **Add role assignment** pane, verify that both the required user and the **Search service managed identity** are listed under **Members (1)**, then click **Review + assign (2)** twice to complete the role assignment.

    ![image](./media/uc1-35.png)

1. Navigate to the **Overview** page, click **Go to Foundry portal** to open the service in Microsoft Foundry.

    ![image](./media/uc1-36.png)

1. On the Create a project pop-up, keep all the details default and click on **Create**.

    ![A](./media/f3.png) 

1. On the **Your project is set up. What would you like to do next?** pop-up, click on **Skip**.

    ![A](./media/f4.png) 

1. Click on **Discover** from the top menu.

    ![A](./media/f5.png) 

1. Select **Models (1)** from the left navigation pane, search for **text-embedding-3-large (2)**, select the model from the **list (3)**.

    ![A](./media/f6.png) 

1. Click on the **Deploy (1)** dropdown button and select **Custom settings (2)**.

    ![A](./media/f7.png) 

1. In the **Deploy text-embedding-3-large** pane, keep the **Deployment type** as **Standard (1)** and click **Deploy (2)**.      

    ![A](./media/f8.png) 

### Congratulations!

You’ve completed the task. Now let’s validate it:
     - Hit the **Validate** button for the corresponding task.
     - If successful, proceed to the next task.
     - If not, retry using the lab guide.
     - Need help? cloudlabs-support@spektrasystems.com\
     
   <validation step="84aae3c9-71f4-401e-a136-f446d2da1749" />

## Exercise 4: Create a vector index

1. Navigate back to the Azure portal, search for **AI Search**, then select **AI Search** from the Services list to open it.

1. Select **searchleaves-<inject key="DeploymentID" enableCopy="false"/>** and click on **Import data** to start importing data into the search index.

    ![image](./media/uc1-40.png)

1. In the **Import data** pane, select **Azure Blob Storage** as the data source to proceed with importing data.

    ![image](./media/uc1-41.png)

1. In the **Import data** workflow, select **RAG** as the scenario to enable AI-powered search over your data.

    ![image](./media/uc1-42.png)

1. In the **Configure your Azure Blob Storage** step, select **leavepolicystg<inject key="DeploymentID" enableCopy="false"/> (1)** for the **Storage account**, choose **document (2)** for **Blob container** , and click **Next (3)** to proceed.

    ![image](./media/uc1-43.png)

1. In the **Vectorize your text** step, configure the following:

    - Set **Kind** to **Microsoft Foundry (1)**
    - Select your **Subscription (2)**
    - Choose the **Microsoft Foundry Project (3)**
    - Set **Model deployment** to **text-embedding-3-large (4)**
    - Select **System assigned identity (5)** for authentication
    - Select the **"I acknowledge..."** checkbox
    - Click **Next (6)** to proceed

         ![image](./media/f9.png)

1. In the **Vectorize and enrich your images** step, leave the default options unchanged (no selection) and click **Next** to proceed.

    ![image](./media/uc1-45.png)

1. In the **Advanced ranking and relevancy** step, leave the default options unchanged (no selection) and click **Next** to proceed.

    ![image](./media/uc1-46.png)

1. In the **Review and create** step, verify the configuration details and click **Create** to complete the RAG setup.

    ![image](./media/uc1-47.png)

1. Once the setup is complete, click **Close** to view and test your indexed data.

    ![image](./media/uc1-48.png)       

   ### Congratulations!

   You’ve completed the task. Now let’s validate it:
     
   - Hit the **Validate** button for the corresponding task.
   - If successful, proceed to the next task.
   - If not, retry using the lab guide.
   - Need help? cloudlabs-support@spektrasystems.com
   <validation step="77d3c91e-95a7-41d5-a2dc-5ee605b4ef21" />

## Exercise 5: Create a knowledge assistant agent

1. In a new tab, navigate to the following URL to open **Microsoft Copilot Studio** using your login credentials.

    ```
    https://copilotstudio.microsoft.com
    ```

1. Select **Get Started** in the Welcome to Microsoft Copilot Studio.

    ![image](./media/image58.png)

1. Enter the following agent description prompt in the prompt box to define your agent’s purpose and click Send.

    ```
    You are a Knowledge assistant agent for HR who will answer questions related to leaves and leave policies to the employees.
    ```

      ![A screenshot of a computer AI-generated content may be incorrect.](./media/cs2.png)

1. Click on **Test (1)** from the top-right corner, then enter following **prompt (2)** and click send to validate your agent’s response.

    ```
    How many days of Maternity leaves can I avail?
    ```

      ![image](./media/cs4.png)

1. It gives a generalized response as shown in the screenshot below.

    ![image](./media/cs5.png)

## Exercise 6: Add the Azure AI Search as a knowledge source

1. Click on **Overview** from the top and select **Add knowledge**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/cs1.png)

1. Select Azure AI Search from the list of knowledge sources available.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image64.png)

1. Click on the **drop down** next to **Not connected** in the next screen and select **Create new connection**.

    ![A screenshot of a search engine AI-generated content may be incorrect.](./media/image65.png)

1. Enter the **Endpoint url** and the **Admin key** values which we saved to a notepad in the first exercise and then click on **Create** to create the connection.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image66.png)

1. Once the connection is established, the available index is listed and already selected. Click on **Add to agent**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image67.png)

1. The AI Search service is added as a knowledge source to the agent and is in **Ready (1)** state now. Ensure that the **Web search** option is **disabled (2)** in the Knowledge section.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/cs3.png)

1. Now, let us test the agent with the same question we tried before.

1. In the Test window, click on the **"+ (1)"** icon and select **Start new test session (2)**.

    ![image](./media/f18.png)

1. Enter the following query and review the generated response to verify the agent’s accuracy.

    ```
    How many days of Maternity leaves can I avail?
    ```

1. You can see that the response from the agent now is from the document uploaded in the AI Search service.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/uc1-51.png)

## Important

   > **Note**: Please delete the resources that you have created in the **AgenticAI** resource group. 

   ![](./media/f13.png) 

  > **Note:**
  >
  > After deleting the resources:
  >
  > - Navigate to **Azure OpenAI** and select **openaiservice-<inject key="DeploymentID" enableCopy="false"/>**.
  >   - From the top menu, click **Manage deleted resources**.
  >   - Select the checkbox next to **openaiservice-<inject key="DeploymentID" enableCopy="false"/> (1)** and click on **Purge (2)**.    

![](./media/f19.png)

  >   - Confirm the action in the pop-up dialog.
  >   - Verify that the resource has been permanently deleted.

## Summary

In this lab, we have learnt to connect the agent to a Azure AI Search
service as a knowledge source and test the agent based on the source.

