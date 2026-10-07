# 2. Bearer Token

A Bearer Token is a token sent in the HTTP Authorization header.

The standard format is:

```http
Authorization: Bearer <token>
```

For example:

```http
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

The word `Bearer` tells the server that the value following it is an access token.

## Example with JavaScript

```js
fetch("http://localhost:3000/profile", {
    headers: {
        Authorization: `Bearer ${token}`
    }
});
```

## Example in Express

```js
app.get("/profile", (req, res) => {
    const authHeader = req.headers.authorization;

    if (!authHeader) {
        return res.status(401).json({
            message: "Authorization header is required"
        });
    }

    const token = authHeader.split(" ")[1];

    console.log(token);

    res.json({
        message: "Token received"
    });
});
```

## Important

The token should be sent over HTTPS in a real application. A token should also be protected because anyone who possesses a valid bearer token may be able to use it until it expires or is revoked.
