# Go Distributed System

This project demonstrates how to implement a simple distributed system using **Go**. It includes a master-worker architecture with secure communication between nodes using **gRPC**.

## Overview

The project involves:
- A **Master Node** to assign tasks and control the system.
- **Worker Nodes** to execute tasks based on commands received from the master.

## Features (Initial Scope)
- Task assignment from the master to workers.
- Worker status reporting to the master.

## Technologies Used
- **Go**: Programming language.
- **gRPC**: Framework for secure inter-node communication.
- **Protocol Buffers**: Interface definition language for gRPC.

## Getting Started

### Prerequisites
1. Install [Go](https://go.dev/) (v1.17 or later).
2. Install `protoc` (Protocol Buffers compiler). Refer to the [official guide](https://grpc.io/docs/protoc-installation/).

### Initial Setup
1. Initialize the project:
   ```bash
   git clone https://github.com/yourusername/go-distributed-system.git
   cd go-distributed-system
   go mod download
