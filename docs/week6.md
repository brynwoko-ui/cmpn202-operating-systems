# Week 6 – Performance Testing and Analysis

## Objective
The objective of this week was to evaluate system performance under controlled workloads and analyse CPU, memory, and disk behaviour on an Ubuntu Server system.

---

## Test Environment
- Ubuntu Server 22.04 LTS
- VirtualBox virtual machine
- 2 CPU cores
- 2 GB RAM
- 20 GB virtual disk
- NAT networking

---

## Methodology

Performance testing was conducted in two phases:

### 1. Idle Baseline
System metrics were captured while the server was idle using the `sar` tool to establish baseline CPU, memory, and disk activity.

### 2. Load Testing
Controlled workloads were generated using the following tools:
- **stress-ng** for CPU and memory stress testing
- **fio** for disk I/O stress testing

Each test was executed for 120 seconds to ensure consistent and comparable results.

---

## Results Evidence

The following screenshot confirms successful execution of performance tests and data collection:

![Week 6 results files](images/week6-results.png)

---

## Analysis

### CPU Performance
Under CPU stress, processor utilisation increased significantly, with idle time reducing close to zero. This demonstrates effective workload scheduling across available CPU cores.

### Memory Performance
Memory stress testing showed increased memory utilisation while remaining within available physical memory limits. Swap usage remained minimal, indicating sufficient RAM allocation for the workload.

### Disk Performance
Disk I/O testing generated sustained write activity, confirming the system’s ability to handle concurrent disk operations without excessive latency.

---

## Reflection

This exercise demonstrated how operating systems respond to different types of workload pressure. The use of controlled, repeatable tests allowed meaningful comparison between idle and load states, reinforcing the importance of performance monitoring in system administration.
