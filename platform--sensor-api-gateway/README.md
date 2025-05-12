# Sensor API Gateway

The Sensor API Gateway is a specialized gateway component of the Distributed IoT Platform that provides a unified entry point for all sensor-related interactions.

## Overview

The Sensor API Gateway serves as a dedicated entry point for all sensor-related interactions in the Distributed IoT Platform. It routes sensor data and commands between external systems/devices and the platform's internal components, particularly the Sensor Manager. This component provides protocol translation, security, and other gateway functionalities specifically tailored for IoT sensor interactions.

## Key Features

- **Sensor Data Ingestion**: Receives data from IoT sensors
- **Command Routing**: Routes commands to sensors
- **Protocol Translation**: Supports multiple IoT protocols
- **Security**: Implements authentication and authorization for sensors
- **Rate Limiting**: Controls data ingestion rates
- **Data Validation**: Validates incoming sensor data
- **Sensor Discovery**: Supports sensor discovery mechanisms
- **Load Balancing**: Distributes sensor traffic
- **Caching**: Caches sensor data and responses
- **Monitoring**: Tracks sensor connectivity and data flow

## Architecture

The Sensor API Gateway follows a modular architecture with several key components:

- **Request Handler**: Processes incoming requests
- **Protocol Adapters**: Supports various IoT protocols
- **Authentication Module**: Verifies sensor identity
- **Routing Engine**: Routes requests to appropriate services
- **Data Validator**: Validates sensor data
- **Rate Limiter**: Controls request rates
- **Caching Layer**: Caches responses
- **Monitoring Module**: Tracks gateway health
- **Kafka Integration**: Communicates with other platform services

## Components

### Request Handler

Processes incoming requests:
- Receives sensor data and commands
- Parses request formats
- Extracts request parameters
- Prepares requests for processing
- Formats responses

### Protocol Adapters

Supports various IoT protocols:
- MQTT adapter
- CoAP adapter
- HTTP/REST adapter
- WebSocket adapter
- Custom protocol adapters

### Authentication Module

Verifies sensor identity:
- Sensor authentication
- API key validation
- Token verification
- Certificate validation
- Authentication policies

### Routing Engine

Routes requests to appropriate services:
- Request classification
- Service selection
- Load balancing
- Failover handling
- Request tracking

### Data Validator

Validates sensor data:
- Format validation
- Schema validation
- Range checking
- Anomaly detection
- Data quality assessment

### Rate Limiter

Controls request rates:
- Rate limit policies
- Quota management
- Throttling
- Burst handling
- Rate monitoring

### Caching Layer

Caches responses:
- Response caching
- Cache invalidation
- Time-to-live management
- Cache size control
- Cache statistics

### Monitoring Module

Tracks gateway health:
- Performance monitoring
- Error tracking
- Traffic statistics
- Resource utilization
- Health reporting

## Workflow

1. **Request Reception**:
   - Sensor request is received
   - Protocol is identified
   - Request is parsed
   - Initial validation is performed

2. **Authentication & Authorization**:
   - Sensor identity is verified
   - Access permissions are checked
   - Rate limits are applied
   - Request is authorized

3. **Request Processing**:
   - Request is validated
   - Request is transformed if needed
   - Routing decision is made
   - Cache is checked for response

4. **Request Routing**:
   - Request is routed to Sensor Manager
   - Request tracking is initiated
   - Timeout monitoring is started
   - Load balancing is applied

5. **Response Handling**:
   - Response is received
   - Response is transformed if needed
   - Response is cached if applicable
   - Response is returned to sensor

## API Endpoints

The Sensor API Gateway exposes several API endpoints:

### Sensor Data

- **`POST /sensors/{sensor_id}/data`**: Submit sensor data
- **`GET /sensors/{sensor_id}/data/latest`**: Get latest sensor data
- **`GET /sensors/{sensor_id}/data/history`**: Get historical sensor data

### Sensor Commands

- **`POST /sensors/{sensor_id}/commands`**: Send command to sensor
- **`GET /sensors/{sensor_id}/commands/history`**: Get command history
- **`GET /sensors/{sensor_id}/commands/{command_id}/status`**: Get command status

### Sensor Management

- **`POST /sensors`**: Register a new sensor
- **`GET /sensors`**: Discover available sensors
- **`GET /sensors/{sensor_id}`**: Get sensor details
- **`PUT /sensors/{sensor_id}`**: Update sensor information
- **`DELETE /sensors/{sensor_id}`**: Deregister a sensor

### Gateway Management

- **`GET /health`**: Get gateway health
- **`GET /metrics`**: Get gateway metrics
- **`GET /protocols`**: List supported protocols

## Protocol Support

The Sensor API Gateway supports multiple protocols:

1. **MQTT**:
   - Topic structure: `sensors/{sensor_id}/data`
   - QoS levels: 0, 1, 2
   - Retained messages
   - Last Will and Testament

2. **CoAP**:
   - Resource structure: `/sensors/{sensor_id}/data`
   - Observe option
   - Block-wise transfers
   - Resource discovery

3. **HTTP/REST**:
   - RESTful API endpoints
   - JSON and XML formats
   - Query parameters
   - HTTP status codes

4. **WebSocket**:
   - Persistent connections
   - Bi-directional communication
   - JSON message format
   - Ping/pong mechanism

## Configuration

The Sensor API Gateway is configured through several files:

- **`config.json`**: Main configuration file with settings for:
  - Server port and host
  - Protocol configurations
  - Authentication settings
  - Routing rules
  - Rate limiting parameters

- **`protocols/`**: Protocol-specific configuration files

## Integration with Other Components

The Sensor API Gateway integrates with several other platform components:

- **Sensor Manager**: Routes sensor data and commands
- **LDAP**: Verifies sensor authentication
- **Monitoring & Fault Tolerance**: Reports gateway health
- **Logger**: Logs gateway activities
- **API Gateway**: Coordinates with main API Gateway

## Security Considerations

The Sensor API Gateway implements several security measures:

- **Sensor Authentication**: Sensors must authenticate before sending data
- **Data Encryption**: All communication is encrypted
- **Input Validation**: All sensor data is validated
- **Rate Limiting**: Prevents DoS attacks
- **Access Control**: Restricts sensor access based on permissions

## Dependencies

- Python 3.8+
- MQTT broker (e.g., Mosquitto)
- CoAP library
- Flask/FastAPI
- Kafka client
- Redis (for caching and rate limiting)

## Files Description

- **`main.py`**: Main application entry point
- **`request_handler.py`**: Request processing
- **`protocol_adapters/`**: Protocol support
- **`authentication.py`**: Authentication functionality
- **`routing_engine.py`**: Request routing
- **`data_validator.py`**: Data validation
- **`rate_limiter.py`**: Rate limiting
- **`caching.py`**: Response caching
- **`monitoring.py`**: Health monitoring
- **`kafka_handler.py`**: Kafka integration
- **`config.json`**: Configuration settings
- **`protocols/`**: Protocol configurations
- **`global_variables.py`**: Shared variables
