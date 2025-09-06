# Kubernetes Bootcamp - Google Cloud Next 19

A sample microservices application demonstrating Kubernetes deployment patterns on Google Cloud Platform.

## Overview

This project contains a Go-based microservices application with frontend and backend components, designed for Kubernetes deployment with various environment configurations (dev, canary, production).

## Architecture

- **Frontend**: Web interface that displays instance metadata and communicates with backend
- **Backend**: API service that provides instance information and metadata
- **Kubernetes**: Container orchestration with multi-environment support

## Features

- Instance metadata display (hostname, zone, IP addresses, etc.)
- Health check endpoints (`/healthz`)
- Version information (`/version`)
- Multi-environment deployment configurations
- Canary deployment support

## Quick Start

### Prerequisites

- Docker
- Kubernetes cluster (GKE recommended)
- kubectl configured

### Running Locally

```bash
# Backend
go run main.go

# Frontend
go run main.go -frontend -backend-service=http://localhost:8080
```

### Docker Build

```bash
docker build -t k8s-bootcamp-app .
```

### Kubernetes Deployment

```bash
# Deploy to development
kubectl apply -f k8s/dev/

# Deploy to production
kubectl apply -f k8s/production/

# Deploy canary release
kubectl apply -f k8s/canary/
```

## Project Structure

```
├── k8s-bootcamp-app/          # Main application code
│   ├── main.go               # Application entry point
│   ├── html.go              # Frontend templates
│   ├── Dockerfile           # Container configuration
│   └── k8s/                 # Kubernetes manifests
│       ├── dev/             # Development environment
│       ├── production/      # Production environment
│       ├── canary/          # Canary deployment
│       └── services/        # Service definitions
└── README.md
```

## Configuration

The application supports several command-line flags:

- `-port`: Port to bind (default: 8080)
- `-frontend`: Run in frontend mode
- `-backend-service`: Backend service URL
- `-version`: Display version information

## License

Copyright 2015 Google Inc. Licensed under the Apache License, Version 2.0.