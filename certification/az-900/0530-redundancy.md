## Describe redundancy options

### LRS - Locally redundant storage

Replicates the data three times within a single data center and provides at least 11 nines of durability (99.999999999%) of objects over a given year.

### ZRS - Zone-redundant storage

Replicates the data synchronously across three Azure availability zones. and provides at least 12 nines of durability (99.9999999999%). However, there is only one copy per availability zone.

### GRS - Geo-redundant storage

On top of LRS, it copies the data _asynchronously_ to a single physical location in the secondary region (the region pair) using LRS there. In this case, there will be three copies of the data in the primary region and eventually three more copies in the secondary region. 16 nines (99.99999999999999%).

The recovery point objective (RPO) - the copy delay - is typically less than 15 minutes, but there is no SLA for that.

### GZRS - Geo-zone-redundant storage

It is the ZRS equivalent of of GRS. The primary region will have one copy in each of three availability zones and the Secondary region will eventually have three copies in the same datacenter. Also 16 nines (99.99999999999999%).

### RA-GRS and RA-GZRS - Read-only access in the secondary region

When using GRS and GZRS, the data in the secondary region is not accessible until Microsoft or the customer initiate a failover from the primary to secondary region.

The RA-* options allows the data to be always available. However, note that it can be outdated as it is copies asynchronously.

References:

* Microsoft Learn: [Describe Azure storage redundancy](https://learn.microsoft.com/en-us/training/modules/describe-azure-storage-services/3-redundancy)
