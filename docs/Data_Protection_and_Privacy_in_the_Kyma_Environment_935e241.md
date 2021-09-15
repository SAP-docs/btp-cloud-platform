<!-- loio935e241ca726412597175bef2add8c57 -->

# Data Protection and Privacy in the Kyma Environment

Protect any confidential and personal data from leakage or misuse by not storing or processing it in an unsafe manner.



<a name="loio935e241ca726412597175bef2add8c57__section_jsc_p14_zkb"/>

## Data Storage and Processing

Kyma environment provides functionality that allows you to store and process data, such as configuration files or specifications. To protect the confidentiality of your information, store only public data. Do not use the environment to process and store any kind of confidential information, including personal data.



<a name="loio935e241ca726412597175bef2add8c57__section_tdc_nb4_zkb"/>

## Personal Data Use in Functions and Event Payloads

Do not store any personal data in Functions or event payloads they receive, as they are not logged. If the Function calls an external API, receives data from an external API, or processes events, ensure compliance with the data privacy laws by making sure that the data is properly logged.



<a name="loio935e241ca726412597175bef2add8c57__section_uf3_xjv_2lb"/>

## Logging Personal Data

The audit log records personal data used by the Kyma environment. On average, it stores the data for at least 201 days, and in case of some services it can be prolonged to up to 400 days. If you want to store any other personal data, be cautious and bear in mind the recommendations provided in [Data Protection and Privacy](Data_Protection_and_Privacy_7e513d3.md).

> ### Note:  
> The logging systems used by the Kyma environment collect logs from stdout. Therefore, you should not log your personal data to stdout, but make sure it is logged using a proper audit logging service.



<a name="loio935e241ca726412597175bef2add8c57__section_kct_3j4_zkb"/>

## Retrieving Personal Data and Audit Log Entries

You can retrieve information regarding your personal data stored in the audit log system, provided that is stored there. To do so, open a [support ticket](https://support.sap.com/en/index.html).

