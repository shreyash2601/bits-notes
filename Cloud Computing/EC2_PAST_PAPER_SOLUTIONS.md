# BITS Pilani WILP — Cloud Computing (CSI/SS/CC ZG527)
# EC-2 (Mid-Semester) Past Paper Deconstructed Solutions
**Exam:** EC-2 Regular (Second Semester) | **Weightage:** 30% | **Max Marks:** 30

---

## 📌 Exam Instructions Reference Check
1. All parts of a question must be answered consecutively.
2. Every sub-question number must be clearly stated.
3. Answers must be specific, crisp, and include mandatory justifications.
4. Assumptions, if any, must be stated clearly at the beginning of the answer.

---

## Question 1 (5 Marks [3 + 2])

> **Question:**  
> Pick any ONE Virtualization technique of your choice, among full virtualization with VMs or software virtualization using containers. State its TWO primary demerits in Cloud Computing with a very brief justification, and how can they be mitigated?

### Model Answer

**Choice of Virtualization Technique:** **Software Virtualization using Containers** *(Note: You can pick either, but Containers is the most straightforward to justify with high marks).*

#### Part (a): Two Primary Demerits with Justifications (3 Marks)

1. **Demerit 1: Weaker Security Isolation / Shared Host Kernel Vulnerability**
   * *Justification:* Unlike Virtual Machines which run isolated guest kernels on hardware-level hypervisors, all containers running on a host share the single underlying Linux kernel. If an application inside a container triggers a kernel privilege-escalation vulnerability (e.g., Dirty COW or container escape), an attacker can compromise the host OS and all other co-located containers.

2. **Demerit 2: Operating System / Kernel Lock-In (Lack of Heterogeneity)**
   * *Justification:* A container does not bundle an operating system kernel; it relies directly on the host kernel's system calls. Consequently, a Linux host cannot natively run Windows kernel containers, and a Windows host cannot natively run Linux containers without spinning up an underlying VM layer (like WSL2).

#### Part (b): Mitigation Strategies (2 Marks)

1. **Mitigation for Shared Kernel Vulnerability:**
   * **Deploy Sandboxed / Micro-VM Runtimes:** Run untrusted containers using lightweight micro-VM container runtimes such as **Kata Containers**, **AWS Firecracker**, or user-space application kernels like **Google gVisor**.
   * **Enforce Least Privilege:** Run container processes as **non-root users** (`USER appuser`), enable user namespaces (`userns-remap`), and drop unnecessary Linux kernel capabilities using **Seccomp** and **AppArmor** profiles.

2. **Mitigation for OS Lock-In:**
   * In multi-cloud or hybrid environments, deploy **heterogeneous worker node pools** in your orchestration cluster (e.g., dedicated Linux node pools for Linux containers and dedicated Windows Server node pools for Windows containers in Kubernetes/AKS/EKS).

---

## Question 2 (5 Marks)

> **Question:**  
> Write a Dockerfile to create an image for a web application that requires a specific version of Node.js (14.16.1) and a custom dependency (express 4.16.2). The image should be based on the official Ubuntu 22.04 image, have a working directory at `/app`, and copy the `package.json` file into the working directory. After installing the dependencies, copy the remaining application code into the working directory and expose port 3232. You need not write any docker commands to build the image or to run the container.  
> **Output:** A Dockerfile that generates the desired image when built.

### Model Answer

```dockerfile
# -------------------------------------------------------------
# Base Image: Official Ubuntu 22.04 as specified
# -------------------------------------------------------------
FROM ubuntu:22.04

# Prevent interactive prompts during apt installations
ENV DEBIAN_FRONTEND=noninteractive

# -------------------------------------------------------------
# Install Node.js 14.16.1 and required build dependencies
# Clean package cache in the same RUN layer to keep image small
# -------------------------------------------------------------
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    ca-certificates \
    && curl -fsSL https://deb.nodesource.com/setup_14.x | bash - \
    && apt-get install -y nodejs=14.16.1* \
    && rm -rf /var/lib/apt/lists/*

# -------------------------------------------------------------
# Set working directory to /app
# -------------------------------------------------------------
WORKDIR /app

# -------------------------------------------------------------
# Layer Caching Best Practice: Copy package.json FIRST
# -------------------------------------------------------------
COPY package.json ./

# -------------------------------------------------------------
# Install specific version of Express dependency (4.16.2)
# -------------------------------------------------------------
RUN npm install express@4.16.2

# -------------------------------------------------------------
# Copy remaining application code into working directory
# -------------------------------------------------------------
COPY . .

# -------------------------------------------------------------
# Expose the specified application port
# -------------------------------------------------------------
EXPOSE 3232

# Default command to start the application
CMD ["node", "index.js"]
```

