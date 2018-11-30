#### Elastic File System (EFS)

A file storage service for EC2 instances. EFS is easy to use and provides a simple interface that allows you to create and configure file systems quickly and easily. With EFS, storage capacity is elastic, growing and shrinking automatically when adding or removing files. Giving just the storage you need, when you need it.

Allows you to share a file system across instances
Single instance of code in EFS served from a file server

- Supports the Network File System Version 4 (NFSv4) protocol
- Pay only for storage used (no pre-provisioning required)
- Can scale up to petabytes
- Can support thousands of concurrent NFS connections
- Data is stored across multiple AZs within a region
- Read after write consistency

