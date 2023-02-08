<!-- loio452d44afda25431485ebf972d760692b -->

# Getting the Text Table of a Database Table

The XCO standard abstraction for database tables \(`IF_XCO_DATABASE_TABLE`\) provides a convenient way to determine the text table of a given database table \(if it has one\):

> ### Sample Code:  
> ```abap
> 
> DATA(lo_database_table) = xco_cp_abap_dictionary=>database_table( 'ZMY_DBT' ).
>  
> " From a database table handle (in this case LO_DATABASE_TABLE) we can obtain
> " the handle for its text table.
> DATA(lo_text_table) = lo_database_table->text_table( ).
>  
> " Using this text table handle, we can first check if a text table exists at all
> " (for the previously fixed database table) and if so, obtain information about
> " it.
> DATA(lv_text_table_exists) = lo_text_table->exists( ).
>  
> IF lv_text_table_exists EQ abap_true.
>   " The name of the text table that belongs to database table ZMY_DBT.
>   DATA(lv_text_table_name) = lo_text_table->get( )->name.
>  
>   " We can also use the text table handle to get the name of the check field of the
>   " database table/text table relationship.
>   DATA(lv_check_field_name) = lo_text_table->get_check_field( )->name.
> ENDIF.
> ```

