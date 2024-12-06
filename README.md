# Distributed System in Go

## Overview

This project demonstrates a simple distributed system written in Go. It includes:

- **Master Node:** Acts as the control system to assign tasks.
- **Worker Node:** Executes tasks assigned by the master.
- **gRPC Protocol:** For efficient and secure communication between master and worker nodes.
- **API Interface:** Enables external task submissions to the master node.

The project uses **gRPC**, **Protocol Buffers**, and **Go Channels** to implement a lightweight distributed system architecture.

---

## Features

1. **Node Communication:**
   - gRPC-based communication between master and worker nodes.
2. **Task Assignment:**
   - Master node assigns tasks to worker nodes using Server-Side Streaming RPC.
3. **Status Reporting:**
   - Worker nodes periodically report their status to the master node using Simple RPC.
4. **Task Execution:**
   - Worker nodes execute commands sent from the master node.

---

## Prerequisites

1. **Go (>= 1.23)** installed.
2. **gRPC tools:** Install `protoc` for Protocol Buffers compilation ([gRPC Installation Guide](https://grpc.io/docs/protoc-installation/)).
3. **curl** for testing API endpoints.

---

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/kodandaravi724/go-distributed-system.git
cd go-distributed-system
```

### 2. Install Dependencies
```bash
go mod download
```

### 3. Compile Protocol Buffers
```bash
protoc --go_out=./core --go-grpc_out=./core core/node.proto
```

---