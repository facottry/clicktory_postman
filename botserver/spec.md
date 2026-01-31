# Bot Server API Specification

## Overview
**Responsibility**: AI Intelligence Layer for REX and AIRA personas.
**Role Access**: Authenticated Users (via Token forwarded from Client).
**Base URL**: 
- DEV: `http://localhost:5003`
- PROD: `https://foundry-bot.onrender.com` (Estimated)

## Authentication
- **Method**: Bearer Token (JWT from App Server).
- **Header**: `Authorization: Bearer <token>`
- **Note**: Botserver verifies token signature but does not issue tokens.

## Endpoints

### Session
- `POST /api/session/start`
  - **Body**: `{ "mode": "mini" | "full" }`
  - **Response**: `{ "sessionId": "...", "greeting": "..." }`

### Persona Intelligence
- `POST /api/persona/ask`
  - **Body**: 
    ```json
    {
      "query": "User question here",
      "persona": "REX" | "AIRA" | null, // Optional, auto-routed if null
      "productId": "optional-product-id"
    }
    ```
  - **Response**: 
    ```json
    {
      "persona": "REX",
      "answer": "Answer text...",
      "confidence": 0.9,
      "source": ["record_type"],
      "notes": "..."
    }
    ```

## Error Format
```json
{
  "persona": null,
  "answer": "Error message...",
  "confidence": 0.0
}
```
