<!-- loio6213705cecd84757bf1badc19836a3ee -->

# Time Library



The XCO time library provides standard abstractions for working with temporal values.

-   A date \(IF\_XCO\_CP\_TM\_DATE\) consists of values for year, month and day

-   A time \(IF\_XCO\_CP\_TM\_TIME\) consists of values for hour, minute and second

-   A moment \(IF\_XCO\_CP\_TM\_MOMENT\) consists of a fully specified date and time

-   A UNIX timestamp \(IF\_XCO\_CP\_TM\_UNIX\_TIMESTAMP\) consists of an INT8 value specifying the number of seconds that have elapsed since 00:00:00 UTC on Jan 1st, 1970.




### Dates, times and moments

The abstractions date, time and moment correspond to the ABAP temporal types DATS, TIMS and TZNTSTMPS. Given a date, time or moment object, a new object can be derived from each of them by adding or subtracting values from their components or directly overriding specific values. Note that date, time and moment objects are always immutable, i.e. once constructed their values will never change.

Time zone information is explicitly not part of the state of a date, time or moment object.



### Time formats

A time format is a unique representation of a date, time or moment. Currently, the following time formats are supported:

-   ABAP: Will provide the DATS, TIMS and TZNTSTMPS value, respectively

-   ISO 8601 Basic

-   ISO 8601 Extended


Time formats are accessible via XCO\_CP\_TIME=\>FORMAT and can be used either directly or passed to the AS method of a date, time or moment object to obtain the string representation of the object according to the provided time format.

The following code sample illustrates the usage of the various time formats for a moment object:

> ### Sample Code:  
> ```lang-abap
> DATA(lo_moment) = xco_cp_time=>moment(
>   iv_year   = '2020'
>   iv_month  = '09'
>   iv_day    = '16'
>   iv_hour   = '22'
>   iv_minute = '33'
>   iv_second = '49'
> ).
> 
> " LV_ABAP_FORMAT will be of type STRING and have the value 20200916223349.
> DATA(lv_abap_format) = lo_moment->as( xco_cp_time=>format->abap )->value.
> 
> " LV_ISO_8601_BASIC will be of type STRING and have the value 20200916T223349.
> DATA(lv_iso_6801_basic) = lo_moment->as( xco_cp_time=>format->iso_8601_basic )->value.
> 
> " LV_ISO_8601_EXTENDED will be of type STRING and have the value 2020-09-16T22:33:49.
> DATA(lv_iso_6801_extended) = lo_moment->as( xco_cp_time=>format->iso_8601_extended )->value.
> 
> " Restore the moment from LV_ISO_8601_EXTENDED. LO_RESTORED_MOMENT will be an object of type
> " IF_XCO_CP_TM_MOMENT with values equal to LO_MOMENT.
> DATA(lo_restored_moment) = xco_cp_time=>format->iso_8601_extended->to_moment( lv_iso_6801_extended ).
> ```



### Integration with XCO\_CP=\>SY

The XCO time library is tightly integrated with the XCO abstraction for the ABAP SY structure to provide an easy way to access the current time, either as a date, time or moment object or as a UNIX timestamp.

When a date, time or moment object is obtained, the time zone according to which the values should be calculated can be specified in addition. Note that a UNIX timestamp will always be in UTC.

> ### Sample Code:  
> ```lang-abap
> " The current moment in the time zone of the active user.
> DATA(lo_moment_user) = xco_cp=>sy->moment( xco_cp_time=>time_zone->user ).
> 
> " The current moment in UTC.
> DATA(lo_moment_utc) = xco_cp=>sy->moment( xco_cp_time=>time_zone->utc ).
> 
> " The current UNIX timestamp.
> DATA(lo_unix_timestamp) = xco_cp=>sy->unix_timestamp( ).
> ```

Note that if a time zone is not explicitly specified when a date, time or moment object is retrieved from XCO\_CP=\>SY, the time zone of the active user will be taken.



### UNIX timestamps

UNIX timestamps are a common way for describing a given point in time by denoting the number of elapsed seconds since 00:00:00 UTC on Jan 1st, 1970. The XCO time library makes it easy to convert from a given UNIX timestamp to a moment and vice versa:

> ### Sample Code:  
> ```lang-abap
> " The current UNIX timestamp.
> DATA(lo_unix_timestamp) = xco_cp=>sy->unix_timestamp( ).
> 
> " Get the moment for the UNIX timestamp (in the time zone of the active
> " user).
> DATA(lo_moment) = lo_unix_timestamp->get_moment( xco_cp_time=>time_zone->user ).
> 
> " Restore the original UNIX timestamp. The value of LO_RESTORED_UNIX_TIMESTAMP is
> " equal to that of LO_UNIX_TIMESTAMP.
> DATA(lo_restored_unix_timestamp) = lo_moment->get_unix_timestamp( xco_cp_time=>time_zone->user ).
> 
> ```

