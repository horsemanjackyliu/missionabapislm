# Deploy Fiori Application to BTP ABAP Environment

## Prerequisites

- Active Node.js LTS version and its associated npm version — see [nodejs.org](https://nodejs.org)

## Step 1: Download the Application

Clone the Fiori application repository:

```bash
git clone https://github.com/horsemanjackyliu/islmwsfiori.git
cd islmwsfiori
```

## Step 2: Configure Your BTP ABAP Environment

Update the BTP ABAP instance URL in the following files, replacing the placeholder with your actual instance URL in the format `https://<instance-id>.abap.<datacenter>.hana.ondemand.com`:

- `ui5-deploy.yaml`
- `ui5-local.yaml`
- `ui5-mock.yaml`
- `ui5.yaml`

## Step 3: Build and Deploy

```bash
npm install
npm run build
npm run deploy
```

After a successful deployment, the application will appear in your ADT (ABAP Development Tools).

![Deployed application in ADT](img/image.png)

## Step 4: Create an IAM Application in ADT

In Eclipse, right-click your package `ZISLM_WS###` and select **New > Other Repository Object**.

![New repository object menu](img/image-1.png)

Search for **IAM App**, select it, and click **Next >**.

![Search for IAM App](img/image-2.png)

Enter the following details and click **Next >**, then **Finish**:

| Field       | Value                           |
| ----------- | ------------------------------- |
| Name        | `ZISLM_IAM_###`                 |
| Description | `IAM App for outbound delivery` |

![Create IAM App](img/image-3.png)

![IAM App created](img/image-4.png)

![IAM App overview](img/image-5.png)

## Step 5: Create a Business Catalog in ADT

![New business catalog](img/image-6.png)

![Business catalog wizard](img/image-7.png)

Enter the following details and click **Next >**, then **Finish**:

| Field       | Value                                    |
| ----------- | ---------------------------------------- |
| Name        | `ZISLM_BC_###`                           |
| Description | `Business Catalog for outbound delivery` |

## Step 6: Create a Business Role in BTP ABAP Environment

Navigate to your BTP ABAP environment and create a new business role.

![Business role list](img/image-8.png)

![New business role](img/image-9.png)

![Business role wizard step 1](img/image-10.png)

![Business role wizard step 2](img/image-11.png)

![Business role wizard step 3](img/image-12.png)

Enter the following details:

| Field                     | Value               |
| ------------------------- | ------------------- |
| Business Role ID          | `ZISLM_ROLE_001`    |
| Business Role Description | `Role for ISLM 001` |

![Business role details](img/image-13.png)

![Business role created](img/image-15.png)

## Step 7: Create a Launchpad Space in BTP ABAP Environment

Navigate to the Launchpad section in your BTP ABAP environment.

![Launchpad navigation](img/image-16.png)

![New launchpad space](img/image-17.png)

![Launchpad space configuration](img/image-19.png)

Enter the following details:

| Field             | Value             |
| ----------------- | ----------------- |
| Space ID          | `ZISLM_SPACE_###` |
| Space Title       | `ISLM SPACE ###`  |
| Space Description | `ISLM SPACE ###`  |
| Page ID           | `ISLM_PAGE_###`   |
| Page Title        | `ISLM PAGE ###`   |
| Page Description  | `ISLM PAGE ###`   |

![Launchpad space created](img/image-20.png)

## Step 8: Update the Business Role

Assign the newly created Business Catalog to your Business Role.

![Update business role](img/image-21.png)

## Step 9: Update the Launchpad Page

Add the application tile to your Launchpad Page.

![Launchpad page editor](img/image-22.png)

![Add app tile](img/image-23.png)

![Tile added](img/image-24.png)

## Step 10: Test the Application

Open the Launchpad in your BTP ABAP environment and verify the application launches correctly.

![Launchpad with app tile](img/image-25.png)

![Application running](img/image-26.png)
