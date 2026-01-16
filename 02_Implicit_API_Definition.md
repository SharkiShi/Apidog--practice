# How to Work with Our User and Settings APIs

This guide walks you through two common API operations you'll need when integrating with our platform. Each section includes the endpoint details, expected parameters, and practical examples you can copy and paste.

---

## Getting a User Profile

To retrieve user information, you'll need to call the `GET /api/v1/users/{id}` endpoint. This is useful when you need to display user details in your dashboard or mobile application.

### Request Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `id` | string | The unique identifier of the user to retrieve |
| `details` | boolean | Set to `true` to include extended profile information |
| `format` | string | Response format - use `json` or `xml` |

### Example Response

When you call this endpoint, here's what a successful response looks like:

```json
{
  "id": "usr_12345",
  "username": "alex_developer",
  "email": "alex@example.com",
  "created_at": "2024-03-15T10:30:00Z",
  "last_login": "2024-11-20T14:22:00Z",
  "profile": {
    "full_name": "Alex Developer",
    "avatar_url": "https://cdn.example.com/avatars/usr_12345.png",
    "bio": "Full-stack developer and API enthusiast"
  }
}
```

---

## Updating User Settings

If you need to modify a user's preferences, use the `POST /api/v1/settings` endpoint. This allows your application to persist user choices across sessions.

### Request Body Parameters

- `theme`: Specifies the UI appearance - use `dark` or `light`
- `language`: Two-letter locale code such as `en`, `es`, `fr`, or `de`
- `notifications_enabled`: Boolean flag to control push notifications
- `timezone`: IANA timezone string like `America/New_York` or `Europe/London`

### Example Request

Here's a cURL command you can use to test this endpoint from your terminal:

```bash
curl -X POST https://api.example.com/api/v1/settings \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -d '{
    "theme": "dark",
    "language": "en",
    "notifications_enabled": true,
    "timezone": "America/New_York"
  }'
```

This request updates the user's settings to match the values in the JSON body. Remember to replace `YOUR_API_TOKEN` with your actual authentication token.
