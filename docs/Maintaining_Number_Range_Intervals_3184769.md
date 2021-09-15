<!-- loio3184769bbbb041dea31612026affe85a -->

# Maintaining Number Range Intervals



You can structure the defined character set of a number range object in intervals. For more information on intervals, see [Intervals](https://help.sap.com/viewer/5db4c2a406234b6995553939c79da063/7.5.18/en-US/55273946daac4f9fbde13528aeee10c4.html).



To maintain a number range interval, proceed as follows:

1.  Start the *Manage Number Range Intervals* app from the *Business Configuration* app group on the fiori launchpad.

2.  Choose a number range object from the list and click the arrow-button on the right-hand side of the entry. The *Properties* section is displayed.

3.  In the *Number Ranges* section, press *Create* to create a new interval. Assign a two-character ID as interval number and a lower and upper limit. If the current number range object supports subtypes or is year-dependent, assign a subtype and a year accordingly.

    > ### Note:  
    > Don’t set the *External Interval* flag if you want to use an internal number assignment. That means that during number determination within an application program using that interval, the number range framework automatically assigns a number from the associated number range object to the data record created by the user. Only digits are assigned from internal intervals of the number range object.
    > 
    > For an external number assignment, an application selects a number for a new data record by their own. This can be useful if you want more information to be included in the structure of the number. The number range framework then checks whether the selected number is in an interval of the number range object that is defined as external. However, it does not check whether this number has already been used. Digits and also letters and special characters are assigned from external intervals of a number range object.

4.  Press *Save* to save the new interval.




If you want to delete an interval mark it by using the radio button and press *Delete*.

If you want to change an interval, open it by clicking the arrow-button on the right-hand side of the entry. Then press *Edit* if you want to change the limits or the external flag.

