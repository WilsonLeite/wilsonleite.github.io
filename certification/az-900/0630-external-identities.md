## Describe external identities in Azure, including business-to-business (B2B) and business-to-customer (B2C)

An external identity is a person, device, service, etc. that is outside your organization.  The external user’s identity provider manages their identity, and the access to the Tenant's resources is managed with Microsoft Entra ID or Azure AD B2C.

<< How does this work in practice? >>

![Azure AD External Identities](https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/azure-active-directory-external-identities-5a892021.png)

It is possible to use any combination of these capabilities:

* Business to business (B2B) collaboration: Integrate external users allowing them to use their preferred identity to sign-in in the Tenant. These users are represented in the tenant's directory, typically as guest users.
* B2B direct connect: Mutual, two-way trust with another Microsoft Entra organization for seamless collaboration. These external users are not represented in the local tenant's directory. Microsoft Teams supports this integration by sharing channels, making the external users visible from within the Teams shared channel and can be monitored in Teams admin center reports.
* Microsoft Entra business to customer (B2C): << The description in the Learn page is useless >>


References:

* Microsoft Learn: [Describe Azure external identities](https://learn.microsoft.com/en-us/training/modules/describe-azure-identity-access-security/4-external-identities)
