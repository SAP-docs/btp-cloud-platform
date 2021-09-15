<!-- loioe8a5adb5a3bc4e31bec26dcdde3e8567 -->

# Define a Service Definition and Binding via InA

Define and bind services via the SAP Information Access \(InA\) service.



<a name="loioe8a5adb5a3bc4e31bec26dcdde3e8567__section_cn4_f3c_q4b"/>

## Service Definition

First, you need to create a service definition on top of your query.

1.  In the *Project Explorer*, right-click on your query and select *New Service Definition*.
2.  Provide a *Name* \(e.g. Z\_BOOKINGS\_SERVICE\) and *Description*. The *Exposed Entity* should be your query \(Z\_BOOKINGS\_VE\_QUERY\). Click *Next*.
3.  Select a transport request, then click *Finish*.
4.  After the query is exposed as a service, activate the service definition by clicking the wand icon \(CRTL+F3\).



### Result

 **Z\_BOOKINGS\_SERVICE** 

```
@EndUserText.label: 'Bookings Service Definition'
define service Z_Bookings_Service {
  expose Z_BOOKINGS_VE_Query as Bookings;
}
```



<a name="loioe8a5adb5a3bc4e31bec26dcdde3e8567__section_tvg_g3c_q4b"/>

## Service Binding

Next, you need to create a service binding on top of your service definition.

1.  In the *Project Explorer*, expand *Business Services*. Right-click on your query \(Z\_BOOKINGS\_SERVICE\) and select *New Service Binding*.
2.  Fill in a *Name* \(e.g. Z\_BOOKINGS\_INA\_BINDING\), *Description* and Service Definition \(Z\_BOOKINGS\_SERVICE\). Select *InA - UI*as the *Binding Type*. Click *Next*.
3.  Select a transport request and click *Finish*.
4.  Activate the service binding by clicking the wand icon \(CRTL+F3\).



### Result

After activation, the external service name for your query is displayed.

Note that the analytical query will be displayed with the external service name as datasource in SAP Analytics Cloud.

**Related Information**  


[Business Services Provisioning](Business_Services_Provisioning_0af6dc0.md "")

