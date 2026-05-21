## Set Up SAP AI Launchpad

1. Navigate to your global account and choose the **Boosters** tile.

   Choose **Set Up Account for SAP AI Launchpad** booster

   ![](img/08.png)

2. Choose **Start**.

   Make sure that **_All required prerequisites are met_** and choose **Next**.

   ![](img/09.png)

3. Choose **Select Subaccount** mode for the booster and choose **Next**.

   ![](img/10.png)

4. Configure your Cloud Foundry Subaccount and Space with the following:

   - Subaccount: **Building Custom AI Solutions**
   - Org: **building-custom-ai-solutions**
   - Space: **dev**

   Choose **Next**.

   ![](img/11.png)

5. Choose **Finish**.
6. Navigate to your subaccount -> **Instances and Subscriptions** tab and validate that you can access SAP AI Launchpad by opening it in incognito window.

   ![](img/23.png)

   Log in with your IAS user. You should see the **SAP AI Launchpad** homepage with no AI API connections (for now). Don't close this tab.

   ![](img/24.png)

   > [!TIP] If a _Forbidden_ error apprears, make sure you're logging on as a user with the following role collections assigned:
   >
   > - **ailaunchpad_aicore_admin_editor**
   > - **ailaunchpad_allow_all_resourcegroups**
   > - **ailaunchpad_connections_editor**
   > - **ailaunchpad_functions_explorer_editor**
   > - **ailaunchpad_mloperations_editor**
   >
   > ![](img/25.png)

## Set Up SAP AI Core

1. Navigate to your global account and choose the **Boosters** tile.

   Choose the **Set Up Account for SAP AI Core** booster

   ![](img/16.png)

2. Choose **Start**.

   Make sure that **_All required prerequisites are met_** and choose **Next**.

   ![](img/17.png)

3. Choose **Select Subaccount** mode for the booster and choose **Next**.

   ![](img/18.png)

4. Configure your Cloud Foundry Subaccount and Space with the following:

   - Plan: **extended**
   - Subaccount: **Building Custom AI Solutions**
   - Org: **building-custom-ai-solutions**
   - Space: **dev**

   ![](img/19.png)

   Please select the subaccount and dev space in which you deploy your **Freight Order Attach Management** application.

   Choose **Next**.

5. Choose **Finish**.
6. Navigate to your subaccount -> **Instances and Subscriptions** tab and filter the list with `SAP AI Core` to show the SAP AI Core service instance.

   Notice that the **Credentials key** has already been created by the booster. Open it.

   ![](img/26.png)

   Choose **Download**.

   ![](img/27.png)

7. Navigate back to the **SAP AI Launchpad** homepage and choose **Add** button to add the connection.

   ![](img/28.png)

   Click **Upload icon** to upload service key you've downloaded on the previous step. Notice that the values are populated automatically.

   Specify the **Connection Name** as `default` and choose **Create**.

   ![](img/29.png)

   Notice that the workspace is set automatically (this may take some time).

   > [!TIP] This includes a default resource group that has been automatically created under **Resource Groups**
   > A resource group is used to connect with all computing resources needed for an AI workflow. It also isolates your own workflow vs other users' workflows. You can create more resource groups if needed.

   ![](img/30.png)

## Deploy Orchestration Service

1. Choose **Generative AI Hub** -> **Orchestration**.

   ![no orch yet](img/orch-01-no-orchestration.png)

2. Choose **ML Operations** -> **Configurations** and choose **Create**.

   ![config orchestration start](img/orch-02-create-config-start.png)

3. Enter Name and Executable

   - Configuration Name: **my-first-orchestration**
   - Scenario: **orchestration**
   - Version: **0.0.1**
   - Executable: **orchestration**

   ![enter name](img/orch-03-enter-name.png)

   Choose **Next** to continue.

4. Choose **Next** to continue.

   ![enter parameter](img/orch-04-next.png)

5. Choose **Review** to continue.

   ![review configuration](img/orch-05-review.png)

6. Review the properties of your orchestraion and choose **Create**.

   ![create configuration](img/orch-06-create-button.png)

7. Choose **Create Deployment**.

   ![create deployment start](img/orch-07-create-deploy-start.png)

8. Choose **Review** to continue.

   ![select duration](img/orch-08-deploy-review.png)

9. Review all properties of this deployment and choose **Create**.

   ![select review](img/orch-09-create-deploy-button.png)

   **Now the deployment has started.** Monitor the status changes here.
   On the deployment screen, you can see the Target Status is **RUNNING** and in the beginning, the Current Status is **UNKNOWN**. Also, the deployment URL shows _URL isn't available_ until the orchestration is deployed.

   > [!Note] The deployment could take a few minutes depending on the server's status, network, the number of parallel jobs, etc. You can refresh the status by clicking the refresh icon on the top right of the screen.
   > ![refresh deployment](img/orch-10-refresh-deploy.png)

10. Finally, you will see the orchestration is deployed.

    ![deployment running](img/orch-12-deploy-running.png)

### Deploy Large Language Models (LLM)

<!--
1. Expand ML Operations menu on the left and choose **Configurations**.

    You need to create a configuration of a specific model. Choose the **Create**.

    ![create button](img/create-config-button.png)

    Let's first create a configuration for the **text embedding** model.

