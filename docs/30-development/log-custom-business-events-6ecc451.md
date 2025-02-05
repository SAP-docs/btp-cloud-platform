<!-- loio6ecc45140a2849a5b9df0db3f522b65b -->

# Log Custom Business Events

You can create your own business events with SAP-defined or customer-defined objects. For more information on creating events, see [Business Events](https://help.sap.com/docs/abap-cloud/abap-rap/concept-business-events).



## Define Events for Business Event Logging

The event binding can contain an SAP-defined or a customer-defined object and and an operation.

Business events should be declared in the correct node they refer to - the child node or the root node.

You must add the `@ObjectModel.sapObjectNodeType.name` annotation in the abstract event entity denoting the SAP Object Node Type the event refers to.



### `@ObjectModel.sapObjectNodeType.name Annotation`

`@ObjectModel.sapObjectNodeType.name Annotation` : The name of the object components the event refers to.

This can be an SAP-defined object component like SalesOrderItem, or a customer defined object component. For example: Z\_MyObjectItem. If the event refers to the object as a whole or the header of the object, then the object component name should be the same as the object component name in the event binding.

> ### Sample Code:  
> ```
> @ObjectModel.sapObjectNodeType.name: 'Z_MySalesOrderItem'
> define abstract entity ZD_SALESORDERITEMCREATED
> { ItemNo : item_no
>  Status : Status } 
> ```

In case an event referring to a child node is exceptionally assigned to a root node to support backward compatibility, then the following `@Event.sapObjectNodeTypeKey` annotation is additionally required:



### `@Event.sapObjectNodeTypeKey Annotations`

`@Event.sapObjectNodeTypeKey Annotations` : The key of the object node the event refers to needs to be defined if this is a customer defined object component, or if the key is deviating from SAP standard. The elements of the key must either be defined in the underlying behaviour definition, or the abstract entity itself.

> ### Note:  
> The order of keys in the annotation should be the same as they are in the node's corresponding entity.

> ### Sample Code:  
> ```
> @ObjectModel.sapObjectNodeType.name: 'Z_MySalesOrderItem' 
>  @Event.sapObjectNodeTypeKey : [ { element : 'SalesOrder' } , { element : 'ItemNo' } ] 
> define abstract entity ZD_SALESORDERITEMCREATED
>  { ItemNo : item_no
> Status : Status }
> ```

