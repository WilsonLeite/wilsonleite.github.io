## Describe the purpose of resource locks

A resource lock prevents resources from being accidentally deleted or changed. Resource locks are inherited and can be applied to individual resources, resource groups, or even an entire subscription.
* Delete lock: Prevent resources from being deleted
* ReadOnly lock: Prevent resources from being changed or deleted

To create or delete management locks, access to Microsoft.Authorization/* or Microsoft.Authorization/locks/* actions is required. Only the Owner and the User Access Administrator built-in roles can create and delete management locks. You can create a custom role with the required permissions.

### References:

Microsoft Learn: 

* [Describe the purpose of resource locks](https://learn.microsoft.com/en-us/training/modules/describe-features-tools-azure-for-governance-compliance/4-describe-purpose-of-resource-locks)
* [Lock your resources to protect your infrastructure](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources)