# SampleApiPlatform

A cloud-native distributed application platform built with ASP.NET Core and Microsoft Azure.

This project demonstrates the design, implementation, deployment, and operation of a modern microservices-based application using Azure-native services, secure authentication, service-to-service communication, and automated CI/CD pipelines.

## Architecture

```text
Client
|
v
SampleAppApi
|
| Dapr Service Invocation
v
SampleDataAccessApi
|
v
Azure SQL Database

```

## Components

### SampleAppApi
The primary API service responsible for handling client requests, business logic, authentication, and communication with backend services.

**Technologies:**
- ASP.NET Core
- Dapr Service Invocation
- JWT Authentication
- Docker
- Azure Container Apps

### SampleDataAccessApi
A dedicated data access service responsible for interacting with Azure SQL Database.

**Technologies:**
- ASP.NET Core
- Entity Framework Core
- Azure SQL Database
- Managed Identity
- Docker
- Azure Container Apps

### SampleSharedModels
Shared contracts and DTO models used by multiple services to ensure consistent communication.

## Cloud Platform

The platform is deployed to Microsoft Azure using:

- Azure Container Apps
- Azure SQL Database
- Azure Container Registry
- Azure Key Vault
- Managed Identities
- Dapr
- Azure Monitor
- Azure DevOps Pipelines

## Security

The platform demonstrates several security practices:

- JWT-based authentication
- Service-to-service authentication
- Managed Identity integration
- Secret management using Azure Key Vault
- Environment-based configuration

## CI/CD

Deployment is automated using Azure DevOps pipelines.

**Features include:**
- Automated builds
- Container image creation
- Azure Container Registry integration
- Automated deployments
- Revision-based deployments in Azure Container Apps

## Challenges Solved

During development several cloud-native engineering challenges were addressed:

- Container startup failures
- Azure Container Apps revision management
- Dapr service discovery and invocation
- Secure database connectivity
- Managed Identity authentication
- Secret management
- CI/CD troubleshooting
- Distributed system debugging

## Documentation

Detailed documentation is available in the `docs/` folder:

- [Container.pdf](docs/Container.pdf) – Deployment and Container Guide

## Skills Demonstrated

`C#` `ASP.NET Core` `REST APIs` `Entity Framework Core` `Azure` `Docker` `Dapr` `Azure SQL Database` `Azure DevOps` `CI/CD` `Cloud Security` `Microservices Architecture`

## Purpose

This project was created as a professional portfolio project to demonstrate practical experience in designing, developing, deploying, and operating cloud-native applications on Microsoft Azure.