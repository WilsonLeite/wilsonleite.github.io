## Describe storage account options and storage types

A storage account provides a unique namespace for your Azure Storage data that is accessible from anywhere in the world over HTTP or HTTPS. It is associated to a unique namespace in Azure, so it must have an unique name in Azure as well. The endpoints will be composed using this namespace and a fixed part related to each service:
* Blob Storage:	https://{storage-account-name}.blob.core.windows.net
* Data Lake Storage Gen2: https://{storage-account-name}.dfs.core.windows.net
* Azure Files: https://{storage-account-name}.file.core.windows.net
* Queue Storage: https://{storage-account-name}.queue.core.windows.net
* Table Storage: https://{storage-account-name}.table.core.windows.net

### Storage types

Standard general-purpose v2

* Redundancy Options: LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS
* Blob Storage (including Data Lake Storage)
* Queue Storage
* Table Storage
* Azure Files

Premium block blobs

* Redundancy Options: LRS, ZRS
* Blob Storage (including Data Lake Storage)

Premium file shares	

* Redundancy Options: LRS, ZRS
* Azure Files

Premium page blobs

* Redundancy Options: LRS
* Page blobs only

References:

* Microsoft Learn: [Describe Azure storage accounts](https://learn.microsoft.com/en-us/training/modules/describe-azure-storage-services/2-accounts)
