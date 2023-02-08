<!-- loiod71a7cdb9c654860b41276b579d30da1 -->

# Kyma Metrics and Logs

In the Kyma environment, you can query, visualize, and explore metrics and logs collected for the Kyma components.

> ### Caution:  
> The in-cluster Logging and Monitoring capabilities, a well as any integration with Grafana, have been deprecated. See *What's New* for Kyma on [Dec 1, 2022](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Kyma%20Runtime&locale=en-US&version=Cloud&Valid_as_Of=2022-12-01%3A2022-12-01&q=observability) and [Jan 20, 2023](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=Kyma%20Runtime&locale=en-US&version=Cloud&Valid_as_Of=2023-01-20%3A2023-01-20).



<a name="loiod71a7cdb9c654860b41276b579d30da1__section_qpn_mdc_grb"/>

## Overview

Project [Grafana](https://grafana.com/oss/grafana/) is an open observability platform for Kubernetes. To access Grafana, go to the Kyma Dashboard and select *Observability* \> *Grafana*.

With Kyma, you get the following Grafana features preconfigured out of the box for your needs:

-   Predefined **dashboards** to visualize the data.
-   **Explore** to query logs and metrics.

> ### Note:  
> If you haven’t exposed Grafana securely yet, read [Set up Grafana Authentication](set-up-grafana-authentication-3e4299c.md).



<a name="loiod71a7cdb9c654860b41276b579d30da1__section_w1j_ndc_grb"/>

## Visualize Data in Dashboards

On the Grafana user interface, you find the list of predefined dashboards with the *Search* function. Search through the dashboards to find the one you want to explore. You can sort the dashboards alphabetically or by assigned tags.

Depending on the selected dashboard, there are further options to query and display the data. For example, in the *Kubernetes/Compute Resources/Pod* dashboard, you can select a *data source*, *Namespace*, and *Pod* to display the graphical representation for metrics collected for a particular Pod in a specific Namespace.

For more information on dashboard search and data filtering, see the [official Grafana documentation](https://grafana.com/docs/grafana/latest/dashboards/search/?src=grafana_gettingstarted).



<a name="loiod71a7cdb9c654860b41276b579d30da1__section_pzg_pdc_grb"/>

## Explore Metrics and Logs with Queries

The *Explore* view provides the following data sources you can query to get information about system metrics and logs:

-   [Prometheus](https://prometheus.io/docs/introduction/overview/) ‒ an open-source toolkit used for system monitoring and alerting.
-   [Loki](https://grafana.com/oss/loki/) ‒ a log aggregation system that collects the logs and indexes their labels for faster log retrieval.

You can view the query results in a graphical representation, and in a table with more details about the values.


<table>
<tr>
<th valign="top">

 



</th>
<th valign="top">

Metrics



</th>
<th valign="top">

Logs



</th>
</tr>
<tr>
<td valign="top">

Where?



</td>
<td valign="top">

To explore the metrics, go to *Explore* \> *Prometheus*.



</td>
<td valign="top">

To check logs collected for specific Kyma components, go to *Explore* \> *Loki*.



</td>
</tr>
<tr>
<td valign="top">

How?



</td>
<td valign="top">

Create a PromQL query using the metrics available under *Metrics*.

For details on creating queries, read the documentation on [Prometheus query editor](https://grafana.com/docs/grafana/latest/features/datasources/prometheus/?src=grafana_gettingstarted#prometheus-query-editor).



</td>
<td valign="top">

Create a Loki query using the labels available under *Log labels*.

For details on creating queries, read the [Querying logs](https://grafana.com/docs/grafana/latest/features/datasources/loki/?src=grafana_gettingstarted#querying-logs) documentation.



</td>
</tr>
</table>



<a name="loiod71a7cdb9c654860b41276b579d30da1__section_nbg_kts_ctb"/>

## Limitations

-   You can view the data in the **read-only mode**. This means, you can browse predefined dashboards and query the data, but you can’t define or edit any configurations.

-   The amount of data that you can **search** at once in predefined dashboards and custom metrics is limited. As a result, large queries that take over 30 seconds to retrieve data may get dropped.

-   You can apply **no custom metrics**, because those are in the Kyma Namespace, which must not be edited.

-   There's a fixed **metrics** retention time and size. Prometheus stores up to 15 GB of data for a maximum period of 30 days. If the default size or time is exceeded, the oldest records are removed first.

-   The configured memory limits of the Prometheus and Prometheus-Istio instances limit the number of **time series samples** that can be ingested. It depends on several factors, for example, the number of Pods and frequency of their recreation, number of Nodes, and topology of the Istio service mesh. The default limit is 800K time series in the Prometheus Pod, and 400K time series in the Prometheus-Istio Pod.

-   There's a fixed **logs** retention time and size. Loki stores up to 30 GB of data for a maximum of 5 days, with maximum ingestion rate of 3MB/s. If the default time is exceeded, the oldest logs are removed first.


