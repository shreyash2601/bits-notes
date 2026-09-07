# Lecture 5: Infrastructure as a Service (IaaS) Deep Dive — Compute, Networking, Storage & Databases

**Course:** Cloud Computing (CCZG527 / CSIZG527 / SEZG527 / SSZG527 - BITS Pilani WILP)  
**Instructor:** Prof. Arun Vadekkedhil  
**Contact Session / Module:** Session 5: IaaS Deep Dive — EC2, VPC, Storage Triad, Databases & Zomato Case Study  
**Core Theme:** Comprehensive architectural decomposition of core IaaS primitives across AWS and Azure—virtual compute lifecycles and placement topologies, isolated software-defined networking, the storage triad (Block, Object, File), managed relational databases, and real-world hyperscale optimization (The Zomato Case Study).

---

## 1. The Big Picture (Why Should I Care?)

- **What is this lecture about?**  
  This lecture connects virtualization theory to production cloud engineering across AWS and Azure. It covers the core IaaS building blocks: Compute (EC2 / Azure VMs), Networking (VPC / VNet), the Storage Triad (Block vs. Object vs. File), Managed Relational Databases (Multi-AZ Standby vs. Read Replicas), and examines how companies like Zomato scale to billions of events per week.
- **The Real-World Problem:**  
  On New Year's Eve, food delivery order volume surges 1,800% in 45 minutes. A legacy un-decoupled architecture collapses: synchronous writes bottleneck a single database, disk IOPS run dry, web server pools freeze, and an on-call reboot causes the public IP to change dynamically, severing all client traffic. Meanwhile, customer audit logs stored on ephemeral disks are permanently wiped when auto-scaling terminates worker nodes. Modern cloud systems prevent this through asynchronous event buffering (Kafka), decoupled storage (EBS/S3), private subnet routing, and Multi-AZ database replication.
- **Where this fits in the course:**  
  Following the virtualization foundations (Sessions 1–4), this session serves as the comprehensive production deep-dive into IaaS cloud infrastructure.

---

## 2. Core Concepts Explained Simply

### Concept 1: Compute Architecture: Sizing, Families & Machine Images

- **What is it?**  
  Virtual machine instances running on bare-metal hypervisors (**AWS Nitro** $\leftrightarrow$ **Azure Hyper-V**), categorized into distinct workload families:
  1. **General Purpose:** Balanced compute, memory, and networking (`t4g`, `m6g` in AWS $\leftrightarrow$ `B-series`, `Dpsv5` in Azure).
  2. **Compute Optimized:** High vCPU-to-RAM ratio; tailored for batch processing, proxies, and web servers (`c6g` $\leftrightarrow$ `Fsv2`).
  3. **Memory Optimized:** High RAM-to-vCPU ratio; essential for in-memory databases and caches like Redis (`r6g` $\leftrightarrow$ `Epsv5`, `Esv5`).
  4. **Storage Optimized:** Direct-attached NVMe storage delivering millions of low-latency IOPS (`i3en` $\leftrightarrow$ `Lsv3`).
  5. **Accelerated Computing:** Dedicated GPU/ASIC hardware for AI/ML model training and graphics (`p4d`, `g5` $\leftrightarrow$ `NCv3`, `NDv4`).
- **Machine Images (AMIs $\leftrightarrow$ Azure Compute Gallery):**  
  Immutable virtual disk blueprints containing the operating system, initial packages, and configuration scripts used to stamp out identical VMs.
- **Tech Quick-Primer:**
  > 💡 **Tech Quick-Primer (`AWS Graviton / Azure Ampere Altra`):** 64-bit ARM-based server processors engineered by cloud hyperscalers to deliver up to 40%–50% better price-performance compared to traditional x86 chips for Linux workloads.

---

### Concept 2: Compute Lifecycles & Placement Topologies

- **The Virtual Machine Lifecycle:**  
  `Pending` $\to$ `Running` $\to$ `Stopping` $\to$ `Stopped / Deallocated` $\to$ `Terminated`.
- **Reboot vs. Stop/Start (Crucial Operational Trap):**
  * **Reboot:** The VM stays on the same physical server blade; private and public IP addresses remain unchanged.
  * **Stop / Deallocate:** Compute billing halts. When started again, the cloud scheduler places the VM on an entirely **new physical host blade, and its public IPv4 address changes dynamically** (unless bound to an **AWS Elastic IP** $\leftrightarrow$ **Azure Static Public IP**).
