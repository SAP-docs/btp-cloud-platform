<!-- loio1503a525e32447e9b62c9a45fd263315 -->

# Authorization Control



[Authorization control in RAP](https://help.sap.com/docs/BTP/923180ddb98240829d935862025004d6/375a8124b22948688ac1c55297868d06.html) protects your business configuration object against unauthorized access to customizing data.

It's recommend to use the authorization `S_TABU_NAM` together with the CDS root entity name of the business object as table name to perform the read and modify operation. However, you can also check against the physical table names or use a different authorization object instead.

The advantage of using the CDS root entity name is that if the business object is extended by a new table you don't need to adjust the authorization check.

See also `Provide Authorization` on how to create the IAM app and add the authorization object.



### Example

The business configuration CDS root entity name is `/ITAPC1/I_Status`.

The data control language \(DCL\) can be dfined as follows:

> ### Sample Code:  
> ```
> @MappingRole: true
> define role /ITAPC1/I_Status {
>   grant select on /ITAPC1/I_Status
>   where ( ) = ASPECT pfcg_auth ( 'S_TABU_NAM', ACTVT = '03', TABLE = '/ITAPC1/I_STATUS' );
> }
> ```

The global authorization check in the behavior implementation can be defined as follows:

> ### Sample Code:  
> ```
>  METHOD GET_GLOBAL_AUTHORIZATIONS.
>     AUTHORITY-CHECK OBJECT 'S_TABU_NAM' ID 'TABLE' FIELD '/ITAPC1/I_STATUS' ID 'ACTVT' FIELD '02'.
>     DATA(is_authorized) = COND #( WHEN sy-subrc = 0 THEN if_abap_behv=>auth-allowed
>                                   ELSE if_abap_behv=>auth-unauthorized ).
>     result-%UPDATE      = is_authorized.
>     result-%ACTION-Edit = is_authorized.
>   ENDMETHOD.
> ```

The authorization instance of *S\_TABU\_NAM* in the IAM app can be defined as follows. Whether or not the user has write or read authorization is finally defined in the General Role Details section of the Business Role the Business Catalog with this IAM app is assigned to.

> ### Sample Code:  
> ```
> ACTVT = Change, Display
> 
> TABLE = /ITAPC1/I_STATUS
> ```

