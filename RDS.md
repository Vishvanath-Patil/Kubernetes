AWS RDS
=======

1. Security and Patching
2. Automated Backup 
3. Software Update for the DB engine
4. if selected, Multi Az's with Synchronous Replication between the active and Standby DB instance.

5. Automatic failiover if Multi Az option was Selected
6. By default Every DB has weekly maintance window ( max 35 days )

Setting Managed by RDS

1) Managing DB Settings 
2) Creating Relational DB Schema
3) Database performance Tuning

 RDS Instance Storage
======================
1. Amazon RDS use EBS Volumes (not instance store ) for DB and logs Storage

1. General Purpose : use for DB workloads with modrate I/o Requirement

limit --> min - 20GB
          max - 16.3 TB

2. Provisional IOPS RDS Storage-
use for high performance OLTP worloads 

limit --> min - 100GB
          max - 16 TB
