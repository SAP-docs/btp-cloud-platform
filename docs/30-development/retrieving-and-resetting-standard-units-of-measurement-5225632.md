<!-- loio5225632409dc4791835335bc728bebe9 -->

# Retrieving and Resetting Standard Units of Measurement

Class `CL_UOM_CONTENT_HANDLER` provides methods for reading the standard units of measurement and dimensions delivered by SAP. With this functionality, you can check the standard units of measurement provided by SAP and adjust any custom changes accordingly. For more information, see [Reading Standard Dimensions and Units of Measurement](reading-standard-dimensions-and-units-of-measurement-1f8954f.md).

This API also provides methods for resetting the content to the standard units of measurement, that is, dimensions, ISO codes, and units.

> ### Caution:  
> Before you use the reset methods, check that custom units of measurement are not already in use by any applications. The reset operation completely refreshes the units of measurement content and reverts to the proposed standard values provided by SAP for the current release. All changes of the standard units of measurement will be removed, and the custom ones will be deleted. This includes dimensions, ISO codes, and units.
> 
> When you use this API, you take full responsibility for UoM configuration changes. Use this API only when you fully understand the impact. SAP does not take responsibility for the deletion of custom units.

For more information, see [Resetting Content to Standard Units of Measurement](resetting-content-to-standard-units-of-measurement-545ebc6.md).

