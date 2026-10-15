# SampleApiPlatform

A cloud-native microservices platform built with ASP.NET Core and Microsoft Azure.

This project demonstrates the design, implementation, deployment, security, and operation of a distributed application hosted on Azure Container Apps. The platform showcases modern cloud-native development practices including Microsoft Entra ID authentication, Dapr service invocation, Azure SQL integration, Managed Identity, Azure Key Vault, and automated CI/CD pipelines.

## Project Highlights

✅ Developed a distributed microservices platform on Microsoft Azure

✅ Implemented a dedicated authentication microservice (SampleAuthApi) using Microsoft Entra ID, OAuth 2.0, OpenID Connect, and JWT tokens

✅ Separated authentication, business logic, and data access into independent services

✅ Secured Azure SQL database access using Managed Identity

✅ Implemented service-to-service communication using Dapr Service Invocation

✅ Integrated Azure Key Vault for secure secret management

✅ Automated build, test, deployment, and database migrations using Azure DevOps

✅ Containerized services using Docker and hosted them in Azure Container Apps

✅ Designed and deployed a secure end-to-end cloud-native architecture

---

## Documentation

Detailed implementation and deployment documentation is available in the project documentation:

- [Container.pdf](docs/Container.pdf) – Azure architecture, Azure Container Apps, Dapr configuration, Managed Identity setup, Azure SQL integration, Microsoft Entra ID authentication, Azure Key Vault integration, CI/CD pipelines, and deployment walkthroughs.

The documentation describes the complete journey from local development through containerization, deployment, authentication, security configuration, and production hosting in Azure.

---

## Solution Architecture

```text
                 ┌─────────────────────┐
                 │  Client Application │
                 │ (Angular / Browser) │
                 └──────────┬──────────┘
                            │
                            │ OAuth 2.0 / OpenID Connect
                            ▼

               ┌─────────────────────────┐
               │      SampleAuthApi      │
               │ Authentication Service  │
               └──────────┬──────────────┘
                          │
                          │ JWT Access Token
                          ▼

               ┌─────────────────────────┐
               │      SampleAppApi       │
               │ Business API Gateway    │
               └──────────┬──────────────┘
                          │
                          │ Dapr Service Invocation
                          ▼

               ┌─────────────────────────┐
               │   SampleDataAccessApi   │
               │     Data Service        │
               └──────────┬──────────────┘
                          │
                          ▼

                  Azure SQL Database
```

---

## Architecture Decisions

### Authentication Boundary

Authentication responsibilities are isolated in the SampleAuthApi microservice.

Responsibilities include:

- User authentication
- Microsoft Entra ID integration
- OAuth 2.0 and OpenID Connect flows
- JWT token issuance
- JWT token validation

This separation follows the Single Responsibility Principle and creates a clear security boundary between authentication and business logic.

### Business Layer

SampleAppApi acts as the public business API of the platform.

Responsibilities include:

- Processing business requests
- Authorization enforcement
- Business workflows
- Service orchestration
- Communication with internal services through Dapr

### Internal Service Communication

The platform uses Dapr Service Invocation for communication between internal services.

Benefits:

- Service discovery
- Retry capabilities
- Circuit breakers
- Resiliency
- Reduced infrastructure coupling
- Simplified service communication

### Database Security

Azure SQL authentication is implemented using Managed Identity.

Benefits:

- Passwordless authentication
- No embedded credentials
- No database secrets in source control
- Secure Azure-native authentication

### Secret Management

Platform secrets are stored securely in Azure Key Vault and retrieved at runtime.

---

## Key Features

### Authentication & Authorization

- Microsoft Entra ID integration
- OAuth 2.0
- OpenID Connect
- JWT Bearer Authentication
- Token issuance
- Token validation
- Scope-based authorization
- Protected REST endpoints

### Cloud Security

- Azure Key Vault
- Managed Identity
- Secret management
- Secure configuration
- Environment-based settings

