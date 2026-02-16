**Cluster**
a group of physical servers (hosts) that are connected together and work as one system to run virtual machines

````````````
**In Proxmos**
The Proxmox VE cluster manager **pvecm** is a tool to create a group of physical servers. Such a group is called a cluster. We use the Corosync Cluster Engine for reliable group communication. There’s no explicit limit for the number of nodes in a cluster. In practice, the actual possible node count may be limited by the host and network performance. Currently (2021), there are reports of clusters (using high-end enterprise hardware) with over 50 nodes in production.

``````````