#### Why Evaluators Award Full Marks for This Solution:
* **Base Image Correct:** Uses `FROM ubuntu:22.04` (not `:latest`).
* **Non-Interactive Flag:** Includes `DEBIAN_FRONTEND=noninteractive` to prevent hung builds during `apt-get`.
* **Exact Versions Pinned:** Explicitly specifies `nodejs=14.16.1` and `express@4.16.2`.
* **Build Cache Preservation:** Accurately places `COPY package.json ./` and `npm install` **before** `COPY . .`.
* **Exposed Port:** Accurately declares `EXPOSE 3232`.

---

## Question 3 (5 Marks [3 + 2])

> **Question:**  
> A multi-specialty hospital is planning to modernize its Hospital Information System (HIS). The management is evaluating two alternative cloud-based architectures:  
> • **Architecture A:** A system primarily built using SaaS solutions for electronic health records, billing, and appointment scheduling, with minimal customization.  
> • **Architecture B:** A system that combines PaaS-based custom application development with IaaS-hosted virtual machines for legacy clinical and diagnostic applications.  
> 
> a) Compare Architecture A and Architecture B in terms of scalability, customization, and operational control.  
> b) Identify scenarios in which Architecture A would be preferred over Architecture B, and vice versa, with justification.

### Model Answer

#### Part (a): Comparative Analysis (3 Marks)

| Evaluation Parameter | Architecture A (SaaS-Driven) | Architecture B (PaaS + IaaS Hybrid) |
| :--- | :--- | :--- |
| **1. Scalability** | **Elastic & Fully Provider-Managed:** Scales instantly on demand without hospital IT intervention. The SaaS provider absorbs sudden surges in patient registrations and billing. | **Configurable but Operationally Demanding:** PaaS auto-scales application layers automatically, but IaaS legacy VMs require manual capacity provisioning or custom Auto Scaling Groups. |
| **2. Customization** | **Low / Rigid:** Limited to vendor-provided workflows, configurable fields, and standardized UI. Custom medical routines or unique workflows cannot be coded into the system. | **High / Flexible:** The PaaS layer enables development of tailored patient portals, while IaaS VMs allow custom OS configurations, proprietary diagnostic drivers, and custom middleware. |
| **3. Operational Control** | **Minimal:** Hospital IT has zero control over the underlying OS, database indexes, network isolation, or patch cycles. Dependent completely on the SaaS vendor’s roadmap. | **Maximum:** Hospital retains full root access over IaaS VMs, controls database schemas, firewall rules, and determines exact maintenance windows without external dependency. |

#### Part (b): Preferred Scenarios with Justification (2 Marks)

1. **When Architecture A (SaaS) is Preferred:**
   * **Scenario:** Setting up standard outpatient consultation clinics, rapid greenfield branch expansion, or administrative billing where fast time-to-market is needed with **zero in-house IT infrastructure staff**.
   * *Justification:* SaaS eliminates the capital expenditure and ongoing operational overhead of patching operating systems, securing databases, and managing server hardware, allowing the hospital to focus 100% on healthcare delivery.

2. **When Architecture B (PaaS + IaaS) is Preferred:**
   * **Scenario:** A large tertiary care research hospital operating proprietary legacy diagnostic equipment (e.g., specialized MRI/CT image processors using legacy DICOM protocols) and custom clinical research pipelines.
   * *Justification:* Legacy diagnostic machines require direct low-level OS driver support, raw socket network access, and specialized software that cannot run on off-the-shelf SaaS. IaaS VMs provide the exact legacy OS environment needed, while PaaS allows developers to rapidly build modern integration APIs around it.

---

## Question 4 (6 Marks [2 + 2 + 2])

