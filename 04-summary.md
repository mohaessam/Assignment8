# Summary

| Term | Meaning |
|---|---|
| Token | A value used to identify/authenticate a client in later requests |
| Bearer Token | A token sent through the Authorization header using the `Bearer` scheme |
| Authentication | Verifying the identity of a user |
| Authorization | Determining what an authenticated user is allowed to access |

## Example

```http
GET /profile
Authorization: Bearer <token>
```

The server receives the request, extracts the token, verifies it, and then decides whether the user can access the protected resource.
