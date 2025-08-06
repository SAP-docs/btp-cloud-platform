<!-- loioaf3e8565d8f44198b3a15103ed6d52c0 -->

# Analyzing Captured Request Statistics

Get an overview of the request statistics that you have captured using the *Capture Request Statistics* app. View the server response time contribution or the database connections of a single request.



## Context

With the *Capture Request Statistics* app, you can define conditions for which request statistics are collected in the system \(see [Capturing Request Statistics](capturing-request-statistics-e86943a.md)\). You can view the captured data by choosing the *Analyze Request Statistics* button that leads you to the *Captured Request Statistics* screen.

> ### Note:  
> Before ABAP statistics records are shown, they are captured and processed by a collector that runs every minute, so you must expect that captured request statistics are displayed with a delay.



## Procedure

1.  In the *Capture Request Statistics* app, choose a profile for which you want to analyze the captured data.

2.  Choose *Analyze Captured Request Statistics*.

    The *Captured Request Statistics* screen opens. The captured request statististics shown are filtered; only the results for the selected profile are shown.

3.  Analyze the data for different aspects like identifying expensive requests and their context \(program name, transaction code, or path of an HTTP request\), so that you can find the area causing performance issues or resource shortages.

    For more information, see [Captured Request Statistics](https://help.sap.com/viewer/b273a660af4e4948a49a316ea2438f24/Cloud/en-US/55bac4b2a6bb4fb1bd6d993b585311e5.html).


