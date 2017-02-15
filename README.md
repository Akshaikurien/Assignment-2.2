1. HDFS

The storage mechanism OF Hadoop is known as HDFS (Hadoop Distributed File System). It is based on google GFS(Google File System) white paper.
Hadoop is a batch oriented system which can never be plugged behind an online transaction processing system. Moreover, it a write once, ready many times data storage mechanism. This means, you can never update the data. If you really want to update, you need to delete the previous version and upload a new copy.\
NameNode is the master daemon whic is stored in some high end machines.
Data Node is a slave daemon software for the storage part of hadoop whic is stored in commodity machines.

 Advantage of HDFS
 
The file store in HDFS provides scalable, fault-tolerant storage at low cost.
The HDFS software detects and compensates for hardware issues, including disk problems and server failure.
HDFS stores files across the collection of servers in a cluster.
Files are decomposed into blocks and each block is written to more than one of the servers.
The replication provides both fault-tolerance and performance.



2.Hadoop Cluster

A Hadoop cluster is a special type of computational cluster designed specifically for storing and analyzing huge amounts of unstructured data in a distributed computing environment.
Such clusters run Hadoop's open source distributed processing software on low-cost commodity computers. Typically one machine in the cluster is designated as the NameNode and another machine the as JobTracker; these are the masters. The rest of the machines in the cluster act as both DataNode and TaskTracker; these are the slaves. Hadoop clusters are often referred to as "shared nothing" systems because the only thing that is shared between nodes is the network that connects them. 
Hadoop clusters are known for boosting the speed of data analysis applications. They also are highly scalable: If a cluster's processing power is overwhelmed by growing volumes of data, additional cluster nodes can be added to increase throughput. Hadoop clusters also are highly resistant to failure because each piece of data is copied onto other cluster nodes, which ensures that the data is not lost if one node fails.
As of early 2013, Facebook was recognized as having the largest Hadoop cluster in the world. Other prominent users include Google, Yahoo and IBM.


3. HDFS blocks

Hadoop distributed file system also stores the data in terms of blocks. However the block size in HDFS is very large. The default size of HDFS block is 128 MB. The files are split into 64MB blocks and then stored into the hadoop filesystem. The hadoop application is responsible for distributing the data blocks across multiple nodes.In a hardisk,blocks are not necessarily stored continuously.but in 
HDFS locks are stores continuosly for faster access.

Advantages of HDFS Block

The benefits with HDFS block are: 
The blocks are of fixed size, so it is very easy to calculate the number of blocks that can be stored on a disk.
HDFS block concept simplifies the storage of the datanodes. The datanodes doesn’t need to concern about the blocks metadata data like file permissions etc. The namenode maintains the metadata of all the blocks.
If the size of the file is less than the HDFS block size, then the file does not occupy the complete block storage.
As the file is chunked into blocks, it is easy to store a file that is larger than the disk size as the data blocks are distributed and stored on multiple nodes in a hadoop cluster.
Blocks are easy to replicate between the datanodes and thus provide fault tolerance and high availability. Hadoop framework replicates each block across multiple nodes (default replication factor is 3). In case of any node failure or block corruption, the same block can be read from another node.
The main reason for having the HDFS blocks in large size is to reduce the cost of seek time. In general, the seek time is 10ms and disk transfer rate is 100MB/s. To make the seek time 1% of the disk transfer rate, the block size should be 128 MB.
