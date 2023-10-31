# Identify options for moving files, including AzCopy, Azure Storage Explorer, and Azure File Sync

## AzCopy

AzCopy is a command-line utility that can be used to copy blobs or files to or from a storage account. It can be use for uploading, downloading and synchronizing data. The synchronization is unidirectional. It can copy files between storage accounts and can even work with other cloud providers to help move files back and forth between clouds.

## Azure Storage Explorer

It is a standalone app that provides a graphical interface to manage files and blobs in a Storage Account. It works on Windows, macOS, and Linux ans uses AzCopy underneath.

## Azure File Sync

It is a tool installed in an on-premises Windows server that bi-directionally synchronizes files stored in an Azure Files instance. It is possible to configure cloud tiering so the most frequently accessed files are replicated locally, while infrequently accessed files are kept in the cloud until requested.

References:

* Microsoft Learn: [Identify Azure file movement options](https://learn.microsoft.com/en-us/training/modules/describe-azure-storage-services/7-identify-azure-file-movement-options)
