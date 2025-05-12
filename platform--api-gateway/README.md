# API Gateway

The API Gateway serves as the central entry point for all client requests to the Distributed IoT Platform, providing routing, authentication, and request handling capabilities.

## Overview

The API Gateway is a critical component of the Distributed IoT Platform that acts as a unified entry point for all external requests. It routes incoming requests to the appropriate microservices, handles authentication and authorization, and provides additional functionalities like request logging, rate limiting, and response caching.

## Key Features

- **Request Routing**: Directs incoming requests to the appropriate backend services
- **Authentication & Authorization**: Verifies user identity and permissions
- **Request Transformation**: Modifies requests before forwarding to backend services
- **Response Transformation**: Formats responses before returning to clients
- **Load Balancing**: Distributes requests across multiple service instances
- **Logging & Monitoring**: Tracks request/response metrics and logs
- **Rate Limiting**: Prevents abuse by limiting request rates
- **Circuit Breaking**: Prevents cascading failures by detecting and isolating failing services
- **Caching**: Improves performance by caching frequently accessed data

## Architecture

The API Gateway follows a modular architecture with several key components:

- **Request Handler**: Processes incoming HTTP requests
- **Router**: Determines the appropriate backend service for each request
- **Authentication Module**: Verifies user credentials and tokens
- **Transformation Engine**: Modifies requests and responses as needed
- **Logging System**: Records request and response details
- **Kafka Integration**: Communicates with other platform services via Kafka

## Components

### Main Application (`main.py`)

The core API Gateway application that:
- Initializes the gateway server
- Sets up routing rules
- Configures middleware
- Handles incoming requests

### Kafka Handler (`kafkaHandler.py`)

Manages communication with Kafka:
- Produces messages to Kafka topics
- Consumes messages from Kafka topics
- Handles message serialization/deserialization

### Heartbeat Generator (`heartbeatGenerator.py`)

Sends periodic heartbeat messages to the monitoring system:
- Generates heartbeat messages
- Reports gateway health status
- Detects and reports issues

### Logging System (`loggingMessage.py`)

Handles logging of requests and responses:
- Formats log messages
- Sends logs to the centralized logging service
- Provides different log levels for various events

## Configuration

The API Gateway is configured through several files:

- **`config.json`**: Main configuration file with settings for:
  - Server port and host
  - Routing rules
  - Authentication settings
  - Rate limiting parameters
  - Logging configuration

- **`globalVariables.py`**: Shared variables used across the gateway

## API Endpoints

The API Gateway exposes several endpoints for different platform functionalities:

### Authentication Endpoints

- **`POST /auth/login`**: User login
- **`POST /auth/logout`**: User logout
- **`POST /auth/refresh`**: Refresh authentication token

### Application Management Endpoints

- **`GET /apps`**: List all applications
- **`GET /apps/{app_id}`**: Get application details
- **`POST /apps`**: Create a new application
- **`PUT /apps/{app_id}`**: Update an application
- **`DELETE /apps/{app_id}`**: Delete an application

### Deployment Endpoints

- **`POST /apps/{app_id}/deploy`**: Deploy an application
- **`GET /apps/{app_id}/deployments`**: List application deployments
- **`GET /apps/{app_id}/deployments/{deployment_id}`**: Get deployment details

### Monitoring Endpoints

- **`GET /apps/{app_id}/metrics`**: Get application metrics
- **`GET /apps/{app_id}/logs`**: Get application logs
- **`GET /platform/health`**: Get platform health status

### Node Management Endpoints

- **`GET /nodes`**: List all nodes
- **`GET /nodes/{node_id}`**: Get node details
- **`POST /nodes`**: Register a new node
- **`DELETE /nodes/{node_id}`**: Remove a node

### Sensor Management Endpoints

- **`GET /sensors`**: List all sensors
- **`GET /sensors/{sensor_id}`**: Get sensor details
- **`POST /sensors`**: Register a new sensor
- **`DELETE /sensors/{sensor_id}`**: Remove a sensor

## Usage

The API Gateway is typically deployed as a Docker container and can be accessed via HTTP/HTTPS:

```
http://<gateway-host>:<gateway-port>/api/v1/<endpoint>
```

## Dependencies

- Python 3.8+
- Flask/FastAPI
- Kafka client
- JWT for authentication
- Redis (optional, for caching)

## Files Description

- **`main.py`**: Main application entry point
- **`kafkaHandler.py`**: Kafka integration
- **`heartbeatGenerator.py`**: Heartbeat mechanism
- **`loggingMessage.py`**: Logging utilities
- **`config.json`**: Configuration settings
- **`globalVariables.py`**: Shared variables
- **`requirements.txt`**: Python dependencies
