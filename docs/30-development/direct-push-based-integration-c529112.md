<!-- loioc529112da2a04f6098847446af8aaf2e -->

# Direct Push-Based Integration

With direct push-based integration, you can connect neighboring ABAP Systems \(for example SAP S/4HANA Public/Private Cloud, SAP S/4HANA On-Premise or SAP BTP, ABAP environment tenants\) with each other. In this scenario, the connected systems exchange data \(like business events\) by calling each other directly via RFC.

Advantages of this functionality are a simpler setup and a faster connectivity \(depending on the RFC technology used\). This integration can also be used to try out event-driven architecture in a small scope.

> ### Note:  
> Direct push-based integration can only be used between ABAP systems. An ABAP system can be an SAP S/4HANA Cloud, SAP S/4HANA On-Premise or SAP BTP, ABAP environment system.

For this one-directional process, you need \(at least\) two ABAP systems:

-   one receiver system
-   one \(or more\) sender system\(s\)

