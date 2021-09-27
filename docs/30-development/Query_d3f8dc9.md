<!-- loiod3f8dc9bdcf1405a84f33e2a92228e61 -->

# Query



On top of an analytical model, analytical queries are defined according to your needs to perform different analytical evaluations and calculations. Queries can define the initial layout that is displayed, select the initial data, and can calculate measures that weren’t included in the analytical model. Each query will fulfil a specific purpose and can be designed for different applications \(e.g. reports, KPIs, etc\).

A CDS view that is based on an analytical model \(i.e. it selects from a view with analytics data category FACT, CUBE or DIMENSION, and further operations like joins or unions are not allowed\) becomes an analytical query with annotation `@Analytics.query: true`. These analytical queries will not be processed by a SQL engine but by an analytical engine, which selects the data via SQL from the views of the underlying analytical model containing cubes, dimensions and text views.

Analytical queries can be exposed to business intelligence \(BI\) tools such as SAP Analytics Cloud or Design Studio.

In this guide, we will define a query on top of our flight booking model and consume it on SAP Analytics Cloud.

