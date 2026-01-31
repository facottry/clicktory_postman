# Admin Server API Specification

## Overview
**Responsibility**: Backend for the Internal Admin Dashboard.
**Role Access**: Strictly restricted to users with `role: 'ADMIN'`.
**Base URL**: 
- DEV: `http://localhost:5001`
- PROD: `https://foundry-admin.onrender.com` (Estimated)

## Authentication
- **Method**: Bearer Token (JWT).
- **Header**: `Authorization: Bearer <token>`P
- **Login Flow**: 
  1. Standard Email/Password Login -> Returns JWT.
  2. OTP Flow (Login with OTP, Send OTP) -> Returns JWT.

## Entities

### User
- **Fields**: `name`, `email`, `role`, `credits_balance`, `created_at`.
- **Operations**: List (paginated, sortable, filterable), Get Detail (with stats).

### Product
- **Fields**: `name`, `tagline`, `status`, `traffic_enabled`, `owner_user_id`.
- **Operations**: List (paginated, sortable, search), Get Detail (with expanded stats), Approve.

### Personality (AI)
- **Fields**: `name`, `tone`, `greeting`, `isActive`, `defaultMode`.
- **Operations**: CRUD, Activate.

### Configuration
- **Purpose**: System-wide feature flags and AI cron settings.
- **Operations**: Get/Set Generic Configs, Get/Set AI Newsletter Config.

## Response Format
Standard JSON wrapper:
```json
{
  "success": true,
  "data": { ... }
}
```
OR (Legacy/Direct)
```json
{
  "field": "value"
}
```
*Note: Some endpoints return direct objects/lists (e.g., Personalities List).*

## Error Format
```json
{
  "success": false,
  "error": "ERROR_CODE",
  "message": "Human readable message"
}
```
