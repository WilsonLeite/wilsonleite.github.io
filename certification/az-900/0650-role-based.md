## Describe Azure role-based access control (RBAC)

Role-based access control (RBAC) is THE central piece of authorization in Azure. 

Each Azure customer (typically, a company) is associated with at least one Tenant in Entra AD. This Tenant has an instance of Azure Active Directory (AAD). This AAD instance contains, amid other things, users and roles. AAD instances come with a default set of roles like Administrator, Contributor, etc. and it is also possible to create custom roles.

These roles can be associated to a hierarchy level and inherited by its sub-levels:
* Management Group
* Subscription
* Resource Group
* Resource

<< Put link to the page explaining this hierarchy >>

Some << or all? >> of the build-in roles are associated to the top level of the resource hierarchy. << How? >>

Each role is associated to a set of rights, like Blob Storage Write, Virtual Machine Creation, etc. and associated to zero or more users. << Or other roles? >>

Therefore, resources (VMs, Blobs, etc.) are associated to roles (like Administrator or MyProductTestAnalyst) directly or by inheritence and the roles are associated to users, so those users have access rights (Read, Write, etc.) on that resource.

<< What is the relationship with policies? >>

Azure RBAC is enforced on any action that is initiated against an Azure resource that passes through Azure Resource Manager, Like the Azure Portal, Azure Cli, or Azure Power Shell. It does not enforce access permissions at the application or data level << but there are exceptions >>.

References:

* Microsoft Learn: [Describe Azure role-based access control](https://learn.microsoft.com/en-us/training/modules/describe-azure-identity-access-security/6-role-based-access-control)
