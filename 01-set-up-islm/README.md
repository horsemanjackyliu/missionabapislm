# Generative AI for ISLM

Following is the architectural representation of ISLM integration with ABAP AI SDK.

![alt text](./img/image.png)

> **Notes: If you use SAP internal BTP ABAP environment, please skip this excercise**.

## Prerequisites:

- You have finished then pre workshop set up for SAP AI Core and SAP AI Launchpad
- You are the BTP Sub Account Administrator
- You have been assigned role `SAP_BR_ADMINISTRATOR` in SAP BTP ABAP Environment.

## Procedure

### Download Certificate in BTP ABAP Environment.

1. Log on to the SAP BTP ABAP Environment.
2. Enter user credentials for administrator.
3. Choose **Maintain Client Certificates**.

   > You can also search for **Maintain Client Certificates** and select it.
   > ![alt text](./img/image-3.png)

4. On the Maintain Client Certificates screen, search for Client Default.
   ![alt text](./img/image-4.png)

5. Choose the Client Default from the certificates list.
6. Choose **Export** to export the file to your local file folder.

   ![alt text](./img/image-5.png)

7. Choose the **Base-64-encoded X.509 certificate (.crt)** format to save the certificate.
8. Choose **Export**.
9. Open the downloaded crt file with text editor .

   ![alt text](./img/image-6.png)

## Create Service Key for SAP AI Core Service Instance.

1. Get into your BTP Sub Account and create service key as the following.

   ![alt text](./img/image-7.png)

   ![alt text](./img/image-8.png)

   - Service Key Name: `abapkey`
   - JSON file as the following

   ```
   {
   "xsuaa": {
    "credential-type": "x509",
    "x509": {
      "certificate": "<Client-Default-Certificate from crt file>",
      "ensure-uniqueness": false,
      "certificate-pinning": true,
      "hide-certificate": true
    }
   }
   }

   ```

Click on **Create**

![alt text](./img/image-9.png)

![alt text](image.png)

## Configure the Communication System for SAP_COM_0A69

> Currently, you can create one instance of the communication scenario per client.

1.  Log on to the SAP BTP ABAP Environment.
2.  Navigate to **Communication Management**.
3.  Choose **Communication Systems** tile.

    ![alt text](./img/image-10.png)

4.  Choose **New**.

    Enter System ID and System Name.

    ![alt text](./img/image-11.png)

    - System Name : `AICORE`
    - System ID : `AICORE`

5.  Choose **Create**.

6.  Navigate to the **Technical Data** tab.

    Update the **Technical Data** details as per the **service key** details.

7.  In the **General section**, for **Host Name**, use the **AI_API_URL** value without protocol.

    ![alt text](./img/image-12.png)

8.  In the Outbound OAuth 2.0 Client Settings, enter the following details:

9.  For **Authorization Endpoint** use the **url** value without protocol.

    For **Token Endpoint**, use the **url** value without protocol and add the path: `/oauth/token`.

    Add the `/oauth/token` string to the **URL** value.

    For **mTLS Endpoint**, use the **certurl** value without protocol and add the path: `/oauth/token`.

    ![alt text](./img/image-13.png)

10. On the Users for **Outbound Communication** tab, choose the **Add** button.

11. Create an authentication method, enter the following details:
    ![alt text](./img/image-14.png)

    - **Authentication Method** - Select `OAuth 2.0`

    - **OAuth 2.0 Client ID** - Use the **clientid** value from the service key.

    - **Client Authentication** - Select `mTLS`

    - For **Client Certificate**, select `Client Default` from the value help.

12. Choose **Create**.

13. Choose **Save**.

## Create the Communication Arrangement for SAP_COM_0A69

1.  Log on to the SAP BTP ABAP Environment.

2.  Navigate to **Communication Management**.

3.  Choose **Communication Arrangements** tile.

    ![alt text](./img/image-15.png)

4.  Choose **New**.

    ![alt text](./img/image-16.png)

5.  In the Scenario field, select the predefined communication scenario **SAP_COM_0A69**.

6.  Enter Arrangement Name `SAP_COM_0A69`.

7.  Choose **Create**.

