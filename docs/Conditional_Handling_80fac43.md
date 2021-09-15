<!-- loio80fac4399d80404f83608452e752caee -->

# Conditional Handling

To speed up processing during service development you can use a condition, for example, `if-match`.

For this, a generic implementation of conditional handling is available for `GET if-none-match` and `PUT if-match`. Application developers can use the generic implementation or redefine the methods for conditional handling.



<a name="loio80fac4399d80404f83608452e752caee__section_vhf_gqr_51b"/>

## IF-MATCH

The `if-match` HTTP request header is supported for `PUT`, `DELETE` and `PATCH` requests.

-   If the value of the provided Etag matches the value of the corresponding Etag property, a 20x HTTP response \(OK\) is returned.

-   If the value of the provided Etag does not match the value of the corresponding Etag property, a 412 HTTP response \(Precondition Failed\) is returned.

-   If the entity has an Etag property, the `@odata.etag` is added to the response payload of requests with `$select`.


Generic conditional handling is done in the implementation in the abstract data provider of the following methods:

-   `/IWBEP/IF_V4_DP_ADVANCED~DELETE_ENTITY`

    `/IWBEP/CL_V4_ABS_DATA_PROVIDER -> CHECK_MODIFICATION_CONDITIONS`

-   `/IWBEP/IF_V4_DP_ADVANCED~UPDATE_ENTITY`

    `/IWBEP/CL_V4_ABS_DATA_PROVIDER -> CHECK_MODIFICATION_CONDITIONS`




<a name="loio80fac4399d80404f83608452e752caee__section_k4g_hqr_51b"/>

## IF-NONE-MATCH

The `if-none-match` HTTP request header is supported only for a `GET` entity request.

-   If the value of the provided Etag matches the value of the corresponding Etag property, a 304 HTTP response \(Not Modified\) is returned.

-   If the value of the provided Etag does not match the value of the corresponding Etag property, a 200 HTTP response \(OK\) is returned.

-   If the application has not done the conditional handling in the `BASIC` method, then there is the generic conditional handling as fallback the advanced method `/IWBEP/IF_V4_DP_ADVANCED~READ_ENTITY`.

