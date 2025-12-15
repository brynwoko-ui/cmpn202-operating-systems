# Week 3 – Application Selection for Performance Testing

## 1. Purpose of Application Selection

This phase focuses on selecting representative applications that generate different types of workloads in order to evaluate how the operating system manages resources under varying conditions. By choosing applications that stress specific subsystems (CPU, memory, disk, and network), it is possible to observe scheduling behaviour, memory management, I/O handling, and network performance in a controlled and measurable way.

The selected applications are lightweight, widely documented, and suitable for execution on a headless server within an isolated virtual environment.

---

## 2. Workload Categories

The following workload categories were identified to provide comprehensive operating system coverage:

- CPU-intensive workloads
- Memory-intensive workloads
- Disk I/O-intensive workloads
- Network-intensive workloads
- Server-style service workloads

Each category targets a different aspect of operating system behaviour.

---

## 3. Application Selection Matrix

| Workload Type | Application | Justification |
|--------------|-------------|---------------|
| CPU-intensive | `stress-ng` (CPU workers) | Generates sustained CPU load to analyse scheduling, context switching, and utilisation |
| Memory-intensive | `stress-ng` (VM workers) | Allocates and accesses memory aggressively to observe memory usage and pressure |
| Disk I/O-intensive | `dd` / `fio` | Produces sequential and random disk reads/writes to analyse I/O throughput and latency |
| Network-intensive | `iperf3` | Measures network throughput and latency over TCP |
| Server workload | `nginx` | Lightweight server application suitable for response-time and resource monitoring |

These applications collectively provide a balanced and realistic performance testing environment.

---

## 4. Installation Documentation (SSH-Based)

All applications will be installed on the server via SSH using the package manager.

```bash
sudo apt update
sudo apt install -y stress-ng fio iperf3 nginx
