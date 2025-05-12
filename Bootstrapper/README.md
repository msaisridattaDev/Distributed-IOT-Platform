# Bootstrapper

The Bootstrapper is the core initialization component of the Distributed IoT Platform, responsible for orchestrating the deployment of all platform services across the distributed nodes.

## Overview

The Bootstrapper is the first component that runs when setting up the Distributed IoT Platform. It handles the initialization of the entire platform by:

1. Setting up the environment on each node
2. Deploying essential services like Kafka
3. Building and deploying Docker images for all platform components
4. Registering services in the service registry
5. Configuring the network and communication between services

## Architecture

![Bootstrapper Architecture](Bootstrapper.drawio.png)

The Bootstrapper follows a modular architecture with several key components:

- **Main Orchestrator**: Coordinates the overall bootstrapping process
- **Node Setup**: Configures the environment on each node
- **Image Builder**: Builds Docker images for platform services
- **Image Deployer**: Deploys Docker containers across nodes
- **Service Registry**: Registers deployed services for discovery
- **Kafka Handler**: Sets up and manages the Kafka messaging system
- **Database Interaction**: Handles interactions with MongoDB

## Key Components

### Main Orchestrator (`main.py`)

The central controller that orchestrates the entire bootstrapping process. It:
- Initializes the platform configuration
- Coordinates the deployment sequence
- Ensures all dependencies are satisfied before service deployment

### Node Setup (`node_setup.py`, `node_env_setup.sh`)

Responsible for preparing the nodes for deployment:
- Installs required dependencies on each node
- Configures SSH access between nodes
- Sets up Docker and Docker Compose
- Initializes the node environment

### Image Builder (`image_builder.py`)

Handles the building of Docker images:
- Processes service definitions
- Builds Docker images for each platform service
- Tags and prepares images for deployment

### Image Deployer (`image_deployer.py`)

Manages the deployment of containers:
- Distributes containers across nodes based on resource availability
- Configures container networking
- Sets up volume mounts and environment variables
- Starts and monitors containers

### Service Registry (`service_registry.py`)

Maintains a registry of all deployed services:
- Registers service endpoints
- Tracks service health and status
- Provides service discovery capabilities

### Kafka Setup (`redpanda_kafka.py`)

Sets up the Kafka messaging infrastructure:
- Deploys Kafka brokers
- Creates required topics
- Configures message retention and partitioning

### Database Interaction (`db_interaction.py`)

Handles interactions with the MongoDB database:
- Initializes database collections
- Stores platform configuration
- Maintains service and node information

## Configuration

The Bootstrapper uses several configuration files:

- **`.env`**: Environment variables for the bootstrapping process
- **`config_info.py`**: Platform-wide configuration settings
- **`node_info.py`**: Information about available nodes
- **`services_info.py`**: Definitions of platform services
- **`docker-compose.yml`**: Docker Compose configuration for service deployment

## Usage

To start the bootstrapping process:

```bash
# Navigate to the Bootstrapper directory
cd Bootstrapper

# Run the main script
python main.py
```

The bootstrapping process will:
1. Set up the environment on all nodes
2. Deploy Kafka for inter-service communication
3. Build and deploy all platform services
4. Register services in the service registry
5. Initialize the platform database

## Dependencies

- Python 3.8+
- Docker and Docker Compose
- SSH access to all nodes
- MongoDB
- Kafka (Redpanda)

## Files Description

- **`main.py`**: Main orchestration script
- **`node_setup.py`**: Node configuration and setup
- **`node_env_setup.sh`**: Shell script for node environment setup
- **`image_builder.py`**: Docker image building utilities
- **`image_deployer.py`**: Container deployment logic
- **`service_registry.py`**: Service registration and discovery
- **`redpanda_kafka.py`**: Kafka setup and configuration
- **`db_interaction.py`**: Database interaction utilities
- **`blob_handler.py`**: Blob storage interaction
- **`unzipping_file.py`**: File extraction utilities
- **`logger.py`**: Logging configuration
- **`config_info.py`**: Platform configuration
- **`node_info.py`**: Node information
- **`services_info.py`**: Service definitions
- **`global_variables.py`**: Shared variables
- **`Templates/`**: Template files for service configuration
