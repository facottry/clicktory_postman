# App Server API Specification

## Overview
**Responsibility**: Main customer-facing application backend.
**Role Access**: Public (unauthenticated) and Founder/Customer (authenticated).
**Base URL**: 
- DEV: `http://localhost:5000`
- PROD: `https://foundry-app.onrender.com` (Estimated)

## Authentication
- **Method**: Bearer Token (JWT).
- **Header**: `Authorization: Bearer <token>`

## Core Entities & Routes

### Auth
- `POST /api/auth/signup` - Register new founder.
- `POST /api/auth/login` - Login.

### Public Discovery
- `GET /api/products` - Search/List products (Public).
- `GET /api/products/:id` - View product detail.
- `GET /api/categories` - List categories.

### Founder Dashboard (Protected)
- `GET /api/founder/dashboard` - Main metrics (clicks, spend).
- `GET /api/founder/products` - List my products.
- `POST /api/products` - Create new product.
- `GET /api/wallet/balance` - Check credit balance.
- `GET /api/wallet/transactions` - Transaction history.

### Traffic & Analytics
- `GET /r/:productId` - Outbound redirect (Tracks click).
- `POST /api/clicks/confirm` - Confirmation beacon (Anti-fraud).

## Response Format
```json
{
  "success": true,
  "data": { ... }
}
```

## Error Format
```json
{
  "success": false,
  "error": "ERROR_CODE",
  "message": "Friendly message"
}
```