> **Question:**  
> A global retailer subscribes to a cloud-based ERP system accessed via a browser for inventory management. At the same time, its IT team uses Azure virtual machines to host custom applications. Identify the service models for these TWO given situations and the deployment model overall. Justify your answer. Without justification no marks.

### Model Answer

#### 1. First Service Model: Cloud-Based ERP System (2 Marks)
* **Identified Service Model:** **Software as a Service (SaaS)**
* **Justification:**
  * The ERP application is fully hosted, maintained, and operated by a third-party cloud software vendor.
  * The retailer’s end-users access it directly via a web browser without purchasing, installing, or managing any underlying hardware, operating system, database, or application code.
  * The retailer only manages user access and configuration settings.

#### 2. Second Service Model: Azure Virtual Machines (2 Marks)
* **Identified Service Model:** **Infrastructure as a Service (IaaS)**
* **Justification:**
  * Microsoft Azure provides raw, virtualized compute resources (vCPU, RAM, block storage, and virtual network adapters).
  * The retailer's IT team possesses administrative/root privileges over the virtual machines and is fully responsible for selecting, installing, and maintaining the operating system, runtime libraries, security patches, firewall configurations, and custom application code.

#### 3. Overall Deployment Model (2 Marks)
* **Identified Deployment Model:** **Hybrid Cloud** *(or Multi-Service Public Cloud Enterprise Integration)*
* **Justification:**
  * The global retailer integrates an external third-party public SaaS application (for standardized ERP inventory management) with cloud-hosted virtual infrastructure (Azure IaaS for proprietary business logic), while typically synchronizing inventory data with physical on-premise retail store point-of-sale (POS) systems.
  * Combining distinct cloud models and interconnecting them via secure APIs and dedicated VPNs constitutes a **Hybrid Cloud** deployment architecture.

---

## Question 5 (4 Marks [2 + 2])

> **Question:**  
> What role do Docker volumes play for container restarts? How do they impact the overall portability and efficiency when multiple Docker containers are deployed in a production environment?

### Model Answer

#### 1. Role of Docker Volumes in Container Restarts (2 Marks)
* **Persistence Across Container Lifecycles:**  
  By default, a container’s writable layer is ephemeral; any files written inside the container are tied to its specific lifecycle and are permanently lost if the container is removed (`docker rm`).
* **Survival During Restarts & Crashes:**  
  Docker volumes reside completely outside the container's Union File System (UnionFS) on the host filesystem (typically at `/var/lib/docker/volumes/<volume_name>/_data`). 
  * When a container stops, crashes, or is restarted (`docker restart` or `docker stop` followed by `docker start`), the data in the volume is entirely unharmed.
  * If a container is completely destroyed and replaced with an upgraded image version, the existing volume can be instantly re-attached to the new container, ensuring zero data loss for stateful applications (like PostgreSQL or MySQL).

#### 2. Impact on Portability and Efficiency in Production (2 Marks)
* **Portability:**
  * **Decoupling Data from Compute:** Volumes abstract the host storage path. A container image contains only immutable application code and libraries, making it 100% portable across developer laptops, staging servers, and production clouds.
  * **Managed Lifecycle:** Named volumes are managed natively via the Docker API (`docker volume create/inspect`), making storage configuration reproducible across different environments without depending on specific host directory path structures.
* **Production Efficiency:**
  * **Bypassing the Storage Driver (Native Disk I/O Performance):** Writing to a container’s standard writable layer requires the Copy-on-Write (CoW) storage driver (e.g., `overlay2`), which incurs CPU and I/O latency overhead. Docker volumes write directly to the host filesystem at native disk speed, maximizing throughput for database workloads.
  * **Data Sharing Between Multiple Containers:** A single named volume can be mounted concurrently by multiple containers (e.g., multiple web workers reading shared static media or an application container writing logs while a log-forwarder container streams them).

---

## Question 6 (5 Marks)

> **Question:**  
> A company may expand private cloud capacity by 20 units, but expansion costs Rs.1,800 (fixed).  
> • Private unit cost even after expansion remains Rs.100  
> • Current private capacity = 40 units  
> • Public cloud cost = Rs.240 per unit  
> • Budget = Rs.10,000 (includes expansion if chosen)  
> 
> **Question:**  
> Should the company expand private capacity to maximize total demand served? Justify by showing appropriate calculations.

