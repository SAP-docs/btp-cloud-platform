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
<th>

UI Element



</th>
<th>

Property



</th>
</tr>
<tr>
<td>

 `TextEdit` 



</td>
<td>

Value



</td>
</tr>
<tr>
<td>

 `TextView` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `FormattedTextEdit` 



</td>
<td>

Value



</td>
</tr>
<tr>
<td>

 `FormattedTextView` 



</td>
<td>

Text

If *value suggest* is active, all proposed texts for this UI element that are displayed on the UI are logged.



</td>
</tr>
<tr>
<td>

 `InputField` 



</td>
<td>

Value

If *value suggest* is active, all proposed texts for this UI element that are displayed on the UI are logged.

Historical values are not recorded.



</td>
</tr>
<tr>
<td>

 `ToolbarInputField` 



</td>
<td>

Value



</td>
</tr>
<tr>
<td>

 `DropdownByIndex` 



</td>
<td>

Texts



</td>
</tr>
<tr>
<td>

 `Caption` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `Button` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToolbarButton` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToolbarDropdownByIndex` 



</td>
<td>

Texts



</td>
</tr>
<tr>
<td>

 `LinkChoice` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToolbarLinkChoice` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ButtonChoice` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToolbarBtnChoice` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToggleButton` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToolbarToggleButton` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `Checkbox` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `Label` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `LinkToAction` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `LinkToURL` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToolbarLinkToAction` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `ToolbarLinkToURL` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `FileDownload` 



</td>
<td>

fileName, mimeType, text, data



</td>
</tr>
<tr>
<td>

 `Panel` 



</td>
<td>

Title



</td>
</tr>
<tr>
<td>

 `RadioButton` 



</td>
<td>

Text

Selected Key



</td>
</tr>
<tr>
<td>

 `RadioButtonGroupByIndex` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `RadioButtonGroupByKey` 



</td>
<td>

Selected Key



</td>
</tr>
<tr>
<td>

 `ToggleLink` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `TriStateCheckbox` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `SectionHeader` 



</td>
<td>

Text



</td>
</tr>
<tr>
<td>

 `DropdownByKey` 



</td>
<td>

Selected Key



</td>
</tr>
<tr>
<td>

 `ToolbarDropdownByKey` 



</td>
<td>

Selected Key



</td>
</tr>
<tr>
<td>

 `DropdownListBox` 



</td>
<td>

ItemText

ItemDescription

Texts



</td>
</tr>
<tr>
<td>

 `ToolbarDropdownListBox` 



</td>
<td>

ItemText

ItemDescription

Texts



</td>
</tr>
</table>

The constituents of the following multiple UI elements can be logged with Read Access Logging:

-    `Table` 

-    `CTable` 

-    `RowRepeater` 

-    `MultiPane` 

-    `Accordion` and `MultiAccordionItem` 


**Related Information**  


[Channel-Specific Information](Channel-Specific_Information_24c7399.md "The Read Access Logging framework handles the channels generically, but each channel configuration is specific.")

[Tips for Configurations with Log Contexts](Tips_for_Configurations_with_Log_Contexts_91d64bf.md)

