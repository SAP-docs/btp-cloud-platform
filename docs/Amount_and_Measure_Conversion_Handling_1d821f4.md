<!-- loio1d821f43af124e89b6027ae253ac624e -->

# Amount and Measure Conversion Handling

The SAP Gateway framework reacts if a wrong currency or unit code is provided for in- or outbound conversion. In OData Version 4 \(V4\) initial currency codes or initial unit of measure codes are handled similarly as in V2. That is, both a wrong currency and a wrong unit of measure code are ignored - in case of amount formatting this is standard behavior of the function module used for formatting, in case of measure formatting there is a specific logic if the unit code cannot be found in table `T006`. Initial currency code or initial unit of measure code lead to a specific handling.

If a currency code or unit of measure code is provided but cannot be found in `TCURC` or `T006` an exception is raised. The check is implemented based on a direct database selection.

If an application does not want to get exceptions in these cases then the V4 stack provides the possibility to replace the standard amount and measure formatting class.



<a name="loio1d821f43af124e89b6027ae253ac624e__section_imx_gvc_pdb"/>

## $filter and Currency and Lambda

Lambda operators can be combined with amount and currency: The use of currency in $filter with the lambda operator `ANY` or `ALL` is supported, even if the currency is not directly connected to the amount.

Example: `/sap/opu/odata4/iwbep/tea/default/iwbep/tea_busi/0001/Departments?$filter=DEPARTMENT_2_TEAMS/**any\(d:d/**Budget gt 4000 and **d/**BudgetCurrency eq 'JPY')`

