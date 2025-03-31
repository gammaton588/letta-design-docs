# Letta Project Architecture

## System Overview

Letta is a distributed system for AI-enhanced productivity and knowledge management, consisting of several interconnected components that work together to provide a seamless experience across multiple devices.

## Core Components

### 1. Letta Server
- **Technology**: FastAPI + PostgreSQL
- **Key Features**:
  - RESTful APIs for memory management
  - JSONB-based memory storage
  - Full-text search capabilities
  - Notion integration bridge
- **Location**: `/server`
- **Dependencies**: PostgreSQL, FastAPI, Google Gemini API

### 2. Synchronization System
- **Technology**: Python + iCloud
- **Key Features**:
  - Bi-directional synchronization
  - Device registration and identification
  - Hash-based file change detection
  - Category-specific syncing
- **Synchronized Components**:
  - Memories (~/.codeium/windsurf/memories)
  - Code (~/Library/Mobile Documents/com~apple~CloudDocs/Windsurf Workspace)
  - Settings (~/.codeium/windsurf/settings)
  - Databases (~/.codeium/windsurf/db)
  - Extensions (~/.codeium/windsurf/extensions)
- **Location**: `/sync/enhanced_workspace_sync.py`

### 3. Task Management System
- **Technology**: Python + JSON
- **Key Features**:
  - Kanban-style workflow (Backlog, In Progress, Review, Completed)
  - Task metadata (priority, tags, description)
  - Automatic archiving
  - Cloud storage integration
- **Storage**:
  - Active Tasks: `~/Library/Mobile Documents/com~apple~CloudDocs/Windsurf Workspace/task_management/tasks.json`
  - Archived Tasks: `task_management/task_archive.json`
- **Location**: `/scripts/task_manager.py`

### 4. Taskade Integration
- **Technology**: Python
- **Key Features**:
  - Task synchronization with Taskade
  - AI-enhanced prioritization (Google Gemini)
  - Prometheus monitoring
  - CLI-based management
- **Location**: `/integrations/taskade`

### 5. Monitoring & Self-Repair
- **Technology**: Python + Gemini AI
- **Key Features**:
  - AI-powered diagnostics
  - Automatic health checks
  - Self-repair capabilities
  - Log management and rotation
- **Location**: `/monitor`
- **Logs**: `~/Library/Logs/letta-*.log`

## Data Flow Architecture

```
┌─────────────────┐     ┌──────────────┐     ┌────────────────┐
│   Letta Server  │◄────┤  Task System  │────►│ Task Archives  │
└────────┬────────┘     └──────┬───────┘     └────────────────┘
         │                     │
         │                     │
┌────────▼─────────┐    ┌─────▼────────┐     ┌────────────────┐
│  PostgreSQL DB   │◄───┤  Sync System  │────►│  iCloud Store  │
└────────┬─────────┘    └──────┬───────┘     └────────────────┘
         │                     │
         │                     │
┌────────▼─────────┐    ┌─────▼────────┐     ┌────────────────┐
│ Notion Bridge    │    │    Monitor    │────►│  System Logs   │
└─────────────────┘     └──────────────┘     └────────────────┘
```

## Security Architecture

- Environment-based configuration
- API key management
- Secure file permissions
- Encrypted data storage
- Device registration system

## Deployment Architecture

### Primary Components
- Docker containers for server
- Launchd agents for auto-start
- Monitoring services
- Background sync processes

### Locations
- Server: `http://localhost:8284`
- Monitor CLI: `letta-monitor`
- Launch Agents:
  - `~/Library/LaunchAgents/com.letta.server.plist`
  - `~/Library/LaunchAgents/com.letta.monitor.plist`

## Development Architecture

### Technology Stack
- Python 3.9+
- FastAPI
- PostgreSQL
- Docker & Docker Compose
- Google Gemini API
- iCloud integration

### Development Tools
- Poetry for dependency management
- pytest for testing
- Black for formatting
- mypy for type checking
- flake8 for linting

## Future Architecture Considerations

1. **Scalability**
   - Microservices decomposition
   - Load balancing
   - Caching layer

2. **Integration Expansion**
   - Additional knowledge base integrations
   - Extended AI capabilities
   - Enhanced monitoring

3. **Performance Optimization**
   - Database query optimization
   - Sync efficiency improvements
   - Memory usage optimization