- **Physical Placement Topologies:**
  * **Cluster Placement Group (AWS) $\leftrightarrow$ Azure Proximity Placement Group (PPG):** Packs VMs tightly into the same physical datacenter rack for ultra-low network latency (100 Gbps). Used for HPC and distributed AI training.
  * **Spread Placement Group (AWS) $\leftrightarrow$ Azure Availability Sets (Fault Domains):** Strictly places each VM on distinct physical hardware racks with independent power and networking to prevent simultaneous hardware failure.
  * **Partition Placement Group (AWS) $\leftrightarrow$ Azure Fault Domains:** Spreads VMs across logical partitions; used for distributed databases like Kafka and Cassandra.
- **Ephemeral Storage vs. Persistent Block Storage:**
  * **Instance Store (Ephemeral):** Raw NVMe SSD physically attached to the server host chassis (**AWS Instance Store** $\leftrightarrow$ **Azure Temp Disk `/dev/sdb`**). **Data is permanently erased when the instance is stopped or deallocated.**
  * **Network Block Storage (Persistent):** Network-attached virtual disks (**Amazon EBS** $\leftrightarrow$ **Azure Managed Disks**). Data persists indefinitely across reboots, stops, and migrations.

---

### Concept 3: Software-Defined Networking: AWS VPC $\leftrightarrow$ Azure VNet

- **What is it?**  
  A logically isolated software-defined private network dedicated to your cloud account (**AWS Virtual Private Cloud [VPC]** $\leftrightarrow$ **Azure Virtual Network [VNet]**).
- **Core Networking Components:**
  * **CIDR Block:** Private IPv4 address allocation (e.g., `10.0.0.0/16`, providing 65,536 private IPs).
  * **Subnets:** Segmenting the network across physical Availability Zones:
    * *Public Subnet:* Connected to an **Internet Gateway (IGW)**; instances have public IPs for incoming internet traffic (e.g., Load Balancers, Bastion hosts).
    * *Private Subnet:* Has zero direct inbound internet routes; instances only have private IPs (e.g., Application backends, Databases).
  * **NAT Gateway:** Allows private-subnet backend instances to initiate outbound requests (for OS security updates or external API calls) while blocking the outside internet from initiating inbound connections.

---

### Concept 4: Dual-Layer Perimeter Defense: Security Groups vs. NACLs

- **What is it?**  
  The two-tier virtual firewall model protecting cloud instances and subnets:
  1. **Security Groups (Stateful - Instance Level):**  
     * Operates at the virtual network interface (vNIC) of each individual VM.  
     * **Stateful:** If an inbound request is permitted (e.g., port 443 HTTPS), the outbound response traffic is automatically allowed regardless of outbound rules.  
     * *Azure Equivalent:* **Network Security Groups (NSGs) applied to Network Interfaces**.
  2. **Network Access Control Lists - NACLs (Stateless - Subnet Level):**  
     * Operates as a security barrier at the subnet boundary.  
     * **Stateless:** Inbound and outbound traffic must be explicitly allowed independently. If port 443 is allowed inbound, you must explicitly open ephemeral return ports (1024–65535) outbound.  
     * *Azure Equivalent:* **Azure Subnet-level NSGs / Azure Firewall**.

---

### Concept 5: The Cloud Storage Triad: Block vs. Object vs. File

| Dimension | Block Storage | Object Storage | File Storage |
| :--- | :--- | :--- | :--- |
| **AWS Service** | **Amazon EBS** | **Amazon S3** | **Amazon EFS** |
| **Azure Service** | **Azure Managed Disks** | **Azure Blob Storage** | **Azure Files** |
| **Data Format** | Raw physical disk sectors / blocks | Unstructured objects + metadata | Hierarchical files & folders |
| **Access Protocol** | Fibre Channel, iSCSI, NVMe | HTTP / HTTPS REST APIs | NFS v4 (Linux) / SMB 3.0 (Windows) |
| **Tenancy / Attachment**| Bound 1:1 to a single VM in same AZ | Globally accessible via HTTP URLs | Shared across hundreds of VMs simultaneously |
| **Best For** | Boot disks, transactional DB files | Videos, backups, images, data lakes | Shared application configs, CMS media |

---

### Concept 6: Managed Databases: Amazon RDS Multi-AZ $\leftrightarrow$ Azure Flexible Server

