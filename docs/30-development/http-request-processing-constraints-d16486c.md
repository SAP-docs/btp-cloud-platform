<!-- loiod16486cd4e24488a8eae19d4f7c42637 -->

# HTTP Request Processing Constraints

In the SAP BTP, ABAP environment, HTTP request processing has constraints: 600-second timeout and 400 MB max request size.



<a name="loiod16486cd4e24488a8eae19d4f7c42637__section_hky_2gr_gdc"/>

## Processing Timeout

The processing timeout for HTTP requests in the SAP BTP, ABAP environment is 600 seconds. After this time period, requests are aborted.

> ### Note:  
> Request processing usually only takes a short amount of time during development because just small data sets are used. Make sure to keep the processing time also for production data set sizes.



<a name="loiod16486cd4e24488a8eae19d4f7c42637__section_fn4_3gr_gdc"/>

## Maximum Request Size

The maximum allowable request size for HTTP requests in the SAP BTP, ABAP environment is 400 MB. Requests that exceed this size limit are rejected to prevent excessive resource consumption and potential performance degradation.

