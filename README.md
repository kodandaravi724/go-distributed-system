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


## How to Run

### Start the Master Node
In the first terminal, run:
```bash
go run main.go master
```

Expected output:
```
[GIN-debug] POST   /tasks                    --> go-distributed-system/core.(*MasterNode).Init.func1 (3 handlers)
[GIN-debug] Listening and serving HTTP on :9092
```

### Start a Worker Node
In a second terminal, run:
```bash
go run main.go worker
```

Expected output:
```
worker node started
```

---

## Example: Assign a Task

1. With the master node running, open a third terminal.
2. Execute the following API call to assign a task:
```bash
curl -X POST -H "Content-Type: application/json" -d '{"cmd": "touch /tmp/hello-distributed-system"}' http://localhost:9092/tasks
```

3. Check the worker node terminal. You should see:
```
received command: touch /tmp/hello-distributed-system
```

4. Verify task execution:
```bash
ls -l /tmp/hello-distributed-system
```

Expected output:
```
-rw-r--r--  1 user  group     0B Dec  6 10:22 /tmp/hello-distributed-system
```

---


## Project Structure

```
.
├── core
│   ├── node.proto             # Protocol Buffers file
│   ├── node.pb.go             # Generated Protocol Buffers Go file
│   ├── node_grpc.pb.go        # Generated gRPC Go file
│   ├── node_service_server.go # Server-side implementation
│   ├── worker_node.go         # Worker node implementation
│   └── master_node.go         # Master node implementation
├── main.go                    # Main entry point
├── go.mod                     # Go module dependencies
└── README.md                  # Project documentation
```

---

## Libraries Used

1. [gRPC](https://grpc.io/)
2. [Protocol Buffers](https://developers.google.com/protocol-buffers)
3. [Gin](https://gin-gonic.com/)
4. Go's built-in libraries: `os/exec`, `context`, `net`.

---

## Future Improvements

1. Add health checks for worker nodes.
2. Implement distributed logging.
3. Introduce authentication for secure communication.