- **What is it?**  
  Fully managed relational database engines (PostgreSQL, MySQL) that automate provisioning, OS patching, backups, and point-in-time recovery.
- **Multi-AZ Standby vs. Read Replicas (Crucial Distinction):**
  * **Multi-AZ Synchronous Standby (High Availability):**  
    * Replicates database writes **synchronously** at the block level to an idle standby instance in a second physical Availability Zone.  
    * The standby cannot be used for read traffic.  
    * If the primary AZ fails, the DNS endpoint automatically fails over to the standby in **under 60 seconds with 0 data loss**.
  * **Read Replicas (Performance & Scale):**  
    * Replicates data **asynchronously** to up to 5–15 read-only database instances.  
    * Used to offload heavy `SELECT` query traffic from the primary instance.  
    * Does **not** offer automated zero-data-loss failover (asynchronous replication lag introduces data loss risk).

---

### Concept 7: Hyperscale Architecture: The Zomato Case Study

- **The Architecture:**  
  India's leading food delivery unicorn, **Zomato**, processes **20 billion events per week** by applying these exact IaaS primitives:
  1. *Decoupled Streaming:* Order placement is ingested asynchronously through **Apache Kafka**, preventing surge traffic from overwhelming the primary database.
  2. *ARM Graviton Spot Fleets:* Worker compute fleets run on 64-bit ARM Spot instances (**AWS Graviton2** $\leftrightarrow$ **Azure Ampere Altra**), cutting infrastructure compute costs by **30%**.
  3. *Multi-Tier VPC Isolation:* Public ALB $\to$ Private ECS/EKS Container Workers $\to$ Private Multi-AZ RDS Cluster.
  4. *Immutable Object Archival:* Delivery telemetry and order receipts are immediately offloaded from ephemeral worker disks to Amazon S3 / Azure Blob Storage.

---

## 3. Visual Architecture Models

### 3-Tier Multi-AZ VPC / VNet & RDS High Availability

```mermaid
flowchart TD
    subgraph Internet["Public Internet"]
        Users["Global Mobile & Web Clients"]
    end

    subgraph Cloud["Virtual Private Network (AWS VPC / Azure VNet: 10.0.0.0/16)"]
        IGW["Internet Gateway"]
        Users --> IGW
        
        subgraph PublicSubnets["Public Subnets (DMZ)"]
            ALB["Application Load Balancer (Multi-AZ)"]
            NAT["NAT Gateway (Outbound Updates Only)"]
            IGW --> ALB
        end

        subgraph PrivateSubnets["Private Subnets (Zero Inbound Internet)"]
            direction TB
            subgraph AZ_A["Availability Zone A"]
                AppA["Container / VM Fleet A"]
                DB_Pri["Primary Managed DB (Read/Write)"]
            end
            
            subgraph AZ_B["Availability Zone B"]
                AppB["Container / VM Fleet B"]
                DB_Stby["Synchronous Standby DB (Failover Only)"]
                DB_Replica["Async Read Replica (Read Traffic)"]
            end
            
            ALB --> AppA & AppB
            AppA & AppB --> NAT
            AppA & AppB --> DB_Pri
            AppA & AppB -.->|"Read Queries"| DB_Replica
            DB_Pri ==="Synchronous Block Replication"=== DB_Stby
            DB_Pri -.->|"Asynchronous Log Replication"| DB_Replica
        end
    end
```

### Diagram Walkthrough:
* **DMZ vs. Private Isolation:** Traffic hits the public Application Load Balancer in the public subnet. Backend application containers and databases live in private subnets with zero inbound internet routing.
* **Synchronous vs. Asynchronous Database Tier:** The primary database writes synchronously to the standby in AZ-B for automated failover (High Availability), while read queries are offloaded asynchronously to Read Replicas (Scalability).

---

## 4. Key Comparisons & Trade-Offs

### Security Groups vs. Network ACLs (NACLs)

| Feature | Security Group (AWS) / NSG (Azure) | Network ACL (NACL) / Azure Subnet NSG |
| :--- | :--- | :--- |
| **Operates At** | Virtual Network Interface (Instance Level) | Subnet Boundary Level |
| **State Nature** | **Stateful** (Return traffic allowed automatically) | **Stateless** (Inbound & outbound evaluated separately) |
| **Rule Types** | **ALLOW rules only** (Default deny) | **ALLOW and DENY rules** |
| **Rule Order** | Evaluates all rules before making a decision | Evaluates rules in numbered order (First match wins) |

