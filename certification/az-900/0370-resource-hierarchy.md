## Describe the hierarchy of resource groups, subscriptions, and management groups

When activated for a Tenant, [Management Groups](./0360-management-groups.md) can be organized in a tree up to six levels deep, having up to 10000 Management Groups.

If Management Groups are active, all [Subscriptions](./0350-subscriptions.md) are associated to a Management Group.

[Resource Groups](./0340-resource-groups.md) are associated to a Subscription.

Resources are associated to a Resource Group.

![Management hierachy](https://learn.microsoft.com/en-ca/azure/role-based-access-control/media/elevate-access-global-admin/elevate-access.png)

References:

* Microsoft Learn: [Describe Azure management infrastructure](https://learn.microsoft.com/en-us/training/modules/describe-core-architectural-components-of-azure/6-describe-azure-management-infrastructure)
