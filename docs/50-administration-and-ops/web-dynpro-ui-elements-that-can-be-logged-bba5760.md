<!-- loiobba576099fb24a2a9cd669a28d8ba150 -->

# Web Dynpro UI Elements that Can Be Logged



<a name="loiobba576099fb24a2a9cd669a28d8ba150__section_N1007D_N1007A_N10002"/>

## Structure

> ### Note:  
> -   Both output and input elements can be logged, but they must be context-bound UI elements.
> 
> -   UI elements that are generated automatically \(for example, when using F4 Help\) can be logged. They do not need to have a UI element ID assigned during application development. In these cases, a temporary ID is assigned during the recording.

The table below shows all UI elements that can be logged in Web Dynpro applications. It shows the properties that can be recorded for each UI element.


<table>
<tr>
<th valign="top">

UI Element

</th>
<th valign="top">

Property

</th>
</tr>
<tr>
<td valign="top">

`TextEdit` 

</td>
<td valign="top">

Value

</td>
</tr>
<tr>
<td valign="top">

`TextView` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`FormattedTextEdit` 

</td>
<td valign="top">

Value

</td>
</tr>
<tr>
<td valign="top">

`FormattedTextView` 

</td>
<td valign="top">

Text

If *value suggest* is active, all proposed texts for this UI element that are displayed on the UI are logged.

</td>
</tr>
<tr>
<td valign="top">

`InputField` 

</td>
<td valign="top">

Value

If *value suggest* is active, all proposed texts for this UI element that are displayed on the UI are logged.

Historical values are not recorded.

</td>
</tr>
<tr>
<td valign="top">

`ToolbarInputField` 

</td>
<td valign="top">

Value

</td>
</tr>
<tr>
<td valign="top">

`DropdownByIndex` 

</td>
<td valign="top">

Texts

</td>
</tr>
<tr>
<td valign="top">

`Caption` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`Button` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToolbarButton` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToolbarDropdownByIndex` 

</td>
<td valign="top">

Texts

</td>
</tr>
<tr>
<td valign="top">

`LinkChoice` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToolbarLinkChoice` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ButtonChoice` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToolbarBtnChoice` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToggleButton` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToolbarToggleButton` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`Checkbox` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`Label` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`LinkToAction` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`LinkToURL` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToolbarLinkToAction` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`ToolbarLinkToURL` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`FileDownload` 

</td>
<td valign="top">

fileName, mimeType, text, data

</td>
</tr>
<tr>
<td valign="top">

`Panel` 

</td>
<td valign="top">

Title

</td>
</tr>
<tr>
<td valign="top">

`RadioButton` 

</td>
<td valign="top">

Text

Selected Key

</td>
</tr>
<tr>
<td valign="top">

`RadioButtonGroupByIndex` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`RadioButtonGroupByKey` 

</td>
<td valign="top">

Selected Key

</td>
</tr>
<tr>
<td valign="top">

`ToggleLink` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`TriStateCheckbox` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`SectionHeader` 

</td>
<td valign="top">

Text

</td>
</tr>
<tr>
<td valign="top">

`DropdownByKey` 

</td>
<td valign="top">

Selected Key

</td>
</tr>
<tr>
<td valign="top">

`ToolbarDropdownByKey` 

</td>
<td valign="top">

Selected Key

</td>
</tr>
<tr>
<td valign="top">

`DropdownListBox` 

</td>
<td valign="top">

ItemText

ItemDescription

Texts

</td>
</tr>
<tr>
<td valign="top">

`ToolbarDropdownListBox` 

</td>
<td valign="top">

ItemText

ItemDescription

Texts

</td>
</tr>
</table>

The constituents of the following multiple UI elements can be logged with Read Access Logging:

-   `Table` 

-   `CTable` 

-   `RowRepeater` 

-   `MultiPane` 

-   `Accordion` and `MultiAccordionItem` 


**Related Information**  


[Channel-Specific Information](channel-specific-information-24c7399.md "The Read Access Logging framework handles the channels generically, but each channel configuration is specific.")

[Tips for Configurations with Log Contexts](tips-for-configurations-with-log-contexts-91d64bf.md)

