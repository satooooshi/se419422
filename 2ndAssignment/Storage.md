# SE419 / SE422 1st Assignment
**Name:** 会川慧 / Aikawa Satoshi / Huichuan Hui

**ID:** 516413990003

**Team members:** HOKHY TANN, 董宇涛

**Topic:** Storage ( ceph ) 

**Date:** October 2018 


---------------------------------------------------------------------- 
# Technical Report : Storage ( ceph )
0. What is Ceph
1. Vendors or types or technologies
1. Key indicators
1. My comment
1. references
## ZERO. What is Ceph
> In computing, Ceph (pronounced /ˈsɛf/ or /ˈkɛf/) is a free-software storage platform, implements object storage on a single distributed computer cluster, and provides interfaces for object-, block- and file-level storage. Ceph aims primarily for completely distributed operation without a single point of failure, scalable to the exabyte level, and freely available.

## 1. Vendors or types or technologies

Generally server vendors love Ceph because it lets them sell servers as enterprise storage, without needing to develop and maintain complex storage software. The drive makers (of both spinners and SSDs) want to love Ceph because it turns their drive components into a storage system. It also lowers the cost of the software and controller components of storage, leaving more money to spend on drives and flash.

###   1. Feature

| Feature      | meaning.. |
| ----------- | ----------- |
| Open Source      | No license fees,Different hardware for different workloads  |Software-defined	|
| Software-defined   | Use commodity hardware, Manage many nodes as one system|
|Scale-out|Distributed capacity,Distributed performance|
| Block + Object      | Store more types of data, Data protection, Self-healing       |
| Enterprise features   | Data efficiency, Caching/tiering       |

Ceph employs four distinct kinds of daemons:

- Cluster monitors (ceph-mon) that keep track of active and failed cluster nodes
- Metadata servers (ceph-mds) that store the metadata of inodes and directories
- Object storage devices (ceph-osd) that uses a direct, journaled disk storage (named BlueStore,[since the v12.x release) or store the content of files in a filesystem (preferably XFS, the storage is named Filestore).
- Representational state transfer (RESTful) gateways (ceph-rgw) that expose the object storage layer as an interface compatible with Amazon S3 or OpenStack Swift APIs
All of these are fully distributed, and may run on the same set of servers. Clients directly interact with all of them.

Ceph does striping of individual files across multiple nodes to achieve higher throughput, similar to how RAID0 stripes partitions across multiple hard drives. Adaptive load balancing is supported whereby frequently accessed objects are replicated over more nodes. As of September 2017, BlueStore is the default and recommended storage type for production environments, which is Ceph's own storage implementation providing better latency and configurability than the filestore backend, and avoiding the shortcomings of the filesystem based storage involving additional processing and caching layers. The Filestore backend is still considered useful and very stable; XFS is the recommended underlying filesystem type for production environments, while Btrfs is recommended for non-production environments. ext4 filesystems are not recommended because of resulting limitations on the maximum RADOS objects length.



### 2. Pros&Cons
Probably the most notable feature of Ceph is that it does not rely on central metadata service to locate data. It uses CRUSH algorithm to calculate location of data.
The drawback of this approach is that cluster topology changes lead to data movement to maintain CRUSH contracts.

### 3. Key indicators

Applications such as "Application Performance Monitoring - ManageEngine Applications Manager" also provides information about the health, availability and storage capacity of Ceph clusters. View details like health severity, latency time checks and monitor rank details etc, to determine if the admin server is down, and to transfer control to the next in line.

## 3. My comment
Ceph can be a hot storage solution, however seen from the description mentioned above, Ceph isn’t perfect for everyone. It’s not the most efficient at using flash or CPU (but it’s getting better), the file storage feature isn’t fully mature yet, and it is missing key efficiency features like deduplication and compression. And some customers just aren’t comfortable with open-source or software-defined storage of any kind. But every release of Ceph adds new features and improved performance, while system integrators build turnkey Ceph appliances that make it easy to deploy and come with integrated hardware and software support.

## 4. References
1. [https://www.quora.com/What-are-the-advantages-of-using-ceph](https://www.quora.com/What-are-the-advantages-of-using-ceph)

2. [分散ストレージ ソフトウェア Ceph（セフ）とは](http://www.fujitsu.com/jp/products/computing/storage/lib-f/tech/beginner/ceph/)

3. [http://www.mellanox.com/blog/2015/06/ceph-is-a-hot-storage-solution-but-why/](http://www.mellanox.com/blog/2015/06/ceph-is-a-hot-storage-solution-but-why/)
