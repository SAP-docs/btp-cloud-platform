<!-- loio6c4feeae9fa84269aed1140d1b2725d3 -->

# Using Client Certificate Authentication with SAP BTP Destination Service

To enable client certificate-based authentication in SAP BTP ABAP environment, the following prerequisites have to be met:



SAP BTP cockpit:





### **For Web Socket RFC**

1.  Select your Web Socket destination within your used destination service.

2.  Under *Additional Properties*, apply the*jco.client.tls\_client\_certificate\_logon property*and set it to value `1`.

3.  Choose *Save*.




### **For HTTP**

1.  Select your HTTP destination within your used destination service.

2.  In the *Authentication* dropdown list of the *Destination Configuration* area, select *Client Certificate Authentication*.

3.  Choose *Save*.


