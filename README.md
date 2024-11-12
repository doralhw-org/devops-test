# Azure DevOps Challenge

Welcome to our DevOps Challenge, crafted to assess your skills. This challenge includes tasks across infrastructure setup, application deployment, API management, and security, giving you the opportunity to demonstrate your proficiency in DevOps practices. Our aim is not only to evaluate your technical capabilities but also to observe your approach to problem-solving and adaptability in a live environment.

You will complete these tasks in a two-hour live session, during which two additional test steps will be disclosed, allowing for dynamic real-time learning and solution development.

---
## Scenario Overview

Contoso Healthcare Solutions is a provider of cloud-based medical records software for healthcare clinics. The company is launching a new patient data application designed to store patient records securely, handle varying traffic levels from different clinics, and ensure infrastructure scalability while maintaining high security.

Your task is to deploy the application with a highly available infrastructure, monitor the application and its underlying components, and ensure smooth operation. The deployment must enforce security and private traffic within the infrastructure, while the system processes API requests from multiple clinics with varying traffic loads.

---

## Application Description

The patient data application consists of two main components:

1. **Front-End**: A web portal for clinic staff to interact with patient records. This web application should display basic information, like a "Hello World" message or similar, and allow clinic staff to check the system's health. It will make HTTP requests to the back end and display the results. The front end may be developed using React, Angular, or plain HTML/JavaScript.

2. **Back-End**: A REST API that handles patient data requests and securely stores the data. It exposes two endpoints:
   - `GET /health`: A health check endpoint returning a JSON object with the status of the system (e.g., `{'status': 'healthy'}`).
   - `POST /data`: An endpoint that accepts patient data in JSON format, stores it in a backend service (SQL, PostgreSQL, Cosmos DB, or Azure Storage Account), and responds with `{'status': 'received'}`.

---

## Step 1: Infrastructure Deployment

In this step, you will set up the infrastructure needed to support the new patient data application. The infrastructure must ensure private and secure communication between components and be highly available to meet the demands of multiple clinics.

### Task 1: Infrastructure Setup (Private Traffic + Optional Custom Domain)

**Objective**: Set up the infrastructure to ensure private traffic and secure API management.

**Resources Required**:
- Virtual Network (VNet) with subnets to separate front-end and back-end traffic.
- Private Endpoints for enforcing private communication between components.
- Network Security Groups (NSGs) to secure traffic flow between the front-end and back-end.
- Key Vault for secure storage of API keys, secrets, and connection strings.
- Azure Container Apps or AKS for hosting the back-end API and handling requests privately.
- DNS service for private traffic routing between components.
- Azure Front Door or Application Gateway for routing and managing the front end.
- Custom Domain (Optional)

**Instructions**:
1. Use an Infrastructure as Code (IaC) tool (e.g., Bicep, Terraform, ARM templates) to deploy the necessary infrastructure, including secure networking components such as VNets, private endpoints, and DNS service integration for internal traffic routing.
2. Include a secure storage mechanism (e.g., Azure Key Vault) to store sensitive configuration items like API keys and connection strings.
3. Enforce private traffic between the front-end and back-end components, ensuring secure communication through VNet integration.
4. As a bonus, set up a custom domain for the application using SSL/TLS certificates for secure access via Azure Front Door or Application Gateway.

---

## Step 2: Application Deployment and Management

Once the infrastructure is set up, deploy the application, which includes the front-end web portal and the back-end API. The front end enables clinic staff to interact with patient records, while the back end manages API requests and data.

### Task 2: Build and Deploy the Application (Front-End and Back-End)

**Objective**: Build both the front-end and back-end applications and deploy them.

**Resources Required**:
- Azure Container Apps or AKS for hosting the back-end API.
- Storage account (Azure Storage, SQL, PostgreSQL, or Cosmos DB) for securely storing patient data.
- Azure DevOps or GitHub Actions for automating the CI/CD pipeline.
- App Configuration service for managing environment-specific settings.

**Instructions**:
1. Build the front-end web portal using a suitable framework (React, Angular, or plain HTML/JavaScript). Ensure it interacts with the back-end API by making at least one HTTP request to retrieve patient data (e.g., a health check).
2. Develop a simple back-end API that exposes two endpoints: `GET /health` for system status and `POST /data` to accept patient data and store it in a secure backend service.
3. Deploy both the front end and back end to a containerized environment, ensuring proper integration with the infrastructure set up in Task 1.
4. Use a CI/CD pipeline to automate the build, deployment, and configuration of both the front end and back end, ensuring proper handling of different environments (development, staging, production).
5. Use Git as the version control system to track changes in the codebase for both front-end and back-end applications.
6. Ensure every successful build in the CI pipeline generates a Git tag or version number.
7. Establish a rollback strategy in case of deployment failures.

---

## Step 3: API Management, Security, and Data Retrieval

### Task 3: API Management, Security, and Scheduled Data Retrieval

**Objective**: Secure the API and set up a scheduled data retrieval task.

**Resources Required**:
- Azure API Management (APIM) or an alternative gateway (e.g., KrakenD, Kong) for managing API security and traffic.
- Azure Functions or Logic Apps for scheduling tasks to retrieve and process data every 3 hours.
- Monitoring and alerting tools to observe API traffic and manage rate-limiting policies.

**Instructions**:
1. Secure the back-end API by implementing rate-limiting and throttling policies to protect against overuse. The system should reject excessive requests beyond the limit and return a custom error message.
2. Store incoming data from the `POST /data` endpoint in a secure backend service (e.g., SQL, PostgreSQL, Cosmos DB, or Azure Storage Account).
3. Implement a scheduled task that retrieves and processes the stored data every 3 hours using automation tools like Azure Functions, Logic Apps, or Azure Automation, and logs the execution to a file in a storage account named “logs”.
