## Describe the purpose of Azure Policy

Each type of resource on Azure has a set of actions and properties associated to it. 

Some of these properties have an alias associated to it, making them available to be used by a policy.

A policy is a set of conditions build around resources attribute aliases and an effect. Examples of effects are:
* Audit => Log that the resource matched the policy
* Deny => Deny any operation in the resource
* DenyAction => Deny a specific action - for example, delete
* Modify => For example, add a tag
* Audit if not exists => For resources that already exists when the policy is created
* Deploy if not exists => For resources that already exists when the policy is created. It needs to define the identity (account) used for the deployment

Policies can be grouped together in Initiatives. Both Policies and Initiatives can be applied to Any scope, from resource to Management Group <<Tenants??>>. They are then inherited to any sub-scope.

A user assigned as an owner of a scope can manage the policies directly associated to it, but not the inherited ones. 

For example:
* The organization system administrators define an initiative on Management Group level denying the creation of resources outside the _US Central_ region
* A department manager that is assigned as owner of a subscription defines a policy that denies the creation of virtual machines not tagged as PROD having more than 8 cores or 16GB of RAM.

<< What about conflicting policies? In the same level of scope or different levels? Is there an order they are applied? >>

Support flagging resource as exception <<!!!!!>>

References:

* Microsoft Learn: [Describe the purpose of Azure Policy](https://learn.microsoft.com/en-us/training/modules/describe-features-tools-azure-for-governance-compliance/3-describe-purpose-of-azure-policy)