### Model Answer

#### 1. Problem Formulation
The goal is to determine whether expanding private cloud capacity results in a higher **Total Demand Served** under the fixed budget constraint of **Rs. 10,000**.

$$\text{Total Demand Served} = \text{Private Units Utilized} + \text{Public Cloud Units Purchased}$$

---

#### 2. Calculation for Option A: DO NOT EXPAND Private Capacity

* **Step 1: Calculate Private Cloud Expenditure**
  * Current Private Capacity = $40 \text{ units}$
  * Private Cost per Unit = $\text{Rs. } 100$
  * Cost of Private Capacity = $40 \times 100 = \mathbf{\text{Rs. } 4,000}$

* **Step 2: Calculate Remaining Budget for Public Cloud**
  * Remaining Budget = $\text{Total Budget} - \text{Private Spend}$
  * Remaining Budget = $\text{Rs. } 10,000 - \text{Rs. } 4,000 = \mathbf{\text{Rs. } 6,000}$

* **Step 3: Calculate Public Cloud Units Purchased**
  * Public Cloud Cost per Unit = $\text{Rs. } 240$
  * Public Units Purchased = $\frac{\text{Rs. } 6,000}{\text{Rs. } 240} = \mathbf{25 \text{ units}}$

* **Step 4: Calculate Total Demand Served (Option A)**
  $$\text{Total Units}_{\text{Option A}} = 40 \text{ (Private)} + 25 \text{ (Public)} = \mathbf{65 \text{ units}}$$

---

#### 3. Calculation for Option B: EXPAND Private Capacity

* **Step 1: Calculate New Private Capacity and Fixed Cost**
  * New Private Capacity = $40 + 20 = \mathbf{60 \text{ units}}$
  * Fixed Expansion Cost = $\mathbf{\text{Rs. } 1,800}$

* **Step 2: Calculate Variable Cost of Private Capacity**
  * Private Unit Cost = $\text{Rs. } 100$
  * Cost of Running 60 Private Units = $60 \times 100 = \mathbf{\text{Rs. } 6,000}$

* **Step 3: Calculate Total Private Spend**
  * Total Private Spend = $\text{Fixed Cost} + \text{Variable Cost}$
  * Total Private Spend = $\text{Rs. } 1,800 + \text{Rs. } 6,000 = \mathbf{\text{Rs. } 7,800}$

* **Step 4: Calculate Remaining Budget for Public Cloud**
  * Remaining Budget = $\text{Rs. } 10,000 - \text{Rs. } 7,800 = \mathbf{\text{Rs. } 2,200}$

* **Step 5: Calculate Public Cloud Units Purchased**
  * Public Cloud Cost per Unit = $\text{Rs. } 240$
  * Public Units Purchased = $\frac{\text{Rs. } 2,200}{\text{Rs. } 240} = \mathbf{9.167 \text{ units}}$

* **Step 6: Calculate Total Demand Served (Option B)**
  $$\text{Total Units}_{\text{Option B}} = 60 \text{ (Private)} + 9.167 \text{ (Public)} = \mathbf{69.167 \text{ units}}$$

---

#### 4. Final Decision & Justification

| Metric | Option A: Do Not Expand | Option B: Expand Capacity | Difference / Gain |
| :--- | :--- | :--- | :--- |
| **Private Units** | 40 units | 60 units | +20 units |
| **Fixed Cost** | Rs. 0 | Rs. 1,800 | +Rs. 1,800 |
| **Private Usage Cost** | Rs. 4,000 | Rs. 6,000 | +Rs. 2,000 |
| **Public Units Purchased** | 25 units | 9.167 units | -15.833 units |
| **TOTAL DEMAND SERVED** | **65.0 units** | **69.167 units** | **+4.167 units** |

**Conclusion:**  
**YES, the company should expand its private capacity.**  
**Justification:** Expanding private cloud capacity yields a total demand served of **69.167 units** compared to **65.0 units** without expansion. Even after paying the upfront fixed expansion cost of Rs. 1,800, the company serves **4.167 additional units (+6.4% higher demand)** under the identical Rs. 10,000 budget.
