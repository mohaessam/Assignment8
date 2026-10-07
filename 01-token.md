# 1. Token

A Token is a piece of information that is used to identify or authorize a user or client when communicating with a server.

Instead of sending sensitive information such as a password with every request, the client can receive a token after a successful login and use that token in later requests.

## Basic flow

1. The user sends email and password to the login endpoint.
2. The server checks the credentials.
3. If they are correct, the server generates a token.
4. The client stores the token.
5. The client sends the token with protected requests.
6. The server checks the token before allowing access.

## Example

```js
app.post("/login", (req, res) => {
    // Check user credentials
    // Generate token
    // Return token to the client
});
```

## Why use tokens?

- They allow the server to identify the client.
- They can protect private API endpoints.
- They are commonly used in REST APIs.
- They reduce the need to send the user's password repeatedly.

A common implementation is a JWT (JSON Web Token).
