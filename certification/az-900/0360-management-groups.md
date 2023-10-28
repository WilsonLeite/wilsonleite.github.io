## Describe management groups

Management Groups is an optional feature inside a Tenant. Once opted in, a root Management Group is created - named Tenant Management Group - and all existing  subscriptions are associated to it.

Management Groups can be nested up to six levels of depth. Subscriptions can be created directly inside of a Management Group, as well as be moved tro another Management Group. << Only inside the same Tenant? >>

![Management groups](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/management-groups-subscriptions-dfd5a108.png)

Management groups give you enterprise-grade management at a large scale. The governance conditions applied to the Management Groups are automatically inherited to its children the same way that resource groups inherit settings from subscriptions and resources inherit from resource groups.

For example, you can apply policies to a management group that limits the regions available for virtual machine (VM) creation. This policy would be applied to all nested management groups, subscriptions, and resources and allow VM creation only in authorized regions.

<< how to do that? examples of other types of policies? >>

References:

Microsoft Learn: 
* [Describe Azure management infrastructure](https://learn.microsoft.com/en-us/training/modules/describe-core-architectural-components-of-azure/6-describe-azure-management-infrastructure)
* [What are Azure management groups?](https://learn.microsoft.com/en-ca/azure/governance/management-groups/overview)
* [Elevate access to manage all Azure subscriptions and management groups](https://learn.microsoft.com/en-ca/azure/role-based-access-control/elevate-access-global-admin)