### Dual-Cloud (AWS $\leftrightarrow$ Azure) IaaS Rosetta Stone

| Cloud Primitive | Amazon Web Services (AWS) | Microsoft Azure | Architecture Function |
| :--- | :--- | :--- | :--- |
| **ARM Compute** | AWS Graviton2 / Graviton3 | Azure Ampere Altra (Dpsv5) | Energy-efficient 64-bit ARM compute (-30% cost) |
| **Ephemeral Disk** | EC2 Instance Store | Azure Temp Disk (`/dev/sdb`) | Blazing fast NVMe scratchpad; wiped on stop/deallocate |
| **Persistent Disk** | Amazon EBS (gp3 / io2) | Azure Managed Disks (Premium/Ultra) | Network-attached virtual drive that persists independently |
| **Object Storage** | Amazon S3 | Azure Blob Storage | Scalable HTTP REST object storage for media/backups |
| **Shared Files** | Amazon EFS | Azure Files | Managed NFS/SMB file system mounted across multiple VMs |
| **Virtual Network**| Amazon VPC | Azure Virtual Network (VNet) | Isolated software-defined private cloud network |
| **Outbound NAT** | AWS NAT Gateway | Azure NAT Gateway | Enables private instances to reach the internet safely |
| **High-Avail DB** | Amazon RDS Multi-AZ | Azure DB Flexible Server Zone-Redundant | Synchronous standby replication with auto-failover |

---

## 5. Professor's Practical Takeaways & Golden Rules

*(Key insights emphasized by Prof. Arun Vadekkedhil in lecture)*

1. **The Stop/Start Public IP Trap:**  
   Rebooting a cloud VM preserves its public IPv4 address. But **stopping and starting a VM schedules it on a new physical blade, changing its public IP**. Never configure external clients to connect to a default public IP; always bind an Elastic IP (AWS) or Static Public IP (Azure).
2. **Never Put Persistent Data on Instance Store / Temp Disks:**  
   Instance Store and Azure Temp Disks are physical NVMe drives on the server blade. They are meant strictly for swap space, caches, or temporary processing. The moment a VM is stopped or resized, all data on that drive is **permanently destroyed**.
3. **Multi-AZ Standby is NOT for Read Scaling:**  
   An RDS Multi-AZ standby instance does not accept read queries; it sits idle waiting for a primary hardware failure. If your application needs read scalability, launch asynchronous **Read Replicas**.
4. **The Zomato Cost Lesson:**  
   Never run standard x86 on-demand instances 24/7 for stateless batch workers. Migrating to ARM silicon (Graviton / Ampere Altra) and Spot instances immediately cuts compute costs by 30% to 70%.

---

## 6. Quick Recap & Terminology Cheatsheet

### Key Terms in 1 Line
* **AMI / Compute Gallery:** Pre-baked immutable machine images containing the OS and application runtime.
* **Elastic IP / Static IP:** Persistent public IPv4 address that does not change when an instance is stopped and restarted.
* **Instance Store / Temp Disk:** Ephemeral scratchpad storage physically tied to the host chassis; data is wiped on deallocation.
* **EBS / Managed Disk:** Persistent network-attached block storage volume bound to a VM.
* **S3 / Blob Storage:** Globally accessible, highly durable HTTP REST object storage for unstructured data.
* **VPC / VNet:** Isolated software-defined private cloud network with user-defined CIDR blocks and subnets.
* **Security Group:** Stateful virtual firewall applied at the VM network interface level.
* **NACL:** Stateless virtual firewall applied at the subnet boundary level.
* **Multi-AZ Standby:** Synchronous cross-datacenter database replication with automated sub-minute failover.
* **Read Replica:** Asynchronous read-only database copy used to offload `SELECT` traffic.

### 4 Core Mental Rules to Remember
1. **Decouple Compute from Storage:** Treat compute instances as disposable; store persistent state on EBS/Disks or S3/Blob.
2. **Stateful Security Groups, Stateless NACLs:** Security Groups auto-allow return traffic; NACLs require opening explicit return ports.
3. **Multi-AZ for Uptime, Read Replicas for Scale:** Multi-AZ provides automated failover; Read Replicas offload query volume.
4. **Protect Private Subnets with NAT:** Backends and databases belong in private subnets, reaching the internet only via NAT Gateways.
