<!-- loio6c4feeae9fa84269aed1140d1b2725d3 -->

# Prerequisites for Maintaining Client Certificates

To enable client certificate-based authentication in SAP Cloud Platform ABAP Environment, the following prerequisites have to be met:



SAP Cloud Platform Cockpit:





### **For Web Socket RFC**

1.  Select your Web Socket destination within your used destination service.

2.  Under *Additional Properties*, apply the*jco.client.tls\_client\_certificate\_logon property*and set it to value `1`.

3.  Click *Save*.




### **For HTTP**

1.  Select your HTTP destination within your used destination service.

2.  In the *Authentication* dropdown list of the *Destination Configuration* area, select *Client Certificate Authentication*.

3.  Click *Save*.


