# Describe the purpose of Microsoft Purview in Azure

Microsoft Purview is a data classification tool for risk, compliance, and governance purposes.

* Input connectors: Allow getting data from several kinds of data sources as databases, Azure data storage (blobs, data lake, etc.), Microsoft 365 (OneDrive, SharePoint, etc.), on-premises servers, and even other cloud providers as Amazon S3 buckets.
* Classification engine: Analyses the data on-site (without copying it) searching for regEx patterns and apply labels to it. There are +200 build-in patterns like Social Security Numbers and credit card numbers and allows the creation of custom patterns as well. It also records data lineage - The history of the data as it is copied from a repository to the next.
* Catalog: A centralized repository that stores the metadata collected. It shows the metadata in a normalized way and can also be queried by third-party analytics tools.
* Insights: Provides actionable suggestions
* Policies: Allow the creation of data policies on Microsoft 365 based on the labels. These policies may be about access, deletion, backup, lifetime and purging, etc.

### Risk and compliance solutions

Microsoft 365 (Teams, OneDrive, Exchange, etc.) features as a core component of the Microsoft Purview risk and compliance solutions. Microsoft Purview is able to help on:

* Protect sensitive data across clouds, apps, and devices.
* Identify data risks and manage regulatory compliance requirements.
* Get started with regulatory compliance.

### Unified data governance

* Create an up-to-date map of the entire data estate that includes data classification and end-to-end lineage.
* Identify where sensitive data is stored in the estate.
* Create a secure environment for data consumers to find valuable data.
* Generate insights about how the data is stored and used.
* Manage access to the data in the estate securely and at scale.

References:

* Microsoft Learn: [Describe the purpose of Microsoft Purview](https://learn.microsoft.com/en-us/training/modules/describe-features-tools-azure-for-governance-compliance/2-describe-purpose-microsoft-purview)
