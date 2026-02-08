# CeiVoice

## Project Structure

```
CeiVoice/
├── docker-compose.yml              # Docker orchestration for all services
├── .env
│
├── ApiGateway/                     # Nginx API Gateway
│   └── nginx.conf
│
├── IdentityServer/                 # Authentication & Authorization Service
│   ├── Dockerfile
│   ├── server.ts
│
├── OrganizationService/            # Organization management service
│   ├── Dockerfile
│   ├── server.ts
│
└── EmailService/                   # Email Notification Service
	├── dockerfile
	├── server.ts
```

### Repository Links

- ApiGateway - https://github.com/CeiVoice/Gateway
- IdentityServer - https://github.com/CeiVoice/IdentityService
- EmailService - https://github.com/CeiVoice/EmailService
- OrganizationService - https://github.com/CeiVoice/OrganizationService

## Architecture

This is a microservices-based architecture with:

- API Gateway (Nginx): Routes requests to appropriate services
- IdentityServer: Handles user authentication, registration, and email confirmation
- EmailService: Sends emails triggered by events from other services
- RabbitMQ: Message broker for asynchronous communication between services
- Supabase: Backend database and authentication provider

## Services

### IdentityServer (Port 8001)
- User registration and authentication
- JWT token generation
- Email confirmation workflow
- Publishes user events to RabbitMQ

### EmailService (Port 5050)
- Consumes user events from RabbitMQ
- Sends transactional emails via Resend API
- Handles email confirmation notifications

### OrganizationService
- Manages organizations and members

### API Gateway (Ports 80/443)
- Reverse proxy for all services
- Request routing and load balancing
- SSL/TLS termination ready
