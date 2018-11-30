### Databases

Relational Databases (RDS) - Online Transaction Processing (OLTP)
- SQL Server
- Oracle
- MySQL
- PostgreSQL
- Amazon Aurora
  - Performant
  - Redundancy
- MariaDB

NoSQL DB
- DynamoDB

Data Warehouse - OLAP
- Amazon Redshift

In Memory
- Elasticache

#### Redshift - Data Warehousing
Used for Business Intelligence
- Used to pull in very large and complex data sets to do queries
- OLAP
- Single Node (160GB)
- Multi-Node
  - Leader Node - manages client connections and receives queries
  - Compute Nodes - store data and perform queries and computations
    - Upto 128 Compute Nodes
- Columnar Data Storage - data stored in columns instead of rows
  - Better performance
- Massively Parallel Processing (MPP)
  - Automatically distributes data and query loads across all nodes.
  - Makes it easy to add nodes to your data warehouse and enables you to maintain fast query performance
- Pricing
  - Compute node hours
    - Not Leader Nodes
  - Backup
- Data transfer (only with a VPC, not outside it)
- Security
  - Encrypted in transit using SSL
  - Encrypted at rest using AES-256
  - Key management managed by AWS by default
    - Can manage own keys through Hardware Security Modules (HSM)
    - AWS Key Management Service
- Availability
  - Only available in 1 AZ
  - Can restore snapshots to new AZ's in the event of an outage
- Good choice if DB is stressed because management is running OLAP transactions on the main DB server

#### Elasticache
Web service for deploying in-memory cache in the cloud. The service improves performance of web applications by allowing you to retrieve information from fast, managed, in-memory caches, instead of relying on slower disk-based databases.

Caching improves application performance by storing critical pieces fo data in memory for low-latency access. Cached information may include the results of I/O-intensive database queries of the results of computationally intensive calculatesions.

Supports 2 open-source in-memory caching engines:
- Memcached
  - Widly adopted memory object caching system
- Redis
  - Popular open-source in-memory key-value store that supports data structures such as sorted sets and lists. 
  - Elasticache supports Master/Slave replication and multi-AZ which can be used for cross AZ redundancy
- Great choice if DB is read-heavy and not prone to frequent changes

### Troubleshooting
- EC2 instances may have trouble connecting due to security groups
  - RDS SGs should allow inbound port 3306 traffic from EC2 SGs

### Backups
#### Automated Backups
- Allow you to recover your database to a point in time within a "retention period". Teh retention period is between 1-35 days.
- Take a full daily snapshot and store transaction logs throughout the day. When you recover AWS will first select the most recent daily backup, then apply transaction logs for that day. Allows for a point in time recivery to a second, within the retention period.
- Enabled by default
- Backup data stored on S3, with free storage space equal to size of database
- Backups are taken within a defined window.
- During backcup, storage I/O may be suspended and my experience elevated latency.
- Deleted with deletion of RDS instance

#### Database Snapshots
- Manual
- Stored even after deleting original RDS instance

#### Restoring a Backup
- Restored database will be a new RDS instance with a new DNS endpoint

### Encryption
Encryption at rest is supported for MySQL, Oracle, SQL Server, PostgreSQL, MariaDB & Aurora.

- Done using the AWS Key Management Service (KMS) 
- Once encrypted, data stored at rest in the underlying storage is encrypted, includeing automated backups, read replicas, and snapshots.
- Currently, encryption of existing DB instances is not supported
  - Workaround: Create a snapshot, create a copy of the snapshot, encrypt the copy

### Multiple-AZ
- Uses DNS name to point to an exact copy of DB in seperate AZ
- Exact copy is replicated to other AZ synchronously
- AWS handles replication
- Disaster Recovery only
  - For performance use _Read Replicas_
- Available for:
  - MySQL
    - Aurora, by default
  - SQL Server
  - Oracle
  - PostgreSQL
  - MariaDB

### Read Replica
- 5 read replicas per database
- Can have read replicas of read replicas (potential latency issues)
- Each RR will have its own DNS endpoint
- Can have RR that have multi-AZ
- Can create RR of Multi-AZ source databases
- RR can be promoted to be their own databases. This breaks replication
- RR can be in another region
- Scaling option for read-heavy database workloads
  - Not for Disaster Recovery
- Read-only copy of database
- Asynchronous replication from primary RDS to read replica
- Must have automatic backups enabled to create a read replica
- Available for:
  - MySQL
  - PostgreSQL
  - MariaDB
  - Aurora

### DynamoDB

Fast and flexible NoSQL database service for all applications
- Consistent
- Single-digit latency at any scale
- Fully managed
- "Push Button" Scaling
- Supports document and key-value data models
- Stored on SSD storage
- Spread across 3 geographic distict data centers
- Eventual Consistent Reads (Default)
  - Consistency across all copies of data is usually within a second. Repeating a read after a short time should return the updated data (Best Read Performance)
- Strongly Consistent Reads
  - Returns a result that reflects all writes that received a successful response prior to the read.
    - i.e. do you need data that was written immediatly?
  - Pricing:
    - Write $0.0065 per hour for every 10 units
    - Read $0.0065 per hour for every 50 units
    - Storage $0.25 per GB per month

### Aurora
- MySQL compatible
- Relational DB engine
- Combines speed and availability fo high-end commercial databases with simplicity and cost-effectivebess of open source databases
- Upto 5 times better performance than MySQL
- 1/10th the cost of a commerical database with similar performance and availablility
- Not available in all regions
- Scaling
  - Auto scales
  - Starts at 10GB, scales in 10GB increments upto 64TB (Storage Autoscaling)
  - Compute resources can scale to 32 vCPUs and 244GB of RAM
  - 2 copies of data in each AZ, with a minimum of 3 AZs, 6 copies of data
  - Can transparently handle loss of up to 2 copies of data without affecting write and upto 3 copies without affecting read
  - Self-healing. Data blocks and disks are continuously scanned for errors and repaired automatically
- Replicas
  - Aurora Replicas, upto 15
    - Will automatically failover to
  - MySQL Replicas, upto 5
    - Will NOT automatically failover to