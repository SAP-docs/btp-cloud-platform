<!-- loio524cc11778c64e2a8322cb3ec71709e5 -->

# Multitenant Java Applications

In the Cloud Foundry environment, you can develop and run multitenant Java applications, and share them with multiple consumers simultaneously on SAP BTP.



<a name="loio524cc11778c64e2a8322cb3ec71709e5__section_rss_gp2_rnb"/>

## What is Multitenancy?

SAP BTP provides a multitenant functionality that allows application providers to own, deploy, and operate tenant-aware applications for multiple consumers, with reduced costs. For example, the application provider can upgrade the application for all your consumers instead of performing each update individually, or can share resources across multiple consumers. The application consumers launch the applications using consumer-specific URLs, and can configure certain application features.

To learn more, see: [Developing Multitenant Applications in the Cloud Foundry Environment](developing-multitenant-applications-in-the-cloud-foundry-environment-5e8a2b7.md)



<a name="loio524cc11778c64e2a8322cb3ec71709e5__section_hnd_hsm_qsb"/>

## Multitenancy in the SAP Java Buildpack

SAP Java Buildpack provides the possibility for multitenant applications running on Cloud Foundry to consume tenant-aware data sources out of the box. This is achieved by integrating the SAP Service Manager capabilities in the buildpack. The SAP Java buildpack provides out of the box tenant-aware data sources for:

-   All tenants that have already been onboarded to an SAP Service Manager service instance.
-   Newly onboarded tenants at runtime. No restart of the Java application is needed.



<a name="loio524cc11778c64e2a8322cb3ec71709e5__section_hgv_btm_qsb"/>

## Configure the Application Multitenancy

To achieve multitenant support in your application deployed with the SAP Java buildpack, your application should meet the following requirements:

1.  Multitenancy support for Cloud Foundry is set up in advance. See: [Developing Multitenant Applications in the Cloud Foundry Environment](developing-multitenant-applications-in-the-cloud-foundry-environment-5e8a2b7.md)

2.  The application should be bound to a managed database service. Your application should also use one of the following datasources that the SAP Java buildpack provides:

    -   `com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory`
    -   `com.sap.xs.jdbc.datasource.tomee7.TomEE7DataSourceFactory`

    See section: [Configure Tenant-Aware Data Source](multitenant-java-applications-524cc11.md#loio524cc11778c64e2a8322cb3ec71709e5__section_tenant_aware_datasource)

3.  The security concept that the application uses should be XSUAA. See section: [Configure XSUAA Authentication Method](multitenant-java-applications-524cc11.md#loio524cc11778c64e2a8322cb3ec71709e5__section_xsuaa_auth_method)


Once these requirements are fulfilled, the application takes care of the onboarding of tenants in the SAP Service Manager service they use. For each request that comes from the application, the SAP Java buildpack will acquire \(obtain\) the tenant ID from the request through the JWT token provided by the XSUAA service. The buildpack will provide different database instance object for each tenant.



<a name="loio524cc11778c64e2a8322cb3ec71709e5__section_tenant_aware_datasource"/>

## Configure Tenant-Aware Data Source

Once a multitenant application is bound to a managed database service instance, provisioning of the tenant-aware data source comes out of the box.

In the following example of **context.xml**, the `jpa-db-managed` service instance is used to configure the data source. Provided that the `jpa-db-managed` service instance is of type *managed-hana* or *service-manager*, it will make the `jdbc/DatasourceOne` tenant aware.

```

<?xml version='1.0' encoding='utf-8'?>
<Context>
 <Resource name="jdbc/DatasourceOne"
    auth="Container"
    type="javax.sql.DataSource"
    factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
    service="jpa-db-managed"
    personalize="true"/>
</Context>
```

If a custom tenant provider is used, define the class in the `Resource` configuration as a `tenantProvider`. For example:

```

<?xml version='1.0' encoding='utf-8'?>
<Context>
  <Resource name="jdbc/DatasourceOne"
    auth="Container"
    type="javax.sql.DataSource"
    factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
    service="jpa-db-managed"
    personalize="true"/>
    tenantProvider="com.sap.test.custom.provider.UserDefinedTenantProvider"/>
</Context>
```

**Tip:** If you want a non-JPA application to consume `jdbc/Outsource`, use the following:

```

public class TestServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;

	@Resource(name = "jdbc/DatasourceOne")
	private DataSource tenantAwareDataSource;

 ...
}
```



<a name="loio524cc11778c64e2a8322cb3ec71709e5__section_xsuaa_auth_method"/>

## Configure XSUAA Authentication Method

The configuration is done in the `login-config` section of the **web.xml** file:

```

<?xml version=“1.0” encoding=“UTF-8”?>
 <web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance xmlns="http://java.sun.com/xml/ns/javaee xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd version=“3.0”>
  <display-name>sample</display-name>
  <login-config>
   <auth-method>XSUAA</auth-method>
  </login-config>
 </web-app>
```



<a name="loio524cc11778c64e2a8322cb3ec71709e5__section_slt_r5m_qsb"/>

## Control Determination of the Current Tenant for Tenant-Aware Data Source

As described above, by default the tenant-aware data source determines which tenant to be used for a specific request by getting the current log user from the JWT token provided by the XSUAA service.

For specific scenarios, the application can get control over the tenant determination with the following steps:

1.  Implement and bundle a class which will handle the tenant provisioning. For example:

    ```
    
    package com.sap.test.custom.provider;
    
    public class UserDefinedTenantProvider implements Supplier<String> {
    
    	private static ThreadLocal<String> currentTenant = new InheritableThreadLocal<>();
    
    	public static ThreadLocal<String> getCurrentTenant() {
    		currentTenant.set("tenant1");
    		return currentTenant;
    	}
    
    	@Override
    	public String get() {
    		return getCurrentTenant().get();
    	}
    }
    ```

    > ### Note:  
    > The class is **required** in order to implement the `Supplier` interface.

2.  Define the application class as a `tenantProvider`. For example:

    ```
    
    <?xml version='1.0' encoding='utf-8'?>
    <Context>
      <Resource name="jdbc/DatasourceOne"
        auth="Container"
        type="javax.sql.DataSource"
        factory="com.sap.xs.jdbc.datasource.tomcat.TomcatDataSourceFactory"
        service="jpa-db-managed"
        personalize="true"/>
        tenantProvider="com.sap.test.custom.provider.UserDefinedTenantProvider"/>
    </Context>
    ```


**Related Information**  


[Providing Multitenant Applications to Consumers in the Cloud Foundry Environment](providing-multitenant-applications-to-consumers-in-the-cloud-foundry-environment-7a013f1.md "Once you have built a multitenant application in the Cloud Foundry environment using SAP BTP, you can then share the application with multiple consumers, such as business units in your organization.")

