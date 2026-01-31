# Track Server API Specification

## Overview
**Responsibility**: High-volume event ingestion (Clicks, Beacons).
**Role Access**: Public / Anonymous (Service-to-Service or Client-to-Service).
**Base URL**: 
- DEV: `http://localhost:5002`
- PROD: `https://foundry-track.onrender.com` (Estimated)

## Authentication
- **Method**: None (Public Ingestion) or Service Headers (Future).
- **Current**: Publicly accessible for `visit_id` confirmation.

## Endpoints

### Ingestion
- `POST /track/visit-confirm`
  - **Purpose**: Confirms a visit/click event using a generated ID.
  - **Body**: `{ "visit_id": "uuid-string" }`
  - **Response**: `{ "status": "queued" }`
  - **Behavior**: Async separation (Queues event, returns 200 OK immediately).

### Health
- `GET /health`
  - **Response**: `OK`

## Error Format
```json
{
  "error": "Error message"
}
```
