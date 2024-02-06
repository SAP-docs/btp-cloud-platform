<!-- loioe5e007357a794a3dad1925ef6acfb6f1 -->

# Constraints

There are some constraints regarding functionality that can be exposed using an SQL service binding.



Only CDS view entities can be exposed, for the following reasons:

-   Only one name \(CDS name equals SQL name\)

-   No table functions for views with parameters \(better performance\)

-   Stricter checks regarding, for example, completeness of currency/unit references

-   Harmonized client handling


These CDS view entities must meet **all** of the following criteria:

-   They are not part of a transactional business object \(BO\).

    -   Reason: Access on SQL-/DB-level doesn’t consider the transactional buffer, so not all relevant data is considered.

    -   Criteria:

        -   Not part of a `ROOT-COMPOSITION` relationship `OR`

        -   They don’t contain the header annotation `@ObjectModel.transactionalProcessingEnabled`



-   They don’t represent an analytical query.

    -   Reason: Access on SQL-/DB-level doesn’t compute the correct results as query contains features that can only be interpreted by an OLAP engine.

    -   Criteria: They don’t contain the header annotation `@Analytical.query`.


-   They don’t represent an \(enterprise\) search model.

    -   Reason: Access on SQL-/DB-level doesn’t compute the correct results as only the enterprise search engine can correctly interpret/consume the view model.

    -   Criteria: They don’t contain the header annotation `@EnterpriseSearch.enabled`.


-   They aren’t implemented via a custom query.

    -   Reason: Access on SQL-/DB-level doesn’t compute the correct results as the query is implemented on ABAP-level.

    -   Criteria: They don’t contain the header annotation `@ObjectModel.query.implementedBy`.


-   They aren’t implemented via an ABAP-implemented analytical cube.

    -   Criteria: They don’t contain the header annotation `@Analytics.readClassName`.


-   They are no private views.

    -   Reason: Even if access on SQL-/DB-level computed the correct results, these views should only be called locally in the system.

    -   Criteria: They don’t contain the header annotation `@VDM.private`.


-   They are no extension include views.

    -   Reason: Even if access on SQL-/DB-level computed the correct results, these views should only be called locally in the system.

    -   Criteria: They don’t contain the header annotation `@VDM.viewType: #EXTENSION`.


-   They don’t represent derivation functions.

    -   Reason: Even if access on SQL-/DB-level computed the correct results, these views should only be called locally in the system.

    -   Criteria:

        -   No header annotation `@VDM.viewType: #DERIVATION_FUNCTION`

        -   No header annotation `@ObjectModel.derivationFunction`



-   They don’t contain elements that meet one of the following criteria:

    -   Virtual elements

        -   Criteria:

            -   They are not defined via the keyword `VIRTUAL` or:

            -   They don’t contain the header annotations `@ObjectModel.virtualElement` or `@ObjectModel.virtualElementCalculatedBy`.



    -   Private elements

        -   Criteria: They don’t contain the header annotation `@Consumption.hidden`.


    -   Derived elements

        -   Criteria: They don’t contain the header annotation `@ObjectModel.value.derivedFrom`.