8.  Navigate to the **Outbound Communication** area.

    ![alt text](./img/image-17.png)

9.  In the **Communication System** field, enter the communication system that you created. See, [Configure the Communication System for SAP_COM_0A69](#configure-the-communication-system-for-sap_com_0a69)

10. Choose **Save**.

## Create an intelligent scenario in Eclipse ADT.

### Prerequisites

- You already have the role `SAP_BR_DEVELOPER` assigned in SAP BTP ABAP Environment.

- You already have the role `SAP_BR_ANALYTICS_SPECIALIST` assigned in SAP BTP ABAP Environment.

### Procedure

1. Right click packange [](./img/adt_package.png) 'ZRAP*ISLM*###', Select **New**> **Other ABAP Repsitory Object**

   ![alt text](./img/image-18.png)

2. On Select a wizard, search for `intelligent scenario` and navigate to **Intelligent Scenario Lifecycle Management** > **Intelligent Scenario**.

   ![alt text](./img/image-19.png)

3. In the Intelligent Scenario wizard, enter the following details:

   - The Project field is auto-populated.

   - Package: Select the package from the value help.

   - Add to favorite packages: Optionally, select this option to add this package to your favorites list.

   - Name: `ZRAP_ISLM_IS_###`

   - Description: `Intelligent Scenario ###`.

   - Scenario Technology: Select `SIDEBYSIDE` from the value help.

     ![alt text](./img/image-20.png)

4. Choose **Next**.

   ![alt text](./img/image-21.png)

5. Choose **Finish**.

6. The new intelligent scenario is created and opened in the Intelligent Scenario editor.

   ![alt text](./img/image-22.png)

   - Select `SAPGENAI` in **Intelligent Scenario Type** field.

   - Select `CUSTOMER` in **Usage Type** field.

     ![alt text](./img/image-23.png)

7. Click on **Save** and **Activate** to save and activate the intelligent scenario.

## Creating Intelligent Scenario Models

1.  Right click **Intelligent Scenario Lifecycle Management**,Open the context menu and select **New** > **Intelligent Scenario**.

    ![alt text](./img/image-24.png)

2.  Choose **Next**.

3.  In the Intelligent Scenario Model wizard, enter the following details:

    ![alt text](./img/image-25.png)

    - The Project field is auto-populated.

    - Package: Select the package from the value help.

    - Add to favorite packages: Optionally, select this option to add this package to your favorite list.

    - Description: `Intelligent Scenario Model 000`.

    - Intelligent Scenario Name: `ZRAP_ISLM_IS_###`.

    - Model Name: `ZRAP_ISLM_ISM_###`.

    > Note:

        The object name of the intelligent scenario model is auto generated based on the Intelligent Scenario Name and Model Name.

4.  Choose Next.

    ![alt text](./img/image-26.png)

5.  Click on **Finish**.

    The new intelligent scenario model is created and opened in the Intelligent Scenario Model editor.

6.  Provide:

    - Executable ID: select `azure-openai`

    - Large Language Model Name: select 'gpt-4o-mini'

    - Large Language Model Version: select the newest version.

      ![alt text](./img/image-27.png)

7.  Click on **Save** and **Activate**.

## Manage Gen AI Scenarios

### Procedure:

1. Log on to the SAP BTP ABAP Environment.

2. Enter user credentials for administrator.

3. Open the **Intelligent Scenario Management** app

   ![alt text](./img/image-28.png)

4. Click the intelligent scenario that you want to work with.

   ![alt text](./img/image-29.png)

5. Select **intelligent scenario model** `ZRAP_ISLM_ISM_###`

   ![alt text](./img/image-30.png)

   ![alt text](./img/image-31.png)

6. Click on **Deploy**

   ![alt text](./img/image-32.png)

7. Click on **Deploy and Monitor**

   ![alt text](./img/image-33.png)

8. After 5 minutes, check again and Activate the deployment

   ![alt text](./img/image-34.png)

   ![alt text](./img/image-36.png)

   ![alt text](./img/image-37.png)

9. Check in **SAP AI Launchpad** for the Deployment.

   ![alt text](./img/image-35.png)
