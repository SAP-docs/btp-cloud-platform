<!-- loioa779e5107dbb49a78b77c11f0f39e4ac -->

# Troubleshooting: Forbidden Access to Kyma

Learn how to get rid of the `forbidden` error messages while using Kyma dashboard or kubectl CLI tool.



<a name="loioa779e5107dbb49a78b77c11f0f39e4ac__section_bp1_ysh_wtb"/>

## Symptom

You see the `forbidden` error messages while using Kyma dashboard or kubectl CLI tool, even though they worked fine before.



<a name="loioa779e5107dbb49a78b77c11f0f39e4ac__section_mm2_gth_wtb"/>

## Cause

Before release 2.0, Kyma used XSUAA instance for user authenticaion and authorization, and your roles were assigned through role collections in SAP BTP cockpit. As of [version 2.0](https://help.sap.com/docs/BTP/922bf2dbe0b646aaaa8cb5e077cfd799/70470339bd09423782c18f2c3a5d7f28.html), Kyma uses the [OIDC Identity Provider](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/85200d8509004236b2a3a637bf1471a8.html) \(default or custom\) to issue access tokens. Because of that, Kyma roles and role bindings must be redefined taking into account new identity subjects, as provided by the new Identity Provider.



<a name="loioa779e5107dbb49a78b77c11f0f39e4ac__section_ons_fvh_wtb"/>

## Remedy

You must bind with a role or cluster role that matches your role in your team or organization. The Kyma runtime administrator must define a \(Cluster\) Role Binding for you, targeting your identity subject \(your email or group\), and the proper role. Follow [Assign Roles in the Kyma Environment](../50-administration-and-ops/assign-roles-in-the-kyma-environment-148ae38.md).

If there is no one with the administrative access, follow [Overwrite Kyma Administrators](../50-administration-and-ops/overwrite-kyma-administrators-df7f9d7.md).