2. Provide the following information and choose **Next**

   - Configuration Name: **openai-embedding-config**
   - Scenario: **foundation-models**
   - Version: **0.0.1**
   - Executable: **azure-openai**

   ![create config 1](img/emb-01.png)

3. Provide the following information and choose **Next**

   - modelName: **text-embedding-ada-002**
   - modelVersion: **latest**
   > [!TIP] Ensure that the model name matches exactly as specified. Optionally, you may include a version number as outlined in the [SAP Note](https://me.sap.com/notes/3437766). For this exercise, the `latest` version is used.

   ![create config 2](img/emb-02.png)

4. Choose **Review**

5. Review the properties of your model and choose **Create**.

    ![create config 4](img/emb-03.png)

6. Choose **Create Deployment**.

    ![create deployment 1](img/emb-04.png)

7. Choose the duration as **Standard** and choose **Review**.

    ![create deployment 2](img/emb-04-2.png)

8. Review the details and choose **Create**.

    ![create deployment 3](img/emb-05.png)

    **Now the deployment has started.** Monitor the status changes here.

    On the deployment screen, you can see the Target Status is **RUNNING** and in the beginning, the Current Status is **UNKNOWN**.  Also, the deployment URL says *URL isn't available* until the model is deployed.

    > [!TIP] The deployment process usually takes between 2 to 10 minutes, depending on the server's status, network, the number of parallel jobs, etc.  You can refresh the status by clicking the refresh icon on the top right of the screen. In the meantime, you can proceed with the following steps.

    ![create deployment 4](img/emb-06.png) -->

<!-- 9. While you are waiting for your first model to be deployed, repeat the steps above to deploy a **gpt-4o** model.

    Follow the configuration process. When it comes to "Enter Name and Executable", provide the following:

    - Configuration Name: **openai-gpt-4o-config**
    - Scenario: *`foundation-models**
    - Version: **0.0.1**
    - Executable: **azure-openai**

    ![create config4 1](img/gpt4-c1.png)

    When it comes to "Input Parameters", please fill in the following:

    - modelName: **gpt-4o**
    - modelVersion: **latest**
    > [!TIP] Ensure that you enter the model name exactly as specified. Optionally, you can include a version number as outlined in the [SAP Note](https://me.sap.com/notes/3437766). For this exercise, the `latest` version is used.

    ![create config4 2](img/gpt4-c2.png)

    Proceed with creating configuration and deploying the model.


10. While you are waiting for your first two models to be deployed, repeat the steps above to deploy a **claude-3.7** model.

    Again, follow the configuration process. When it comes to "Enter Name and Executable", please fill in the followings:

    - Configuration Name: **anthropic-claude-3.7-sonnet-config**
    - Scenario: **foundation-models**
    - Version: **0.0.1**
    - Executable: **aws-bedrock**

    ![create config claude 1](img/dp-1-claude35.png)

    When it comes to "Input Parameters", please fill in the following:

    - modelName: **anthropic--claude-3.7-sonnet**
    - modelVersion: **latest**
    > [!TIP] Ensure that you enter the model name exactly as specified. Optionally, you can include a version number as outlined in the [SAP Note](https://me.sap.com/notes/3437766). For this exercise, the `latest` version is used.

    ![create config claude 2](img/dp-2-claude35.png)

    Proceed with creating configuration and deploying the model.

After some time you should see all models deployed and running.

![models deployed](img/dp-4-all-models.png) -->

1. Expand ML Operations menu on the left and choose **Configurations**.

   You need to create a configuration of a specific model. Choose the **Create**.

   ![create button](img/create-config-button.png)

   Let's first create a configuration for the **text embedding** model.

2. Provide the following information and choose **Next**

   - Configuration Name: **openai-gpt-4o-mini-config**
   - Scenario: \*`foundation-models\*\*
   - Version: **0.0.1**
   - Executable: **azure-openai**

   ![create config4 1](img/gpt4mini-c1.png)

   <!-- ![create config4 1](img/gpt4-c1.png) -->

3. Provide the following information and choose **Next**

   - modelName: **gpt-4o-mini**
   - modelVersion: **latest**
     > [!TIP] Ensure that you enter the model name exactly as specified. Optionally, you can include a version number as outlined in the [SAP Note](https://me.sap.com/notes/3437766). For this exercise, the `latest` version is used.
     > ![create config 2](img/gptmini-2.png)

4. Choose **Review**

5. Review the properties of your model and choose **Create**.

   ![create config 4](img/gptmini-3.png)

6. Choose **Create Deployment**.

   ![create deployment 1](img/gptmini-4.png)

7. Choose the duration as **Standard** and choose **Review**.

   ![create deployment 2](img/emb-04-2.png)

8. Review the details and choose **Create**.

![alt text](image.png)

![create deployment 3](img/gptmini-5.png)

**Now the deployment has started.** Monitor the status changes here.

On the deployment screen, you can see the Target Status is **RUNNING** and in the beginning, the Current Status is **UNKNOWN**. Also, the deployment URL says _URL isn't available_ until the model is deployed.

> [!TIP] The deployment process usually takes between 2 to 10 minutes, depending on the server's status, network, the number of parallel jobs, etc. You can refresh the status by clicking the refresh icon on the top right of the screen. In the meantime, you can proceed with the following steps.

![create deployment 4](img/gptmini-6.png)

> [!TIP] Congratulations! You have successfully deployed the chat completion model **gpt-4o-mini** model on SAP AI Core.
