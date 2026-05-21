## Create **Service Definition**

1. In ADT, Right click Package: `ZRAP_ISLM_###` and choose **New** > **Other ABAP Repository Object**:

![alt text](./img/image.png)

![alt text](./img/image-1.png)

![alt text](./img/image-2.png)

- Name: `ZSRV_DN_###`

- Description: `Outbound Delivery Document Service`

- Source Type: `Definition`

Click on **Next**

![alt text](./img/image-3.png)

Click on **Finish**

![alt text](./img/image-4.png)

2. Expose the entities in Service Definition.

![alt text](./img/image-5.png)

```
@EndUserText.label: 'Outbound Delivery Document Service'
define service ZSRV_DN_### {
  expose ZDN_HEADER_###;
  expose ZDN_ITEM_###;
  expose ZDN_ADDRESS_###;
}

```

> please replace the '###' with your group id .

Please click on **Save** and **Activate** button to save and activate the service definitions.

## Create **Service Binding**

1. In ADT, Right click **Service Definition**: `ZSRV_DN_###` and choose **New Service Binding**

![alt text](./img/image-7.png)

![alt text](./img/image-8.png)

- Name: `ZSRV_BINDING_###`

- Description: `Outbound Delivery Document Service Binding`

- Binding Type: `Odata V4 - UI`

- Service Definition: `ZSRV_DN_###`

Click on **Next**

![alt text](./img/image-9.png)

Click on **Finish**

![alt text](./img/image-10.png)

Click on **Activate**

![alt text](./img/image-11.png)

Click on **Publish**

## Preview **Service Binding**

In ADT, double click Service Binding `ZSRV_BINDING_###`

![alt text](./img/image-12.png)

Click on **Preview**

![alt text](./img/image-13.png)