### Service-to-Service Communication

- Dapr Service Invocation
- Service discovery
- Retry mechanisms
- Internal API communication

### Data Layer

- Azure SQL Database
- Entity Framework Core
- Repository Pattern
- Service Pattern

### Platform & Hosting

- Azure Container Apps
- Docker
- Azure Monitor
- Log Analytics

### DevOps

- Azure DevOps Pipelines
- Continuous Integration
- Continuous Deployment
- Automated Testing
- Entity Framework Migrations

---

## Components

### SampleAuthApi

Authentication and identity microservice.

#### Responsibilities

- User authentication
- Microsoft Entra ID integration
- OAuth 2.0
- OpenID Connect
- JWT token generation
- JWT token validation
- User identity management

#### Technologies

- ASP.NET Core
- Microsoft Identity Web
- Microsoft Entra ID
- JWT Authentication
- Docker
- Azure Container Apps

---

### SampleAppApi

Public business API and orchestration layer.

#### Responsibilities

- Business endpoints
- Authorization
- Request validation
- Service orchestration
- Dapr communication
- API gateway functionality

#### Technologies

- ASP.NET Core
- Dapr
- Azure Key Vault
- Docker
- Azure Container Apps

---

### SampleDataAccessApi

Internal data access microservice.

#### Responsibilities

- Azure SQL interaction
- CRUD operations
- Entity Framework Core operations
- Database abstraction

#### Technologies

- ASP.NET Core
- Entity Framework Core
- Azure SQL Database
- Managed Identity
- Docker
- Azure Container Apps

---

### SampleSharedModels

Shared NuGet package used by all services.

Contains:

- DTOs
- Interfaces
- Shared contracts
- Result models
- Common abstractions

This package ensures consistent communication between microservices.

---

## Azure Services Used

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

## Authentication Flow

```text
User
 │
 ▼
SampleAuthApi
 │
 │ Authenticate with Microsoft Entra ID
 ▼
JWT Access Token
 │
 ▼
SampleAppApi
 │
 │ Authorization
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

Protected business endpoints require a valid JWT access token issued by SampleAuthApi.

---

## CI/CD Pipeline

Azure DevOps pipelines automate the complete deployment process.

Pipeline responsibilities:

- Restore dependencies
- Build solution
- Execute unit tests
- Generate code coverage
- Execute Entity Framework migrations
- Build Docker images
- Push container images
- Deploy new Azure Container App revisions

Each microservice is independently containerized and deployed through Azure DevOps pipelines.

---

## Challenges Solved

During the development of this platform I gained practical experience with:

- Azure Container Apps deployment and troubleshooting
- Microsoft Entra ID integration
- OAuth 2.0 and OpenID Connect flows
- JWT token validation and authorization policies
- Microservice decomposition and service boundaries
- Azure Key Vault integration
- Managed Identity configuration
- Azure SQL authentication
- Dapr service discovery and invocation
- Secret management
- CI/CD automation
- Distributed system debugging

---

## Skills Demonstrated

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

## Architectural Evolution

The platform originally consisted of two services:

- SampleAppApi
- SampleDataAccessApi

As the project evolved, authentication concerns were extracted into a dedicated authentication service (SampleAuthApi).

This refactoring improved:

- Separation of concerns
- Security boundaries
- Scalability
- Maintainability
- Independent deployment of authentication features

The result is a three-service cloud-native architecture consisting of:

- SampleAuthApi (Authentication)
- SampleAppApi (Business APIs)
- SampleDataAccessApi (Data Access)

---

## Purpose

SampleApiPlatform was created as a professional portfolio project to demonstrate practical experience designing, building, securing, deploying, and operating cloud-native applications on Microsoft Azure.

The project combines modern enterprise technologies including Microsoft Entra ID, Azure Container Apps, Dapr, Azure SQL, Managed Identity, Azure Key Vault, and Azure DevOps to showcase real-world cloud architecture and software engineering practices.