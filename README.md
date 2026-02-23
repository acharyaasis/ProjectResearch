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
(Zettabyte file system) a modern, advanced file system + volume manager designed to keep data safe, consistent, and easy to manage—even at huge scale.

**why it is special**
-> ZFS uses checksums on all data.
- Every block is verified when read
- If corruption is detected, ZFS automatically repairs it (when redundancy exists)
- This protects against bit rot, silent corruption, bad RAM, flaky disks

**Note:file system and volume manager in one**


**GPU passthrough**
-> method that allows a virtual machine to use physical GPU on the host directely instead of relaing on the virtualized graphics.
- the VM sees the GPU as if it owns it exclusively.
- great for the high perfomance graphics, gaming, AI, or GPU computing.

- **Use Cases**
- AI/ Machine Learning(Tensorflow)
- Video editing / 3D Rendering 
- Gaming Vm's 

**REST API in Proxmos**
- Api uses HTTPS protocol and the server listens to port 8006

*Parameters can be passed using standard HTTP techniques:*
- via the URL
- using x-www-form-urlencoded content-type for PUT and POST request.

**Return formats can be used**
- json: JSON
- extjs: JSON, but result nested inside an object, with data object, variant compatible with ExtJS forms
- html: HTML formatted text - sometimes useful for debugging
- text: plain text - sometimes useful for debugging

**Authentication**
-> uses a ticket or token based authentication,
-> all request to the API need to include a ticket inside a Cookie (header) or sending an API token through the Authorization header.

**Ticket Cookie**
-> A ticket is a signed random text value with the user and creation time included. Tickets are signed by the cluster-wide authentication key that is rotated once per day.
-> any write (POST/PUT/DELETE) request must include a CSRF prevention token inside the HTTP header.

**Example: Get a New Ticket and the CSRF Prevention Token Using Curl**
*Request - warning, command line parameters are visible to the whole system, avoid running below on untrusted hosts:*
curl -k -d 'username=root@pam' --data-urlencode 'password=xxxxxxxx' https://10.0.0.1:8006/api2/json/access/ticket

*Safer variant with the password in a file only readable for the user:*
curl -k -d 'username=root@pam' --data-urlencode "password@$HOME/.pve-pass-file" https://10.0.0.1:8006/api2/json/access/ticket

**Api Tokens**
-> API tokens allow stateless access to most parts of the REST API by another system, software or API client. Tokens can be generated for individual users and can be given separate permissions and expiration dates to limit the scope and duration of the access. Should the API token get compromised it can be revoked without disabling the user itself.
- To use an API token, set the HTTP Authorization header value to the form of PVEAPIToken=USER@REALM!TOKENID=UUID when making API requests, or refer to your API client documentation.
