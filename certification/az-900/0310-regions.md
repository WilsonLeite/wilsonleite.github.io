## Describe Azure regions, region pairs, and sovereign regions

A region is a geographical area on the planet that contains at least one, but potentially multiple datacenters that are nearby and networked together with a low-latency network. Not all Azure Regions currently support availability zones.

![Azure Region](https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/availability-zones-c22f95a3.png)

Most Azure regions are paired with another region within the same geography (such as US, Europe, or Asia) at least 300 miles away. Services that provide options for region redundancy - like Blob Storage - are replicated to the secondary region associated with the primary region chosen for the service.

![Geo-replication](https://learn.microsoft.com/en-us/azure/storage/common/media/storage-redundancy/geo-redundant-storage.png)

Sovereign regions are instances of Azure that are isolated from the main instance of Azure. They are used for compliance or legal purposes. Ex: DoD, Gov, China

References:

* Microsoft Learn: 
    * [Describe Azure physical infrastructure](https://learn.microsoft.com/en-us/training/modules/describe-core-architectural-components-of-azure/5-describe-azure-physical-infrastructure)
    * [Azure Storage redundancy](https://learn.microsoft.com/en-us/azure/storage/common/storage-redundancy)
* [Azure global infrastructure experience](https://datacenters.microsoft.com/globe/explore/)
