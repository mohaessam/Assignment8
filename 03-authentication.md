# 3. Authentication

Authentication is the process of verifying the identity of a user.

For example, when a user logs in using an email and password, the server checks whether those credentials belong to a registered user.

## Authentication vs Authorization

### Authentication
Answers:

> Who are you?

Example:
A user logs in with email and password.

### Authorization
Answers:

> What are you allowed to do?

Example:
A normal user can read their profile, while an admin can delete users.

## Common authentication flow

```text
Register
   ↓
Login
   ↓
Server verifies credentials
   ↓
Server generates token
   ↓
Client sends token with protected requests
   ↓
Server verifies token
   ↓
Access granted
```

## Example

```js
app.post("/login", async (req, res) => {
    const { email, password } = req.body;

    // Find user in database
    // Compare password
    // Generate authentication token

    res.json({
        message: "Login successful",
        token: "example-token"
    });
});
```

## Protecting a route

A middleware can check the token before allowing the request to continue:

```js
function authMiddleware(req, res, next) {
    const authHeader = req.headers.authorization;

    if (!authHeader) {
        return res.status(401).json({
            message: "Unauthorized"
        });
    }

    const token = authHeader.split(" ")[1];

    if (!token) {
        return res.status(401).json({
            message: "Token is required"
        });
    }

    // Verify token here

    next();
}

app.get("/profile", authMiddleware, (req, res) => {
    res.json({
        message: "Profile data"
    });
});
```

## HTTP status codes

- `200` - Request succeeded
- `401` - Authentication is required or credentials/token are invalid
- `403` - User is authenticated but does not have permission
