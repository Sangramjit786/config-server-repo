# Config Server Repository for SpringBoot Microservices

This repository contains **externalized configuration files** (`.properties` and `.yml`) for different Spring Boot microservices used in the [springboot-banking-services](https://github.com/Sangramjit786/springboot-banking-services.git) and other microservice projects.  

These configurations are managed by **Spring Cloud Config Server**, which allows all microservices to fetch their environment-specific configuration dynamically at runtime.  

---

## 📂 Repository Purpose
- Centralized configuration management for microservices.  
- Separate configuration files for each service.  
- Environment-specific files for **DEV, QA, PROD**.  
- Supports both `.properties` and `.yml` formats.  
- Enables **dynamic refresh** of configs without redeploying services.  

---

## ⚙️ Configurations Explained

### 1) **Department Service**
- **File:** `department-service.properties`
- Initial creation and multiple updates:
  - Added basic department-service configuration.
  - Introduced **service messages**.
  - Updated messages multiple times to reflect changes.
- Purpose: Demonstrates how service-specific configs can be changed without modifying code.

---

### 2) **Employee Service**
- **File:** `employee-service.properties`
- Added as an externalized config file.
- Updates included:
  - Added **employee-service message**.
  - Updated/modified the message multiple times.
- Purpose: Shows real-time propagation of config changes to employee-service.

---

### 3) **Organization Service**
- **File:** `organization-service.properties`
- Created to store `organization-service` configs.
- Purpose: New service support added to the centralized repo.

---

### 4) **Accounts Service**
- Files created:
  - `accounts.yml` → Default config.  
  - `accounts-prod.yml` → Production-specific configs.  
  - `accounts-qa.yml` → QA-specific configs.  
- Updates:
  - Modified `accounts-prod.yml` to reflect production changes.
- Purpose: Demonstrates environment-specific configs for **accounts** microservice.

---

### 5) **Cards Service**
- Files created:
  - `cards.yml` → Default config.  
  - `cards-prod.yml` → Production-specific configs.  
  - `cards-qa.yml` → QA-specific configs.  
- Updates:
  - Modified `cards-prod.yml` with new configuration values.
- Purpose: Showcases environment-driven configuration flexibility.

---

### 6) **Loans Service**
- Files created:
  - `loans.yml` → Default config.  
  - `loans-prod.yml` → Production-specific configs.  
  - `loans-qa.yml` → QA-specific configs.  
- Updates:
  - Modified `loans-prod.yml` for updated production configuration.
- Purpose: Illustrates environment management for **loans microservice**.

---

### 7) **Gateway Server**
- **File:** `gatewayserver.yml`
- Created to manage routing and gateway properties.
- Purpose: Centralized gateway configs to control microservice routing.

---

### 8) **Eureka Server**
- **File:** `eurekaserver.yml`
- Created to configure Eureka discovery server.
- Purpose: Centralized service discovery configs.

---

## 🌍 Environment Strategy
Each service may have:  
- **Default config** (`<service>.yml` or `<service>.properties`)  
- **QA config** (`<service>-qa.yml`)  
- **PROD config** (`<service>-prod.yml`)  

This structure ensures:
- **Isolation of environments** (Dev, QA, Prod).  
- **Easy overrides** based on environment profiles.  
- **No code change required** → just update config in repo.  

---

## 🔄 Dynamic Updates
- Configs in this repo can be updated at runtime.  
- Microservices using `@RefreshScope` can fetch new configs dynamically after triggering:
  ```bash
  curl -X POST http://<service-url>/actuator/refresh
  ```
- Ensures faster delivery without redeployment.

## ✅ Benefits

- Centralized configuration management.
- Environment-specific support.
- Easy updates without code changes.
- Version-controlled (Git) → full audit history.
- Reduces duplication by externalizing configs.

## 📌 Next Steps

- Secure sensitive configs using Spring Cloud Vault or Kubernetes Secrets.
- Add DevOps automation to sync config updates across environments.
- Enable Spring Cloud Bus with Kafka or RabbitMQ to broadcast refresh events automatically.
