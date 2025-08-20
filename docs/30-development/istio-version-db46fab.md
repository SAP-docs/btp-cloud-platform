<!-- loiodb46fab66ac7498192e12742d45e9f1c -->

# Istio Version

To track the changes introduced in the upstream Istio, learn which version of Istio the Istio module installs. To revert certain changes in Istio's behavior when you encounter compatibility issues with its new version, consider enabling compatibility mode.

The version of Istio depends on the version of the Istio module that you use. If a new version of the Istio module introduces a new version of Istio, an upgrade of the module causes an automatic upgrade of Istio. To learn which version of Istio is installed by the newest version of the Istio module, follow [What's New notes](https://help.sap.com/whats-new/f0d108472a9347d99053658d05ae23e2?Component=Kyma+Runtime&locale=en-US&state=DRAFT&q=Istio+module:).



<a name="loiodb46fab66ac7498192e12742d45e9f1c__section_w3n_3rj_rcc"/>

## Compatibility Mode

Compatibility mode allows you to revert certain changes in Istio's behavior, and it is recommended only when you encounter compatibility issues with the new version of Istio. The Istio module supports compatibility with the previous minor version of Istio. For example, for the version of the Istio module that contains Istio 1.24, you can apply a compatibility version of Istio 1.23. See [Compatibility Versions](https://istio.io/latest/docs/setup/additional-setup/compatibility-versions/).

> ### Caution:  
> You can use the compatibility mode to retain the behavior of the current Istio version before a new version of the Istio module with a higher version of Istio is released. Then, the compatibility is first set to a minor version lower than the one you are currently using. If this lower version’s behavior is not compatible with your current mesh setup, some configurations may be broken until the new release of the Istio module is rolled out.

To enable compatibility mode, set the `spec.compatibilityMode` field in the Istio CR to *true*.

When you set `spec.compatibilityMode: true`, the Istio module applies an opinionated subset of Istio `compatibilityVersion` variables. To learn more about the changes that specific compatibility versions revert, follow [What's New notes](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?q=Istio+module&locale=en-US&version=Cloud).

