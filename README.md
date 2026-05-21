# BTP ABAP Custom AI Application with the ABAP AI SDK powered by Intelligent Scenario Lifecycle Management,

## Overview

[^Top of page](#)

This hands-on workshop will guide you to build side-by-side extensions for an SAP S/4HANA backend system in an SAP BTP ABAP Environment system (aka _Steampunk_).

## Business Scenario

![architecture](pages/img/RAPISLMdrawio.png)

Our scenario is an outbound deliveries management application that runs on SAP BTP ABAP environment. This application will get the outbound deliveries from SAP S/4Hana Cloud by Odata API. We will use ABAP AI SDK to connect to SAP AI Core to suggest best route for Outbound Delivery documents from SAP S/4HANA Cloud.

<!-- <details>
<summary>Click to expand!</summary>

**Create a custom BO for a specific business context and integrate remote OData services**

For that, you will build a custom business object with RAP to manage inventory data. The product data is being retrieved from the SAP backend system using public remote enabled API's.

To speed up the development we will use a wizard in ADT that generates the complete stack of a RAP business object based on a single existing table. This allows us to skip writing lots of boilerplate coding that you otherwise would have to write yourself.

The product data is being retrieved from the SAP backend system using an OData service. In addition, we use a SOAP Web service to read the price of a product to showcase that remote APIs based on various protocols are supported (OData, SOAP, RFC).

You’ll enhance the generated application by enriching it with additional UI annotations, and display it in a SAP Fiori elements based List Report.
Then you’ll enable the consumption of the remote OData and SOAP services by enhancing the business object (BO) with a value help that is based on a custom entity and a determination that calls the remote SOAP Web service.

Your application will finally look like this:

![Custom business application](./img/resulting_app_000.png)

![Custom business application](./img/resulting_app_010.png)

![Custom business application](./img/resulting_app_020.png) -->
