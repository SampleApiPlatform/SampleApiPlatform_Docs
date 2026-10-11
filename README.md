# SampleApiPlatform

A cloud-native microservices platform built with ASP.NET Core and Microsoft Azure.

This project demonstrates the design, implementation, deployment, security, and operation of a distributed application hosted on Azure Container Apps. The platform showcases modern cloud-native development practices including Microsoft Entra ID authentication, Dapr service invocation, Azure SQL integration, Managed Identity, Azure Key Vault, and automated CI/CD pipelines.

---

# Project Highlights

✅ Developed a distributed microservices platform on Microsoft Azure

✅ Implemented Microsoft Entra ID authentication using OAuth 2.0, OpenID Connect, and JWT Bearer tokens

✅ Secured Azure SQL database access using Managed Identity

✅ Implemented service-to-service communication using Dapr Service Invocation

✅ Integrated Azure Key Vault for secure secret management

✅ Automated build, test, deployment, and database migrations using Azure DevOps

✅ Containerized services using Docker and hosted them in Azure Container Apps

✅ Designed and deployed a secure end-to-end cloud-native architecture

---

---

# Documentation

Detailed implementation and deployment documentation is available in the project documentation:

- [Container.pdf](docs/Container.pdf) – Azure architecture, Azure Container Apps, Dapr configuration, Managed Identity setup, Azure SQL integration, Microsoft Entra ID authentication, Azure Key Vault integration, CI/CD pipelines, and deployment walkthroughs.

The documentation describes the complete journey from local development through containerization, deployment, authentication, security configuration, and production hosting in Azure.

# Solution Architecture

```text
                 ┌─────────────────────┐
                 │  Client Application │
                 │ (Angular / Browser) │
                 └──────────┬──────────┘
                            │
                            │ OAuth 2.0 / OpenID Connect
                            ▼
                   Microsoft Entra ID
                            │
                            │ JWT Access Token
                            ▼
                    ┌───────────────┐
                    │ SampleAppApi  │
                    │  Public API   │
                    └───────┬───────┘
                            │
                            │ Dapr Service Invocation
                            ▼
                  ┌───────────────────┐
                  │SampleDataAccessApi│
                  │  Internal API     │
                  └─────────┬─────────┘
                            │
                            ▼
                    Azure SQL Database
```

---

# Architecture Decisions

The platform intentionally uses a microservices architecture to demonstrate modern cloud-native engineering practices.

### Authentication Boundary

Authentication and authorization are enforced at the SampleAppApi boundary using Microsoft Entra ID.

Protected endpoints require:

```http
Authorization: Bearer <JWT>
```

Authenticated users must possess the required API scope:

```text
access_as_user
```

### Internal Service Communication

The SampleDataAccessApi is designed as an internal service and communicates with SampleAppApi through Dapr Service Invocation.

Benefits:

- Service discovery
- Retry capabilities
- Resiliency
- Reduced infrastructure coupling
- Simplified service communication

### Database Security

Azure SQL authentication is implemented using Managed Identity.

Benefits:

- No passwords
- No embedded credentials
- No database secrets in source control
- Passwordless Azure authentication

### Secret Management

Platform secrets are stored securely in Azure Key Vault and retrieved at runtime.

---

# Key Features

## Authentication & Authorization

- Microsoft Entra ID integration
- OAuth 2.0
- OpenID Connect
- JWT Bearer Authentication
- Scope-based authorization
- Protected REST endpoints
- User identity validation

## Cloud Security

- Azure Key Vault
- Managed Identity
- Secret management
- Secure configuration
- Environment-based settings

## Service-to-Service Communication

- Dapr Service Invocation
- Service discovery
- Retry mechanisms
- Internal API communication

## Data Layer

- Azure SQL Database
- Entity Framework Core
- Repository Pattern
- Service Pattern

## Platform & Hosting

- Azure Container Apps
- Docker
- Azure Monitor
- Log Analytics

## DevOps

- Azure DevOps Pipelines
- Continuous Integration
- Continuous Deployment
- Automated Testing
- Entity Framework Migrations

---

# Components

## SampleAppApi

The public entry point of the platform.

### Responsibilities

- User authentication
- User authorization
- JWT validation
- Business logic execution
- Service orchestration
- Dapr communication

### Technologies

- ASP.NET Core
- Microsoft Identity Web
- JWT Authentication
- Dapr
- Azure Key Vault
- Docker
- Azure Container Apps

---

## SampleDataAccessApi

Internal service responsible for data access.

### Responsibilities

- Azure SQL interaction
- CRUD operations
- Entity Framework Core operations
- Database abstraction

### Technologies

- ASP.NET Core
- Entity Framework Core
- Azure SQL Database
- Managed Identity
- Docker
- Azure Container Apps

---

## SampleSharedModels

Shared NuGet package used by both services.

Contains:

- DTOs
- Interfaces
- Shared contracts
- Common models

This package ensures consistent communication between services.

---

# Azure Services Used

- Microsoft Entra ID
- Azure Container Apps
- Azure SQL Database
- Azure Key Vault
- Azure Monitor
- Azure Log Analytics
- Managed Identity
- Azure DevOps
- Dapr

---

# Authentication Flow

```text
User
 │
 ▼
Microsoft Entra ID
 │
 │ JWT Access Token
 ▼
SampleAppApi
 │
 │ Token Validation
 ▼
Business Logic
 │
 │ Dapr Service Invocation
 ▼
SampleDataAccessApi
 │
 ▼
Azure SQL Database
```

The API validates:

- Token signature
- Audience
- Tenant
- Expiration
- Scope (`access_as_user`)

Only authenticated users can access protected endpoints.

---

# CI/CD Pipeline

Azure DevOps pipelines automate the complete deployment process.

Pipeline responsibilities:

1. Restore dependencies
2. Build solution
3. Execute unit tests
4. Generate code coverage
5. Execute Entity Framework migrations
6. Build Docker images
7. Push container images
8. Deploy new Azure Container App revisions

---

# Challenges Solved

During the development of this platform I gained practical experience with:

- Azure Container Apps deployment and troubleshooting
- Microsoft Entra ID integration
- OAuth 2.0 and OpenID Connect flows
- JWT token validation and authorization policies
- Azure Key Vault integration
- Managed Identity configuration
- Azure SQL authentication
- Dapr service discovery and invocation
- Secret management
- CI/CD automation
- Distributed system debugging

---

# Skills Demonstrated

- C#
- ASP.NET Core
- REST APIs
- Entity Framework Core
- Azure Container Apps
- Azure SQL Database
- Microsoft Entra ID
- OAuth 2.0
- OpenID Connect
- JWT Authentication
- Azure Key Vault
- Managed Identity
- Dapr
- Docker
- Azure DevOps
- CI/CD Pipelines
- Cloud Security
- Distributed Systems
- Microservices Architecture

---

# Purpose

SampleApiPlatform was created as a professional portfolio project to demonstrate practical experience designing, building, securing, deploying, and operating cloud-native applications on Microsoft Azure.

The project combines modern enterprise technologies including Microsoft Entra ID, Azure Container Apps, Dapr, Azure SQL, Managed Identity, Azure Key Vault, and Azure DevOps to showcase real-world cloud architecture and software engineering practices.