# What do I know about Ceph
1. [Component](#component)
## Components
---
### Terminology
- OSD
    - Ceph Object Storage Daemon
    - Object Storage Device: physical or logical storage unit (LUN)

### Storage Clients
1. Ceph Block Device
2. Ceph Object Stroage
3. Ceph File System
4. Custom implementaion using librados

### Storage Cluster

1. Ceph Monitors (Mon)
    - maintain cluster map
    - cluster of Mon ensure high availability
    - client retrieve a copy of cluster map from Mon
2. Ceph OSD Daemon (OSD)
    - check own state + other OSDs status
    - report the statuses back to monitor
3. Ceph Managers (Mgr)
    - (???) Endpoint of monitoring, orchestration and plug-in modules
4. Ceph Metadata Server (MDS)
    - manage file metadata when CephFS is used to provide file services

### Storing Data
1. Data from Ceph Client are stored as RADOS objects
2. Each object is stored on an Object storage Device (OSD)
3. OSD Daemon handle read, write and replication operation on storage drive
4. Store data as objects in a flat namespace (no hierarchy of directories)
5. An object has an identifier, binary data, and metadata consisting of a set of name/value pairs

> An object id is unique in global sense

### Scalability and high availability
Ceph eliminates the centralized gateway to enable clients to interact with Ceph OSD Daemons directly. Ceph OSD Daemons create object replicas on other Ceph Nodes to ensure data safety and high availability. Ceph also uses a cluster of monitors to ensure high availability. To eliminate centralization, Ceph uses an algorithm called CRUSH.
