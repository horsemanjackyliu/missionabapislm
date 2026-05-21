## Using a Booster to Automate the Setup of the ABAP Environment

You can use a booster to automate some of the required steps for setting up the ABAP environment. Automation includes creating a subaccount and space, configuring the required entitlements, and assigning administrators and developers to the subaccount.

### Procedure

- 1. Log on to the SAP BTP cockpit and choose the global account for the Cloud Foundry environment as administrator.

- 2. From the navigation menu, choose Boosters.
     ![alt text](./img/image.png)

- 3. Choose the booster Prepare an Account for ABAP Development.
     > The tab pages Overview, Components, and Additional Resources are displayed, where you get more information about the booster.
     > ![alt text](./img/image-1.png)

- 4. Choose Start.

  ![alt text](./img/image-2.png)

- 5. After the booster wizard has successfully checked the prerequisites, choose Next to continue.
     ![alt text](./img/image-3.png)

- 6. On the Select Scenario dialog, choose whether you'd like the booster to create your ABAP environment service instance in a new, or in an existing subaccount.

  ![alt text](./img/image-4.png)

- 7. Depending on what you have ordered for your account, additional entitlements for the services Cloud Foundry Runtime, SAP Build Work Zone, standard edition, and SAP Business Application Studio might be shown. They are optional; you can remove the entitlements if you don't need them right now and want to add them later:
     > A quota for the Cloud Foundry runtime is only needed for the ABAP environment if your developers want to deploy their own apps in Cloud Foundry.
     > The SAP Build Work Zone, standard edition enables organizations to establish a central point of access to SAP, custom-built, and third party applications and extensions, both in the cloud and on premise.
     > SAP Business Application Studio is a UI development environment.

- 8. On the Configure Subaccount dialog, follow the instructions on the screen to enter subaccount name, provider, region, and so on.

![alt text](./img/image-5.png)

- 9. On the Add Users dialog, add the e-mail addresses of new users in the ABAP environment.
     > This step allows you to quickly create additional administration users for the ABAP environment, if needed, and developer users. In the Origin field, you can see the identity provider for the ABAP environment. By default, this is SAP ID service (sap.ids), but if you have set up a custom identity provider, you can choose this provider from the dropdown list.

  ![alt text](./img/image-6.png)

- 10. On the **Configure ABAP Environment Instance** dialog, enter a 3-character ID for your ABAP system.
      ![alt text](./img/image-7.png)

- 11. Review your settings and finish the booster.

  ![alt text](./img/image-8.png)

## Assign business role BR_ANALYTICS_SPECIALIST to your use account.

- 1. Log on to the SAP BTP cockpit and choose the sub-account in which you have created the SAP BTP ABAP Environment.

  ![alt text](./img/image-14.png)

  In next screen, select the default IAS or the custom IAS to fill your email and password.

- 2. Create role from role template.

  ![alt text](./img/image-9.png)

  ![alt text](./img/image-10.png)

  ![alt text](./img/image-11.png)

  **Template:** `SAP_BR_ANALYTICS_SPECIALIST`

  **New Business Role ID:** `BR_ANALYTICS_SPECIALIST`

  **Description:** `Analytics Specialist`

  **Option for Launchpad Spaces:** `Use Space Template`

  ![alt text](./img/image-12.png)

  ![alt text](./img/image-13.png)

## Download the Eclipse IDE and add the ABAP Development Tools (ADT) Plugin

<!-- description --> Download the Eclipse IDE and add the ABAP Development Tools (ADT) Plugin.

### You will learn

- How do download the Eclipse IDE
- How to add the ADT plugin to Eclipse

### Prerequisites

