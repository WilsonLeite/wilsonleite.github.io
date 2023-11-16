# Describe the purpose of Microsoft Defender for Cloud

Defender for Cloud is an Azure native monitoring tool for security posture management and threat protection. 

### Cloud security posture management (CSPM)

CSPM provides detailed visibility into the security state of assets and workloads and provides hardening guidance. It supports Azure, AWS, GCP, and on-premises (ARC).

It has two pricing plans:

__Foundational CSPM__

* Security recommendations
* Asset inventory
* Secure score
* Data visualization and reporting with Azure Workbooks
* Data exporting
* Workflow automation
* Tools for remediation
* Microsoft Cloud Security Benchmark

__Defender CSPM__ - The list above plus:

* Security governance
* Regulatory compliance standards
* Cloud security explorer
* Attack path analysis
* Agentless scanning for machines
* Agentless discovery for Kubernetes
* Container registries vulnerability assessment, including registry scanning
* Data aware security posture
* EASM insights in network exposure

<< Review what each of these entries means >>

It provides Continuous Assess giving security benchmarks and recommends security policies based on stardard guidelines.

__Security alerts__

When Defender for Cloud detects a threat in any area of your environment, it generates a security alert. Security alerts:
* Describe details of the affected resources
* Suggest remediation steps
* Provide, in some cases, an option to trigger a logic app in response

__Advanced threat protection__

Available for virtual machines, SQL databases, containers, web applications, and network. It includes port management and allow lists.

### Azure-native protections

* Azure PaaS services: Azure App Service, Azure SQL, Azure Storage Account, and more data services.
* Azure data services: Includes capabilities that automatically classify the data in Azure SQL.
* Networks: Reduces access to VM ports using the just-in-time VM access. Set secure access policies on selected ports, for only authorized users, allowed source IP address ranges or IP addresses, and for a limited amount of time.


__Cloud workload protection__

* Microsoft Defender for Servers
* Microsoft Defender for Containers
* Microsoft Defender for SQL - Azure SQL, SQL Server, MySQL, PostgreSQL, MariaDB, Cosmos DB
* Microsoft Defender for Storage - Add on: Malware Scanning
* Microsoft Defender for App Service
* Microsoft Defender for Key Vault
* Microsoft Defender for Resource Manager

References:

* Microsoft Learn: [Describe Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/training/modules/describe-azure-identity-access-security/9-describe-microsoft-defender-for-cloud)

[Cloud security posture management (CSPM)](https://learn.microsoft.com/en-ca/azure/defender-for-cloud/concept-cloud-security-posture-management)