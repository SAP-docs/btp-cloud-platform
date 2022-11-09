<!-- loioa7a5cfa16e714a81bdf8b1709b3f3152 -->

# Developing Metrics for Health Monitoring

Learn how you can add your own metrics to Health Monitoring in SAP Cloud ALM or SAP Focused Run.



<a name="loioa7a5cfa16e714a81bdf8b1709b3f3152__section_l5b_q1y_x5b"/>

## Use Case

SAP Cloud ALM provides you with insights regarding the health of Cloud services. In the overview dashboard, all health monitoring metrics are exposed, and for each metric, a detailed history is available. While a number of metrics defined by SAP are available for checking customer-initiated operational issues in the ABAP environment, you might want to add your own application-specific metrics. These metrics serve to monitor the health of your own customer or partner solutions running on the ABAP environment in SAP BTP. Similarly, you might want to have your own metrics in Health Monitoring of SAP Focused Run.



<a name="loioa7a5cfa16e714a81bdf8b1709b3f3152__section_sy5_r1y_x5b"/>

## Architecture Overview

![](images/Health_Monitoring_for_Partners_and_Customers_Architecture_e2b8baf.png)

The central object in this context is the metric provider, an ABAP repository object that references an implementing class. The class defines a metric model for your application and implements the metric measurement. The metric model defines, for example, what kind of metrics are available in the system, how often a metric is measured, its tags, or its unit of measurement.

An application job \(the generic simple metric collector\) runs regularly. It calls up the `GET_METRIC_VALUES( )` method of all metric providers and stores all measured values as metrics in a generic format in the metric store. After an administrator has set up a communication arrangement based on the communication scenario `SAP_COM_0527`, the metrics are automatically pushed from the generic metric store to SAP Cloud ALM and SAP Focused Run.



<a name="loioa7a5cfa16e714a81bdf8b1709b3f3152__section_ryx_t1y_x5b"/>

## About This Documentation

In this documentation, you get information about creating your own metric providers as a developer. In addition, there's also a short information for administrators about creating an application job that calls up all created metric providers and transfers their measured values to the generic metric store.

For more information about setting up SAP Cloud ALM and SAP Focused Run for the ABAP environment, see [Central Health Monitoring Using SAP Focused Run and SAP Cloud ALM](../50-administration-and-ops/central-health-monitoring-using-sap-focused-run-and-sap-cloud-alm-8d6e2e7.md).

