<!-- loiod514c43c8250418c8ab8e7d4bd44f083 -->

# Troubleshooting: Kyma Console URL Responds with Not Found 404

Learn how to fix the 404 response in the Console URL for your Kyma runtime.



<a name="loiod514c43c8250418c8ab8e7d4bd44f083__section_etk_4zx_xtb"/>

## Symptom

The console URL for your Kyma runtime is not working anymore, serving a 404 response.



<a name="loiod514c43c8250418c8ab8e7d4bd44f083__section_g25_q1y_xtb"/>

## Cause

With [Kyma 2.0](https://help.sap.com/docs/BTP/922bf2dbe0b646aaaa8cb5e077cfd799/70470339bd09423782c18f2c3a5d7f28.html), Kyma Dashboard is no longer hosted locally in Kyma runtime. Instead, it is a hosted service that can be accessed by referencing Kyma Service Instance ID, as a `path` parameter in the Kyma Dashboard URL. For example, `https://dashboard.kyma.cloud.sap/?kubeconfigID={KYMA_SERVICE_INSTANCE_ID}`.



<a name="loiod514c43c8250418c8ab8e7d4bd44f083__section_w3m_nmy_xtb"/>

## Remedy

1.  Go to your SAP BTP cockpit, open your subaccount overview page, and click *Link to dashboard*.
2.  Optionally, change your browser bookmarks to the updated URL.

