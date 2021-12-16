<!-- loio935e241ca726412597175bef2add8c57 -->

# Data Protection and Privacy in the Kyma Environment

To protect any confidential and personal data from leakage or misuse, you must store and process it safely.



<a name="loio935e241ca726412597175bef2add8c57__section_jsc_p14_zkb"/>

## Data Storage and Processing

In the Kyma environment you can store and process data, such as configuration files or specifications. To protect the confidentiality of your information, store only public data. Don't use the environment to process and store any kind of confidential information, including personal data.



<a name="loio935e241ca726412597175bef2add8c57__section_uf3_xjv_2lb"/>

## Kyma Logging

A Kyma runtime collects two log types: audit and application.



### Audit Logs

A Kyma runtime collects audit logs for configuration changes to the runtime itself, Kubernetes API server, and security events. Usually, those logs contain the user account \(technical account or email address\) and the client IP address of the subject who triggered the changes. No other personal data is stored in the audit logs. On average, the logs store the data for 90 days. If you want to store any other personal data, be cautious and bear in mind the recommendations provided in [Data Protection and Privacy](data-protection-and-privacy-7e513d3.md).



### Application Logs

A Kyma runtime collects access logs and application logs provided by the Kyma system components. Those logs reflect regular events that occurred in a Kyma runtime and should not include any personal or sensitive data.



<a name="loio935e241ca726412597175bef2add8c57__section_kct_3j4_zkb"/>

## Retrieving Audit Log Entries

You can retrieve information stored in the audit log system. To do so, open a [support ticket](https://support.sap.com/en/index.html).

