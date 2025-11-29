# 📘 Library Management System — API Gateway

## 🚀 Overview
- Acts as the single entry point for all LMS services  
- Routes client requests to appropriate backend services  
- Handles authentication, authorization, logging, and rate limiting  
- Protects internal microservices behind a secure gateway layer  

---

## 🔑 Key Responsibilities
- **Authentication** – Validates JWT tokens and user identity  
- **Authorization** – Enforces Admin, Librarian, and Member permissions  
- **Unified Error Handling** – Provides consistent API responses  
- **Security** – CORS, rate limiting, request validation, TLS support  
- **Service Discovery Integration** – Auto-resolves internal service addresses  
- **Monitoring & Logging** – Tracing + structured logs  

---

## 🏗 Architecture
- Client  
  → **API Gateway**  
  → **Service Discovery**  
  → Backend Microservices (Books, Members, Circulation, etc.)  
- Works with:
  - Consul  
  - Eureka  

---

## ⚙️ Configuration
Set all values using environment variables.

Important environment variables:
- `PORT` – Gateway port  
- `DISCOVERY_URL` – Service Discovery URL  
- `JWT_ISSUER` – JWT issuer  
- `JWKS_URL` – JWKS public key endpoint  
- `RATE_LIMIT_MAX` – Max requests per minute  
- `REQUEST_TIMEOUT` – Timeout for backend service calls  

---

## 🔐 Security Best Practices
- Validate all JWT tokens at the gateway  
- Never expose internal microservices directly  
- Use HTTPS/TLS termination  
- Apply rate limiting to prevent abuse  
- Enforce least-privilege role permissions  
- Store secrets in Vault or Kubernetes Secrets (never in repo)  

---

## 📊 Observability
- Logs every request with correlation IDs  
- Exposes Prometheus `/metrics` endpoint  
- Supports distributed tracing headers (OpenTelemetry)  
- Provides `/health` endpoint for readiness/liveness  
