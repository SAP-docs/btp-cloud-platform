<!-- loio95a410144d7c449687c957da0cc43a0d -->

# Kyma Module Releases

For each of your Kyma modules, you can choose if you want the regular release, or an earlier preview so you can test new features and provide early feedback.



<a name="loio95a410144d7c449687c957da0cc43a0d__section_kyma_release_channels"/>

## Kyma Release Channels

Kyma is released in a modular approach. To learn more about the available Kyma modules, read: [Kyma Modules](kyma-modules-0dda141.md).

Kyma modules are deployed in the following release channels:

-   *Regular channel* is the default release channel.

-   *Fast channel* provides more frequent releases. It offers early previews of all new features and changes before they are promoted to the regular channel. It also allows you to test and provide feedback on the new features sooner.


According to the Kyma modules\` release cycle, we first release a new module's major or minor version in the fast channel. After approximately two weeks, we promote the release to the regular channel.

> ### Note:  
> In case of important functionality fixes or critical vulnerabilities identified by our security organization, the timeline doesn't apply, as we provide hotfixes between regular releases.

You can use one or both release channels in your Kyma cluster, but you can define only one release channel per module. For example, you can mix different modules from the regular and fast channels in your development cluster, but you cannot deploy the same module in the regular and fast versions in one cluster.

> ### Tip:  
> You can upgrade module versions, but you cannot downgrade them. To test the upstream versions, you can switch a module or an entire cluster from the regular channel to the fast one.
> 
> To return to the regular channel, you must wait until the version you are using in the fast channel is promoted to the regular channel. Once the versions in both the fast and regular channels are the same, you can switch back to regular. Alternatively, you can delete and add your module from the regular channel.

To find out which module version is running in your cluster, go to [Kyma dashboard](https://dashboard.kyma.cloud.sap/clusters).



<a name="loio95a410144d7c449687c957da0cc43a0d__section_eqm_3qd_gzb"/>

## Release Notes

A release of a new module’s version is announced with a release note in [What’s New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&version=Cloud) for both, the fast and regular channels:

-   On the day of the release in the fast channel, a release note is published with the *Preview* label.

-   After approximately two weeks, the module version becomes available in the regular channel and the *Preview* label is removed.


For details on the Kyma release schedule, see [3459911](https://me.sap.com/notes/3459911).

> ### Note:  
> For any changes that require user action, we notify users at least three months in advance in the “What’s New for SAP Business Technology Platform”. You get information on the required or recommended actions, as well as links to more detailed guidance, including details on the opt-in solutions and migration timelines.
> 
> To get notifications on such changes and other updates, subscribe to [What’s New for SAP Business Technology Platform](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=Kyma+Runtime).

**Related Information**  


[Kyma Functionalities](kyma-functionalities-4b83be9.md "SAP BTP, Kyma runtime and open source project &quot;Kyma&quot; offer slightly different functionalities and install a different set of components.")

