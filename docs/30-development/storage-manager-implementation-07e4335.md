<!-- loio07e43355d0614e658625337f89700338 -->

# Storage Manager Implementation

The storage manager integrates the data archiving runtime with the actual storage of the archiving files.

The storage manager will be processed in the different steps of the data archiving process. Within the storage manager implementation, you have the full flexibility to choose which storage will be integrated. Possible options to integrate external storages already exist in ABAP Cloud:

-   [Via cloud connector for On-Premise integration](https://help.sap.com/docs/btp/sap-business-technology-platform/integrating-on-premise-systems?version=Cloud)

-   [Developing External Service Consumption \(Outbound Communication\)](developing-external-service-consumption-outbound-communication-f871712.md)


As a precondition for data archiving, you need to create a class which implements the interface `IF_ARCH_STORAGE_MANAGER`. This interface provides the following methods:

-   The method <code><i>IF_ARCH_STORAGE_MANAGER~STORE_FILE</i></code> stores the archived data to a physical storage location outside of the SAP system. It will be called by the ADK write API and has the following parameters:


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_ARCHIVE_KEY</i></code>
    
    </td>
    <td valign="top">
    
    Key of the archive file to be stored
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_DATA</i></code>
    
    </td>
    <td valign="top">
    
    Content of the archive file \(binary data\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_LENGTH</i></code>
    
    </td>
    <td valign="top">
    
    Length of the binary content
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Returning: <code><i>RV_DOCUMENT_ID</i></code>
    
    </td>
    <td valign="top">
    
    Document identifier which can be used to access the archived data. The document ID needs to be returned by the storage manager and will be stored in a link table in the SAP system.
    
    </td>
    </tr>
    </table>
    
-   The method <code><i>IF_ARCH_STORAGE_MANAGER~GET_BYTESTREAM</i></code> retrieves parts of the binary content of an archive file via range request. It will be called by an ADK API to read the archived data and has the following parameters:


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_DOCUMENT_ID</i></code>
    
    </td>
    <td valign="top">
    
    Document identifier
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_FROM_OFFSET</i></code>
    
    </td>
    <td valign="top">
    
    Data object address
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_LENGTH</i></code>
    
    </td>
    <td valign="top">
    
    Length of the binary content
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Exporting: <code><i>EV_DATA</i></code>
    
    </td>
    <td valign="top">
    
    Content of the archive file \(binary data\)
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Exporting:<code><i>EV_ACT_LENGTH</i></code>
    
    </td>
    <td valign="top">
    
    Length of the byte stream which is returned
    
    </td>
    </tr>
    </table>
    
-   The method <code><i>IF_ARCH_STORAGE~RETRIEVE_FILE</i></code> retrieves the entire binary content of an archive file.


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_DOCUMENT_ID</i></code>
    
    </td>
    <td valign="top">
    
    Document identifier
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Returning:<code><i>RV_DATA</i></code>
    
    </td>
    <td valign="top">
    
    Content of the archive file \(binary data\) which will be returned by the storage manager
    
    </td>
    </tr>
    </table>
    
-   The method <code><i>IF_ARCH_STORAGE_MANAGER~DELETE FILE</i> </code> deletes the archive file from the external storage system.


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Importing: <code><i>IV_DOCUMENT_ID</i></code>
    
    </td>
    <td valign="top">
    
    Document identifier
    
    </td>
    </tr>
    </table>
    

> ### Note:  
> If any errors appear during any of the operations of the storage manager, please use the exception class `CX_ARCH_STORAGE_MANAGER`.

