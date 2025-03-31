# Windsurf Cross-Device Synchronization Guide

## Overview
This toolkit provides a seamless development experience across multiple devices, specifically optimized for Mac mini and MacBook Air.

## Prerequisites
- Git
- Python 3.8+
- pip
- pytest

## Synchronization Workflow

### Quick Start
```bash
# Sync project across devices
./scripts/windsurf_sync.sh sync

# Check current environment
./scripts/windsurf_sync.sh status
```

### Key Features
🔄 Automatic Git synchronization
🧪 Dependency management
📊 Environment tracking
🔒 Safe stashing of local changes

## Workflow Details

### 1. Git Synchronization
- Stashes local changes
- Fetches and pulls latest changes
- Updates submodules
- Restores local changes

### 2. Environment Verification
- Captures device-specific details
- Logs development environment
- Provides cross-device insights

### 3. Dependency Management
- Updates project dependencies
- Ensures consistent environment across devices

### 4. Integration Testing
- Runs comprehensive test suite
- Validates project integrity

## Security Considerations
- Temporary stashing of local changes
- No automatic overwriting of local work
- Explicit user interaction required

## Troubleshooting
- Ensure Git credentials are configured
- Check network connectivity
- Verify Python and dependency versions

## Recommended Workflow
1. Start on one device
2. Run `./scripts/windsurf_sync.sh sync`
3. Switch to another device
4. Repeat synchronization

## Configuration
Customize synchronization in `scripts/windsurf_sync.sh`

## Support
Report issues on GitHub repository
