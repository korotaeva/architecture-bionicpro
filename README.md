# Secure Reports Application with PKCE Authentication

## Overview
A modern web application demonstrating PKCE (Proof Key for Code Exchange) implementation to enhance OAuth 2.0 Authorization Code Flow security.

## System Architecture

| Component       | Technology         |
|----------------|--------------------|
| Frontend       | React + TypeScript |
| Backend        | JAVA         |
| Authentication | Keycloak + PKCE    |

## Key Components

### 1. PKCE Security Layer
- `code_verifier` generation (random string)
- `code_challenge` creation (SHA-256 hash)
- Secure session storage management
- Keycloak PKCE flow integration

### 2. Backend Services
- JWT validation middleware
- Role-based access control (`prothetic_user`)
- Mock report data generation
- Authentication/authorization handlers

### 3. Frontend Application
- Keycloak PKCE integration
- Report visualization interface
- Authentication error handling

### Quick Start
```bash
docker-compose up --build