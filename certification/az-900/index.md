# Microsoft Certified: Azure Fundamentals

### Exam AZ-900: Microsoft Azure Fundamentals

You can describe Azure architectural components and Azure services, such as:

* Compute
* Networking
* Storage

You can also describe features and tools to secure, govern, and administer Azure.

### External links:

* [Microsoft Certified: Azure Fundamentals](https://learn.microsoft.com/en-us/redentials/certifications/azure-fundamentals/)
    * [Exam AZ-900: Microsoft Azure Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/exams/az-900/)
    * [Skills measured](https://learn.microsoft.com/en-ca/credentials/certifications/resources/study-guides/az-900#skills-measured-as-of-july-31-2023)
* Microsoft Learn
    * [Study Guide](https://learn.microsoft.com/en-ca/credentials/certifications/resources/study-guides/az-900)
    * Learning Path
        * [Describe cloud concepts](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/)
        * [Describe Azure architecture and services](https://learn.microsoft.com/en-us/training/paths/azure-fundamentals-describe-azure-architecture-services/)
        * [Describe Azure management and governance](https://learn.microsoft.com/en-us/training/paths/describe-azure-management-governance/)
* Pluralsight
    * [ACloudGuru](https://app.pluralsight.com/library/courses/az-900-microsoft-azure-fundamentals-2/table-of-contents)
    * Microsoft Azure Fundamentals (AZ-900) [Path](https://app.pluralsight.com/paths/certificate/microsoft-azure-fundamentals-az-900)

## Skills measured as of July 31st, 2023

### Describe cloud concepts (25–30%)

Describe cloud computing
* [Define cloud computing](./0010-cloud-computing.md)
* [Describe the shared responsibility model](./0020-shared-responsibility.md)
* [Define cloud models, including public, private, and hybrid](./0030-cloud-models.md)
* [Identify appropriate use cases for each cloud model](./0040-cloud-model-use.md)
* [Describe the consumption-based model](./0050-consumption-based.md)
* [Compare cloud pricing models](./0060-pricing-models.md)
* [Describe serverless](./0070-serverless.md)

Describe the benefits of using cloud services
* [Describe the benefits of high availability and scalability in the cloud](./0110-high-availability.md)
* [Describe the benefits of reliability and predictability in the cloud](./0120-reliability.md)
* [Describe the benefits of security and governance in the cloud](./0130-governance.md)
* [Describe the benefits of manageability in the cloud](./0140-manageability.md)

Describe cloud service types
* [Describe infrastructure as a service (IaaS)](./0210-iaas.md)
* [Describe platform as a service (PaaS)](./0220-paas.md)
* [Describe software as a service (SaaS)](./0230-saas.md)
* [Identify appropriate use cases for each cloud service (IaaS, PaaS, and SaaS)](./0240-use-cases.md)

### Describe Azure architecture and services (35–40%)

Describe the core architectural components of Azure
* [Describe Azure regions, region pairs, and sovereign regions](./0310-regions.md)
* [Describe availability zones](./0320-zones.md)
* [Describe Azure datacenters](./0330-datacenters.md)
* [Describe Azure resources and resource groups](./0340-resource-groups.md)
* [Describe subscriptions](./0350-subscriptions.md)
* [Describe management groups](./0360-management-groups.md)
* [Describe the hierarchy of resource groups, subscriptions, and management groups](./0370-resource-hierarchy.md)

Describe Azure compute and networking services
* [Compare compute types, including containers, virtual machines, and functions](./0410-compute-types.md)
* [Describe virtual machine options, including Azure virtual machines, Azure Virtual Machine Scale Sets, availability sets, and Azure Virtual Desktop](./0420-vm.md)
* [Describe the resources required for virtual machines](./0430-vm-resources.md)
* [Describe application hosting options, including web apps, containers, and virtual machines](./0440-app-hosting.md)
* [Describe virtual networking, including the purpose of Azure virtual networks, Azure virtual subnets, peering, Azure DNS, Azure VPN Gateway, and ExpressRoute](./0450-network.md)
* [Define public and private endpoints](./0460-endpoints.md)

Describe Azure storage services
* [Compare Azure Storage services](./0510-storage-services.md)
* [Describe storage tiers](./0520-storage-tiers.md)
* [Describe redundancy options](./0530-redundancy.md)
* [Describe storage account options and storage types](./0540-storage-account.md)
* [Identify options for moving files, including AzCopy, Azure Storage Explorer, and Azure File Sync](./0550-file-moving.md)
* [Describe migration options, including Azure Migrate and Azure Data Box](./0560-migration.md)

Describe Azure identity, access, and security
* [Describe directory services in Azure, including Azure Active Directory (Azure AD), part of Microsoft Entra and Azure Active Directory Domain Services (Azure AD DS)](./0610-directory-services.md)
* [Describe authentication methods in Azure, including single sign-on (SSO), multi-factor authentication (MFA), and passwordless](./0620-authentication.md)
* [Describe external identities in Azure, including business-to-business (B2B) and business-to-customer (B2C)](./0630-external-identities.md)
* [Describe Conditional Access in Azure AD](./0640-conditional-access.md)
* [Describe Azure role-based access control (RBAC)](./0650-role-based.md)
* [Describe the concept of Zero Trust](./0660-zero-trust.md)
* [Describe the purpose of the defense-in-depth model](./0670-defense-in-depth.md)
* [Describe the purpose of Microsoft Defender for Cloud](./0680-microsoft-defender.md)

### Describe Azure management and governance (30–35%)

Describe cost management in Azure
* [Describe factors that can affect costs in Azure](./0710-cost-factors.md)
* [Compare the pricing calculator and the Total Cost of Ownership (TCO) Calculator](./0720-pricing-calculator.md)
* [Describe cost management capabilities in Azure](./0730-cost-management.md)
* [Describe the purpose of tags](./0740-tags.md)

Describe features and tools in Azure for governance and compliance

* [Describe the purpose of Microsoft Purview in Azure](./0810-purview.md)
* [Describe the purpose of Azure Policy](./0820-azure-policy.md)
* [Describe the purpose of resource locks](./0830-resource-locks.md)

Describe features and tools for managing and deploying Azure resources

* [Describe the Azure portal](./0910-portal.md)
* [Describe Azure Cloud Shell, including Azure Command-Line Interface (CLI) and Azure PowerShell](./0920-cloud-shell.md)
* [Describe the purpose of Azure Arc](./0930-arc.md)
* [Describe infrastructure as code (IaC)](./0940-iac.md)
* [Describe Azure Resource Manager (ARM) and ARM templates](./0950-arm.md)

Describe monitoring tools in Azure
* [Describe the purpose of Azure Advisor](./1010-advisor.md)
* [Describe Azure Service Health](./1020-service-health.md)
* [Describe Azure Monitor, including Log Analytics, Azure Monitor alerts, and Application Insights](./1030-monitor.md)

## Notes

By default, Azure Account admins only have admin powers on its own subscription. In order to manage other subscriptions and Management Groups, they need to have their access [elevated](https://learn.microsoft.com/en-ca/azure/role-based-access-control/elevate-access-global-admin) to become Global Administrators.

To create another Tenant (Azure Active Directory) you need to have a non-trial subscription. The Azure Portal will allow you to run the wizard to create it but it will return a generic error message. By using Dev Tools it is possible to see the response payload explaining the error but the Azure Portal will not show the message.