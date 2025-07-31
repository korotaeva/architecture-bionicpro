# Secure Reports Application with PKCE Authentication

## Overview
A modern web application demonstrating PKCE (Proof Key for Code Exchange) implementation to enhance OAuth 2.0 Authorization Code Flow security.

## System Architecture

| Component       | Technology       |
|----------------|------------------|
| Frontend       | React + TypeScript |
| Backend        | Node.js + Express |
| Authentication | Keycloak + PKCE   |

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

## Deployment Guide

### Prerequisites
- Docker 20.10+
- Docker Compose 1.29+
- Node.js 18+ (development only)

### Quick Start
```bash
docker-compose up --build