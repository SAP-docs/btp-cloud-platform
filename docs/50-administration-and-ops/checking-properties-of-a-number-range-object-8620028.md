<!-- loio86200283b5a94f72b1750504cfabb3b1 -->

# Checking Properties of a Number Range Object

To check the properties of a number range object, proceed as follows:

1.  Start the *Manage Number Range Intervals* app from the *Business Configuration* app group on thr fiori launchpad.

2.  Choose a number range object from the list and click the arrow-button on the right-hand side of the entry. The *Properties* section is displayed.

    > ### Note:  
    > You can only display properties. You don't have the option of changing them.

    The following parameters are displayed:

    -   Subobject exists: The number range object distinguishes between further subobjects. For more information, see [https://help.sap.com/viewer/5db4c2a406234b6995553939c79da063/7.5.18/en-US/996c7a939f5c488aaebc91665e673d95.html](https://help.sap.com/viewer/5db4c2a406234b6995553939c79da063/7.5.18/en-US/996c7a939f5c488aaebc91665e673d95.html)

    -   Year-Dependent: This parameter is set to *Yes* if the number range intervals are distinguished according to to-fiscals.

    -   Subobject as Prefix: This parameter is set to *Yes* if determined numbers consist of the prefix \(name of subobject\) and the numbers.

    -   Number of Digits: This parameter determines the length of an interval.

    -   Rolling: This parameter is set to *No* to prevent the number range object intervals from starting from the upper limit automatically.

    -   Buffering Type: This parameter shows whether main memory, parallel, or no buffering is supported.

    -   Number: In case of parallel and main memory, this parameter determines how many numbers are reserved in the buffer for the intervals.

    -   Warning at Remaining: This parameter displays the percentage of numbers remaining in a number range. When reaching the percentage in number assignment, a warning is given. Assuming an interval from 1 to 1000 and a percentage of 10 \(%\) is used, a notification will be triggered if number 900 has been reached.



You can maintain number range objects using the ABAP Development Tool \(ADT\) or APIs. For more information, see

-   ADT:

    [Working with Number Range Objects](https://help.sap.com/viewer/5371047f1273405bb46725a417f95433/Cloud/en-US/28e0a0177ed3452babc1047b3e41f9cb.html)

-   API:

    [Maintaining Number Range Objects](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/bb50d4cb39b74801acdd440c91131034.html)


