# Node Manager

The Node Manager is responsible for managing and monitoring the distributed nodes in the IoT Platform, handling resource allocation, node health monitoring, and load balancing.

## Overview

The Node Manager is a critical component of the Distributed IoT Platform that oversees the management of all nodes in the system. It tracks node health, manages resource allocation, and works closely with the Load Balancer to distribute workloads efficiently across the available nodes.

## Key Features

- **Node Registration**: Handles the registration of new nodes to the platform
- **Resource Monitoring**: Tracks CPU, memory, disk, and network usage of each node
- **Health Checking**: Performs regular health checks on all nodes
- **Resource Allocation**: Manages the allocation of resources to applications
- **Node Selection**: Selects appropriate nodes for application deployment
- **Load Distribution**: Works with the Load Balancer to distribute workloads
- **Fault Detection**: Identifies node failures and issues
- **Node Recovery**: Initiates recovery procedures for failed nodes

## Architecture

The Node Manager follows a modular architecture with several key components:

- **Node Registry**: Maintains information about all registered nodes
- **Resource Monitor**: Tracks resource utilization on each node
- **Health Checker**: Performs regular health checks
- **Resource Allocator**: Manages resource allocation
- **Node Selector**: Selects nodes for deployment
- **Kafka Integration**: Communicates with other platform services

## Components

### Node Registry

Maintains a comprehensive registry of all nodes in the platform:
- Node identification (ID, name, IP)
- Node capabilities (CPU, memory, disk)
- Node status (online, offline, maintenance)
- Deployed applications and services

### Resource Monitor

Continuously monitors resource utilization on each node:
- CPU usage tracking
- Memory usage tracking
- Disk space monitoring
- Network bandwidth monitoring
- Container resource usage

### Health Checker

Performs regular health checks on all nodes:
- Connectivity checks
- Service availability checks
- Resource threshold monitoring
- Performance metrics collection

### Resource Allocator

Manages the allocation of resources to applications:
- Resource reservation
- Resource quota enforcement
- Resource optimization
- Overcommitment management

### Node Selector

Selects appropriate nodes for application deployment:
- Resource-based selection
- Affinity/anti-affinity rules
- Geographical distribution
- Load balancing considerations

## Workflow

1. **Node Registration**:
   - New nodes register with the Node Manager
   - Node capabilities and resources are recorded
   - Initial health check is performed

2. **Continuous Monitoring**:
   - Regular health checks are performed on all nodes
   - Resource utilization is monitored
   - Metrics are collected and stored

3. **Deployment Support**:
   - When a deployment request is received, suitable nodes are selected
   - Resources are allocated for the deployment
   - Node selection information is provided to the Deployer

4. **Load Balancing**:
   - Works with the Load Balancer to distribute traffic
   - Provides node health and load information
   - Suggests optimal traffic distribution

5. **Fault Handling**:
   - Detects node failures or issues
   - Initiates recovery procedures
   - Coordinates with Monitoring & Fault Tolerance service

## API Endpoints

The Node Manager exposes several internal API endpoints:

### Node Management

- **`GET /nodes`**: List all registered nodes
- **`GET /nodes/{node_id}`**: Get node details
- **`POST /nodes`**: Register a new node
- **`PUT /nodes/{node_id}`**: Update node information
- **`DELETE /nodes/{node_id}`**: Deregister a node

### Resource Management

- **`GET /nodes/{node_id}/resources`**: Get node resource information
- **`GET /nodes/{node_id}/utilization`**: Get current resource utilization
- **`POST /nodes/{node_id}/allocate`**: Allocate resources on a node
- **`POST /nodes/{node_id}/deallocate`**: Deallocate resources on a node

### Health Management

- **`GET /nodes/{node_id}/health`**: Get node health status
- **`POST /nodes/{node_id}/health/check`**: Trigger a health check
- **`PUT /nodes/{node_id}/status`**: Update node status

### Deployment Support

- **`POST /deployment/node-selection`**: Select nodes for deployment
- **`GET /deployment/{deployment_id}/nodes`**: Get nodes for a deployment

## Configuration

The Node Manager is configured through several files:

- **`config.json`**: Main configuration file with settings for:
  - Server port and host
  - Monitoring intervals
  - Resource thresholds
  - Health check parameters

- **`node_types.json`**: Definitions of different node types and their capabilities

## Integration with Other Components

The Node Manager integrates with several other platform components:

- **Deployer**: Provides node selection for application deployment
- **Load Balancer**: Shares node health and load information
- **Monitoring & Fault Tolerance**: Coordinates on node health monitoring
- **Scheduler**: Provides resource information for scheduling decisions
- **API Gateway**: Exposes node management APIs

## Dependencies

- Python 3.8+
- Docker API client
- Kafka client
- Prometheus client (for metrics)
- SSH client (for node management)

## Files Description

- **`main.py`**: Main application entry point
- **`node_registry.py`**: Node registration and management
- **`resource_monitor.py`**: Resource monitoring functionality
- **`health_checker.py`**: Health checking implementation
- **`resource_allocator.py`**: Resource allocation logic
- **`node_selector.py`**: Node selection algorithms
- **`kafka_handler.py`**: Kafka integration
- **`config.json`**: Configuration settings
- **`node_types.json`**: Node type definitions
