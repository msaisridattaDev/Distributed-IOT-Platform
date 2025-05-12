# Admin UI & API

The Admin UI & API component provides a comprehensive administrative interface and API for managing the Distributed IoT Platform.

## Overview

The Admin UI & API component serves as the primary interface for platform administrators to manage and monitor the Distributed IoT Platform. It provides a web-based user interface and a set of RESTful APIs for performing administrative tasks, monitoring platform health, managing users and applications, and configuring platform settings. This component integrates with all other platform components to provide a unified administrative experience.

## Key Features

- **Platform Dashboard**: Provides an overview of platform status
- **User Management**: Manages platform users and roles
- **Application Management**: Manages deployed applications
- **Node Management**: Monitors and manages platform nodes
- **Sensor Management**: Manages IoT sensors
- **Deployment Management**: Manages application deployments
- **Monitoring & Alerts**: Displays monitoring data and alerts
- **Log Viewer**: Provides access to platform logs
- **Configuration Management**: Manages platform configuration
- **API Access**: Provides RESTful APIs for all functionality

## Architecture

The Admin UI & API component follows a modular architecture with several key components:

- **Frontend UI**: Web-based user interface
- **API Layer**: RESTful API implementation
- **Authentication Module**: Handles user authentication
- **Authorization Module**: Controls access to functionality
- **Data Access Layer**: Accesses platform data
- **Integration Layer**: Integrates with other platform components
- **Notification System**: Manages notifications and alerts

## Components

### Frontend UI

Web-based user interface:
- Dashboard views
- Management interfaces
- Monitoring displays
- Configuration forms
- Interactive visualizations

### API Layer

RESTful API implementation:
- API endpoints
- Request handling
- Response formatting
- API documentation
- API versioning

### Authentication Module

Handles user authentication:
- Login/logout functionality
- Session management
- Token handling
- Multi-factor authentication
- Authentication policies

### Authorization Module

Controls access to functionality:
- Permission checking
- Role-based access control
- Feature access control
- Data access control
- Audit logging

### Data Access Layer

Accesses platform data:
- Database access
- Data retrieval
- Data manipulation
- Data validation
- Data caching

### Integration Layer

Integrates with other platform components:
- Component communication
- Data synchronization
- Event handling
- Service discovery
- Error handling

### Notification System

Manages notifications and alerts:
- Alert display
- Notification generation
- Notification delivery
- Notification preferences
- Notification history

## Workflow

1. **User Authentication**:
   - Administrator logs in
   - Authentication is verified
   - Session is established
   - Permissions are determined

2. **Dashboard View**:
   - Platform status is displayed
   - Key metrics are shown
   - Recent activities are listed
   - Alerts are highlighted

3. **Administrative Tasks**:
   - Administrator performs tasks
   - Changes are validated
   - Actions are executed
   - Results are displayed

4. **Monitoring**:
   - Platform health is monitored
   - Performance metrics are displayed
   - Resource utilization is shown
   - Alerts are managed

## API Endpoints

The Admin UI & API component exposes several API endpoints:

### Authentication

- **`POST /api/auth/login`**: User login
- **`POST /api/auth/logout`**: User logout
- **`POST /api/auth/refresh`**: Refresh authentication token

### User Management

- **`GET /api/users`**: List all users
- **`GET /api/users/{user_id}`**: Get user details
- **`POST /api/users`**: Create a new user
- **`PUT /api/users/{user_id}`**: Update user information
- **`DELETE /api/users/{user_id}`**: Delete a user

### Application Management

- **`GET /api/apps`**: List all applications
- **`GET /api/apps/{app_id}`**: Get application details
- **`POST /api/apps`**: Register a new application
- **`PUT /api/apps/{app_id}`**: Update application information
- **`DELETE /api/apps/{app_id}`**: Delete an application

### Node Management

- **`GET /api/nodes`**: List all nodes
- **`GET /api/nodes/{node_id}`**: Get node details
- **`PUT /api/nodes/{node_id}`**: Update node information
- **`POST /api/nodes/{node_id}/actions/restart`**: Restart a node

### Deployment Management

- **`GET /api/deployments`**: List all deployments
- **`GET /api/deployments/{deployment_id}`**: Get deployment details
- **`POST /api/deployments`**: Create a new deployment
- **`DELETE /api/deployments/{deployment_id}`**: Cancel a deployment

### Monitoring

- **`GET /api/monitoring/health`**: Get platform health
- **`GET /api/monitoring/metrics`**: Get platform metrics
- **`GET /api/monitoring/alerts`**: Get active alerts
- **`GET /api/monitoring/resources`**: Get resource utilization

### Logs

- **`GET /api/logs`**: Query logs
- **`GET /api/logs/search`**: Search logs
- **`GET /api/logs/download`**: Download logs

## UI Sections

The Admin UI is organized into several sections:

1. **Dashboard**: Overview of platform status
2. **Users**: User management
3. **Applications**: Application management
4. **Nodes**: Node management
5. **Sensors**: Sensor management
6. **Deployments**: Deployment management
7. **Monitoring**: Platform monitoring
8. **Logs**: Log viewer
9. **Configuration**: Platform configuration
10. **Settings**: UI settings

## Configuration

The Admin UI & API component is configured through several files:

- **`config.json`**: Main configuration file with settings for:
  - Server port and host
  - UI configuration
  - API configuration
  - Authentication settings
  - Integration settings

- **`ui-config.json`**: UI-specific configuration

## Integration with Other Components

The Admin UI & API component integrates with all other platform components:

- **API Gateway**: Routes API requests
- **LDAP**: Authenticates users
- **Node Manager**: Manages nodes
- **Scheduler**: Manages deployments
- **Deployer**: Tracks deployments
- **Monitoring & Fault Tolerance**: Displays monitoring data
- **Logger**: Displays logs
- **Sensor Manager**: Manages sensors

## Dependencies

- **Frontend**:
  - React.js
  - Material-UI
  - Chart.js
  - Axios

- **Backend**:
  - Python 3.8+
  - Flask/FastAPI
  - Kafka client
  - MongoDB client
  - JWT library

## Files Description

- **Frontend**:
  - **`src/`**: React application source
  - **`public/`**: Static assets
  - **`package.json`**: NPM dependencies

- **Backend**:
  - **`main.py`**: Main application entry point
  - **`api/`**: API implementation
  - **`auth/`**: Authentication functionality
  - **`integration/`**: Integration with other components
  - **`models/`**: Data models
  - **`config.json`**: Configuration settings
  - **`global_variables.py`**: Shared variables
