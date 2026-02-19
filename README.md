**Vm Migration**
The process of moving a running or stopped virtual machine from one physical host or environment to another, usually with little or no downtime.

# Types of migration
1. **Live Migration**:
- VM keeps running while it moves
- Users usually don’t notice anything
- Used for maintenance, load balancing, high availability
- Common in platforms like VMware vMotion, Microsoft Hyper-V Live Migration, and KVM

2. **Cold Migration**
- VM is powered off before moving
- Simpler, but causes downtime
- Often used during upgrades or major changes

3. **Storage Migration**
- VM stays on the same Host 
- Only the VM’s disk/storage moves (e.g., to faster storage)

4. **Cloud migration/cross-platform**
- Moving VMs between environments (on-prem → cloud, cloud → cloud)
- Example: on-prem to Amazon Web Services, Microsoft Azure, or Google Cloud

**Migration is done for :**
1. Hardware maintenance without downtime
2. Load balancing / performance optimization
3. Disaster recovery
4. Cost optimization
5. Data center or cloud modernization

**Cluster**
a group of physical servers (hosts) that are connected together and work as one system to run virtual machines

-----
**In Proxmos**
The Proxmox VE cluster manager **pvecm** is a tool to create a group of physical servers. Such a group is called a cluster. We use the Corosync Cluster Engine for reliable group communication. There’s no explicit limit for the number of nodes in a cluster. In practice, the actual possible node count may be limited by the host and network performance. Currently (2021), there are reports of clusters (using high-end enterprise hardware) with over 50 nodes in production.
-----

**what is **ZFS** File System**

