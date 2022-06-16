<!-- loioa779e5107dbb49a78b77c11f0f39e4ac -->

# Troubleshooting guide for lost access to Kyma runtime

Learn how to get rid of the `forbidden`error messages while using Kyma Dashboard or kubectl CLI tool.



<a name="loioa779e5107dbb49a78b77c11f0f39e4ac__section_bp1_ysh_wtb"/>

## Symptom

You see the `forbidden`error messages while using Kyma Dashboard or kubectl CLI tool, even though they worked fine before.



<a name="loioa779e5107dbb49a78b77c11f0f39e4ac__section_mm2_gth_wtb"/>

## Cause

Before 2.0 Kyma Kyma used XSUAA instance for user authenticaion and authorization. Prior to 2.0 your roles were assigned through role collections in SAP BTP cockpitWith Kyma 2.0, we changed the authentication and authorization model. XSUAA is no longer valid. Instead, now Kyma uses an OIDC identity provider \(default or custom one\) to issue access tokens. Because of that Kyma Roles and Role Bindings must be redefined taking into account new identity subjects, as provided by the new identity provider.

After the 2.0 release, Kyma hosted a migrator tool, which helped with the migration of user permissions. However, the unused XSUAA instances must be now cleaned up, together with the migrator tool.



<a name="loioa779e5107dbb49a78b77c11f0f39e4ac__section_ons_fvh_wtb"/>

## Remedy

You need to bound with a Role or Cluster Role that matches your Role in your team or organization. Kyma administrator must define a \(Cluster\) Role Binding for you, matching your identity subject \(your email or group\).

For more information, follow this guide.

If there is no one with the administrative access, follow this procedure to override administrators in your Kyma runtime.

