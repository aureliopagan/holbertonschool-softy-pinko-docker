# Docker Containerization Project

This project demonstrates Docker fundamentals through building a multi-container web application with Flask backend, Nginx frontend, and load balancing.

## Quick Start

```bash
cd task6
docker-compose up --scale back-end=2
```

Access at http://localhost

## Project Structure

- **Task 0**: Basic Ubuntu container
- **Task 1**: Flask API server
- **Task 2**: Added Nginx frontend  
- **Task 3**: Connected frontend to backend with CORS
- **Task 4**: Docker Compose orchestration
- **Task 5**: Nginx reverse proxy
- **Task 6**: Horizontal scaling with load balancing

## Key Files

```
task6/
├── docker-compose.yml          # Container orchestration
├── proxy/
│   ├── Dockerfile
│   └── proxy.conf             # Nginx proxy config
├── back-end/
│   ├── Dockerfile  
│   └── api.py                 # Flask API
├── front-end/
│   ├── Dockerfile
│   ├── softy-pinko-front-end.conf
│   └── softy-pinko-front-end/  # Static files
└── 2-api-servers.txt          # Scaling command

```

## Architecture

```
Client → Proxy (Port 80) → Frontend (Port 9000) / Backend APIs (Port 5252)
```

The proxy routes `/` to frontend and `/api` to backend services. Multiple backend instances are load balanced using round-robin.

## Common Commands

```bash
# Build all containers
docker-compose build

# Start with multiple backend servers
docker-compose up --scale back-end=2

# Stop all services  
docker-compose down
```

## Tech Stack

- **Backend**: Python Flask with CORS
- **Frontend**: Nginx serving static content
- **Proxy**: Nginx reverse proxy and load balancer
- **Orchestration**: Docker Compose