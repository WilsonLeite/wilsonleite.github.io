## Describe subscriptions

Subscriptions are a unit of management, billing, and scale. Each subscription exists inside a Tenant in the Entra AD (Formerly Azure Active Directory).

If that Tenant is configured to use Management Groups, the subscription is associated to a Management Group.

<< Add link to accounts <=> tenants >>

Each resource is associated to a subscription, so its cost is billed into it. Each subscription generates every month a bill to be paid.

An account requires at least one subscription, but it can have more than one. Using multiple subscriptions may provide these kind of boundaries:
* Billing boundary, where resource costs are grouped per subscription
* Access control boundary, where different users have access to differnt subscriptions and different subscriptinos have differnt policies regarding what resources can be created.

![Azure subscriptions](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/subscriptions-d415577b.png)

<< What is the relationship between Accounts and Tenants? Is it possible to move a subscription to another Tenant? >>

References:

* Microsoft Learn: [Describe Azure management infrastructure](https://learn.microsoft.com/en-us/training/modules/describe-core-architectural-components-of-azure/6-describe-azure-management-infrastructure)
