---
description: ""
title: Cloud store
weight: 2
---

# Cloud store


Cloud store is an abstraction for storage API for various features of daptin like file column storage and site hosting.

Most cloud storage require oauth connection and token to operate.

You can create more stores by creating more rows in the cloud_store table, daptin will take care of syncing it.

Daptin can work with the following storage providrs:

- Amazon Drive  
- Amazon S3  
- Backblaze B2  
- Box  
- Ceph  
- DigitalOcean Spaces  
- Dreamhost  
- Dropbox  
- FTP  
- Google Cloud Storage  
- Google Drive  
- HTTP  
- Hubic  
- Memset Memstore  
- Microsoft Azure Blob Storage  
- Microsoft OneDrive  
- Minio  
- Nextloud  
- OVH  
- Openstack Swift  
- Oracle Cloud Storage  
- Ownloud  
- pCloud  
- put.io  
- QingStor  
- Rackspace Cloud Files  
- SFTP  
- Wasabi  
- WebDAV  
- Yandex Disk  
- The local filesystem  

### Things to keep ready

If the service you want to integrate with requires authentication, create the following:

- An [oauth connection](/feature-manuals/extend/oauth_connection)
- An [oauth token](/feature-manuals/extend/oauth_token) generated from the above connection