- Operating System: - Windows 10, or higher - Apple macOS 10.15 or higher
- Microsoft VC++ Runtime: - For Windows: [Microsoft Visual C++ 2015-2022 Redistributable (x64)](https://learn.microsoft.com/en-US/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022)
- Java Runtime:
  - The latest Eclipse packages are bundled with [`Eclipse Temurin`](https://adoptium.net/), an `OpenJDK` binary distribution provided by the [`Eclipse Adoptium`](https://projects.eclipse.org/projects/adoptium) project. Any other JRE found on the system is not used. If you want to remove the bundled JRE and use a custom one, see SAP note [3035242](https://launchpad.support.sap.com/#/notes/3035242).
    > **Hint:** You do not need to manually install a JRE / JDK, since it is already bundled with the latest Eclipse packages, which are downloadable as a ready-to-run zip file.

---

#### Download and run Eclipse IDE

1. Open the [Eclipse download page](https://www.eclipse.org/downloads/packages/) to download the appropriate (usually latest) Eclipse version.

   ![eclipse](./img/eclipse.png)

2. Click **Download**.

   ![eclipse](./img/eclipse2.png)

3. Click the **Download** icon of your browser and select the folder symbol.

   ![eclipse](./img/download0.png)

4. Extract the Eclipse file with right-click.

   ![eclipse](./img/download1.png)

5. Click **Extract** in the wizard.

   ![eclipse](./img/download2.png)

6. Open the **Eclipse-Java** folder.

   ![eclipse](./img/download3.png)

7. Open the **Eclipse** folder.

   ![eclipse](./img/eclipse6.png)

8. Double-click **`eclipse.exe`** to run the application.

   ![eclipse](./img/eclipse7.png)

9. Launch your workspace.

   ![eclipse](./img/eclipse8.png)

10. Close both pages.

    ![eclipse](./img/eclipse9.png)

    ![eclipse](./img/eclipse10.png)

#### Add ADT plugin to Eclipse

1.  Select **Help** > **Install New Software**.

    ![eclipse](./img/eclipse11.png)

2.  Enter the latest ADT URL **`https://tools.hana.ondemand.com/latest`** in the **Work with** section, press enter, select **ABAP Development Tools** and click **Next >**.

    ![eclipse](./img/adt.png)

3.  Click **Next >**.

    ![eclipse](./img/adt2.png)

4.  Accept the **license agreement** and click **Finish**.

    ![eclipse](./img/adt3.png)

5.  Click **Select All** and **Trust Selected**.

    ![eclipse](./img/adt4.png)

6.  Click **Restart Now**.

    ![eclipse](./img/eclipse17.png)

7.  Now ADT is installed. Switch to the ABAP perspective. Therefore select **Window** > **Perspective** > **Other Perspective** > **Other**.

    ![eclipse](./img/perspective.png)

    Then select **ABAP** and click **Open**.

    ![eclipse](./img/perspective2.png)

8.  Check your result.

    ![eclipse](./img/eclipse18.png)

## Install the abapGit Plugin

<!-- description --> Install the abapGit plugin for ADT.

### You will learn

- How to install `abapGit` plugin

### Prerequisites

- You finished the [Download the Eclipse IDE and add the ABAP Development Tools (ADT) Plugin](abap-install-adt) tutorial.

This tutorial is only required to transfer ABAP development objects between a Git repository and an SAP S/4HANA Cloud, ABAP Environment instance or an SAP BTP, ABAP Environment instance.

---

#### Install abapGit plugin

To transfer your ABAP development objects from on-premise SAP systems to an SAP BTP, ABAP Environment instance, you can use the `abapGit` plugin.

1.  Open **Eclipse** and select **Help** > **Install New Software**.

    ![plugin](./img/eclipse11.png).

2.  Enter the `abapGit` URL **`https://eclipse.abapgit.org/updatesite/`** in the **Work with** section, press enter, select **`abapGit` for ABAP Development Tools (ADT)** and click **Next >**.

    ![plugin](./img/plugin.png)

3.  Click **Next >**.

    ![plugin](./img/plugin2.png)

4.  Accept the **license agreement** and click **Finish**.

    ![plugin](./img/plugin3.png)

5.  Click **Select All** and **Trust Selected**.

    ![plugin](./img/plugin4.png)

6.  Click **Select All** and **Trust Selected**.

    ![plugin](./img/plugin5.png)

7.  Click **Restart Now**.

    ![eclipse](./img/plugin7.png)

8.  Now `abapGit` for ADT is installed.

    ![eclipse](./img/plugin8.png)

## Create a Developer User in SAP BTP ABAP Environment

<!-- description --> Create a developer user with the developer role in SAP Business Technology Platform ABAP Environment.

### Prerequisites

- You must have an administrator user.

### You will learn

- How to create an employee user
- How to assign business roles to an employee user

### Time to Complete

**# 10 Min**.

---

#### Overview

To be connected to your system in ADT, expose an ABAP service and consume this service to create a Fiori Application, you will need to have a Developer User with developer role.

![Overview](./img/Picture21.png)

#### Log in to SAP Fiori Launchpad as administrator

If you do not have already an existing ADT project, you need to find the URL to the launchpad in the BTP cockpit. For more information see the [link] (https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/11e765e8af6d476f99ce014b3f02bd64.html). Otherwise you can use the existing project to find out the launchpad link as follows:

1.  Open Eclipse and do right click on your system and navigate to **Properties**.

    ![Open Eclipse](./img/Picture17.png)

2.  Navigate to **ABAP Development** and copy the **System URL**.

    ![System URL](./img/Picture18.png)

3.  Copy this URL in a browser and change the URL like this:

    Add `-web` after `.abap` and `/ui` at the end of URL.
    `https://<your-system>.abap-web.eu10.hana.ondemand.com/ui`

    ![Change URL](./img/Picture20.png)

4.  Login with admin user and password in SAP Fiori Launchpad.

    ![Login to SAP Fiori Launchpad](./img/Picture19.png)

#### Navigate to Maintain Employees application

Navigate to **Maintain Employees** application.

![Maintain Employees](./img/Picture2.png)

#### Create a new employee

Create a new employee by clicking **New**

![Create a new employee](./img/Picture3.png)

#### Enter user data

1. Enter user data and a valid Email address .

   - Employee ID: `DEVELOPER_XXX`
   - Last Name: `DEVELOPER_XXX`
   - E-Mail: `developer_xxx@example.com`

2. **Save** your changes.

   ![Enter user data](./img/Picture4.png)

#### Create business user

1. Select the newly created entry in the employee list.

2. Press **Create Business User**.

   ![Create business user](./img/Picture5.png)

#### Add business roles

1. Press **Add** Business Roles.

   ![Add business Roles](./img/Picture6.png)

2. Select business role **Developer** and press **OK**.

   ![Add business Roles](./img/Picture7.png)

3. Save all changes with click on **Save**.

   ![save](./img/Picture8.png)
