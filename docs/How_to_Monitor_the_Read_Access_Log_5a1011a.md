<!-- loio5a1011a87588417187561b63562a900e -->

# How to Monitor the Read Access Log



## Context

You use the read access log for evaluation purposes. In it, all log entries as well as all errors that occurred in Read Access Logging are displayed. There are the following data sources from which you can display log entries:

-   *Expanded Database* \(default\)
-   *Expanded Archive*
-   *Raw Database*

    Only contains the Read Access Logging data of the current client.

-   *Raw Archive*

    Archive of the raw database.

-   *Raw Archive with Index*

    Indexed archive of the raw database.




## Procedure

1.  Open the Read Access Logging: Monitor app.

2.  Select the data source from which you want to display log entries.

3.  Search for the log entries you want to evaluate.

    To search for values of fields that have been accessed, you must use the *Expanded Database* as the source.

    For data source *Archive*, select the archive in which you want to search for log entries. Additionally, there are various search criteria that you can use \(choose the *Add Line* icon\). Typically, you would search for a time range and a log domain or a logging purpose. These search criteria are also available if you search using the database as the source.

    > ### Note:  
    > Searching the archive may be time-consuming. It is much faster if you search an archive with an index. In this case, the search criteria that you have specified for the index are available.

    When you choose *Search*, all log entries are displayed that match your search criteria. By default, only a few attributes are displayed per log entry. You can switch between the default and the extended view.

    Within the search, you can clear the values you have entered for search criteria by choosing *Clear*, and you can reset the search criteria to the default by choosing *Reset*.

    > ### Note:  
    > You can use the button *Download* at the top left of the search result table to save your search results in an Excel file.

4.  Select a log entry to display detailed information at the bottom.

    On the *Details* tab, all fields are displayed with their log domain and, if logged, the field values. On the *Access Environment* tab, you find more information about the underlying object that was logged.


