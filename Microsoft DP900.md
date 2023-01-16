### SQL statement types

Data Definition Language (DDL)

Data Control Language (DCL)

Data Manipulation Language (DML)

### Azure Blob Storage 

A service that enables you to store massive amounts of unstructured data as binary large objects, or blobs, in the cloud. 

#### Blobs 

An efficient way to store data files in a format that is optimized for cloud-based storage, and applications can read and write them by using the Azure blob storage API.

#### Block blobs

handled as a set of blocks. Each block can vary in size, up to 100 MB. A block blob can contain up to 50,000 blocks, giving a maximum size of over 4.7 TB. The block is the smallest amount of data that can be read or written as an individual unit. Block blobs are best used to store discrete, large, binary objects that change infrequently.
#### Page blobs

organized as a collection of fixed size 512-byte pages. A page blob is optimized to support random read and write operations; you can fetch and store data for a single page if necessary. A page blob can hold up to 8 TB of data. Azure uses page blobs to implement virtual disk storage for virtual machines.

#### Append blobs

A block blob optimized to support append operations. You can only add blocks to the end of an append blob; updating or deleting existing blocks isn't supported. Each block can vary in size, up to 4 MB. The maximum size of an append blob is just over 195 GB.

#### Blob storage provides three access tiers, which help to balance access latency and storage cost:

##### The Hot tier （default）

You use this tier for blobs that are accessed frequently. The blob data is stored on high-performance media.

##### The Cool tier 

has lower performance and incurs reduced storage charges compared to the Hot tier. Use the Cool tier for data that is accessed infrequently. It's common for newly created blobs to be accessed frequently initially, but less so as time passes. In these situations, you can create the blob in the Hot tier, but migrate it to the Cool tier later. You can migrate a blob from the Cool tier back to the Hot tier.

##### The Archive tier

provides the lowest storage cost, but with increased latency. The Archive tier is intended for historical data that mustn't be lost, but is required only rarely. Blobs in the Archive tier are effectively stored in an offline state. Typical reading latency for the Hot and Cool tiers is a few milliseconds, but for the Archive tier, it can take hours for the data to become available. To retrieve a blob from the Archive tier, you must change the access tier to Hot or Cool. The blob will then be rehydrated. You can read the blob only when the rehydration process is complete.

Azure File Storage offers two performance tiers. The Standard tier uses hard disk-based hardware in a datacenter, and the Premium tier uses solid-state disks. The Premium tier offers greater throughput, but is charged at a higher rate.

### Azure Files 

#### supports two common network file sharing protocols:

##### Server Message Block (SMB) file sharing 

commonly used across multiple operating systems (Windows, Linux, macOS).

##### Network File System (NFS) shares 

used by some Linux and macOS versions. To create an NFS share, you must use a premium tier storage account and create and configure a virtual network through which access to the share can be controlled.

#### Azure File Storage offers two performance tiers. 

##### The Standard tier 

uses hard disk-based hardware in a datacenter

##### the Premium tier 

uses solid-state disks
offers greater throughput, but is charged at a higher rate.

### Azure Table Storage 

a NoSQL storage solution that makes use of tables containing key/value data items. 
Each item is represented by a row that contains columns for the data fields that need to be stored.

### Batch and stream processing

### Real-time analytics in Azure
Microsoft Azure supports multiple technologies that you can use to implement real-time analytics of streaming data, including:

##### Azure Stream Analytics: 
A platform-as-a-service (PaaS) solution that you can use to define streaming jobs that ingest data from a streaming source, apply a perpetual query, and write the results to an output.

##### Spark Structured Streaming: 
An open-source library that enables you to develop complex streaming solutions on Apache Spark based services, including Azure Synapse Analytics, Azure Databricks, and Azure HDInsight.

##### Azure Data Explorer: A high-performance database and analytics service that is optimized for ingesting and querying batch or streaming data with a time-series element, and which can be used as a standalone Azure service or as an Azure Synapse Data Explorer runtime in an Azure Synapse Analytics workspace.


#### Sources for stream processing

##### Azure Event Hubs: 
A data ingestion service that you can use to manage queues of event data, ensuring that each event is processed in order, exactly once.

##### Azure IoT Hub: 
A data ingestion service that is similar to Azure Event Hubs, but which is optimized for managing event data from Internet-of-things (IoT) devices.

##### Azure Data Lake Store Gen 2: 
A highly scalable storage service that is often used in batch processing scenarios, but which can also be used as a source of streaming data.

##### Apache Kafka: 
An open-source data ingestion solution that is commonly used together with Apache Spark. You can use Azure HDInsight to create a Kafka cluster.
