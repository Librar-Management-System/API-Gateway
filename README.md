🚀 Overview

Acts as the single entry point for all LMS services.
Routes client requests to appropriate backend services.
Handles authentication, authorization, logging, and rate limiting.
Protects internal microservices behind a secure gateway layer.

🔑 Key Responsibilities

Authentication → Validates JWT tokens, checks user roles.
Authorization → Enforces Admin, Librarian, Member permissions.
Unified Error Handling → Consistent API responses.
Security → CORS, rate limiting, request validation, TLS.
Service Discovery Integration → Auto-resolves internal service addresses.
Monitoring & Logging → Tracing + structured logs.

🏗 Architecture

Client → API Gateway → Service Discovery → Individual microservices.
Works with Consul / Eureka / Kubernetes Service Discovery.

⚙️ Configuration

Set all configs using environment variables.
Important environment values:
PORT – Gateway port
DISCOVERY_URL – Service Discovery URL
JWT_ISSUER, JWKS_URL – Auth settings
RATE_LIMIT_MAX – Max requests per minute
REQUEST_TIMEOUT – Timeout for backend calls


🔐 Security Best Practices

Validate all tokens at the gateway
Never expose internal services directly
Use HTTPS / TLS termination
Rate limiting to prevent abuse
Apply least-privilege route permissions
Store secrets in vault or K8s secrets (not in repo)

📊 Observability

Logs every request with correlation IDs
Exposes Prometheus metrics
Supports distributed tracing headers (OpenTelemetry)
Provides /health endpoint for monitoring
