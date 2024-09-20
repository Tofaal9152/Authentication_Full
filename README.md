
# Important Concepts and Code Snippets

This document serves as a reference for key concepts and code snippets that are useful in various web development scenarios, particularly when working with Next.js, JWTs, and handling requests.

## 1. **Setting Headers**

To set a custom header in a response:

```javascript
res.headers.set('xUserId', payload.userId);
```

### Explanation:
- **`xUserId`**: A custom header that stores the user ID from the JWT payload.
- **`payload.userId`**: The user ID extracted from the JWT payload.

## 2. **JWT Verification**

To verify a JWT using the `jwtVerify` function:

```javascript
const secret = new TextEncoder().encode(process.env.JWT_TOKEN);
const { payload } = await jwtVerify(token, secret);
```

### Explanation:
- **`secret`**: The encoded JWT secret from the environment variable `JWT_TOKEN`.
- **`jwtVerify`**: Verifies the provided `token` using the `secret` and returns the decoded payload.

## 3. **Getting Token from Cookies**

To retrieve a token from the request cookies:

```javascript
const token = req.cookies.get('token')?.value;
```

### Explanation:
- **`req.cookies.get('token')`**: Retrieves the cookie named `token`.
- **`?.value`**: Safely accesses the value of the cookie if it exists.

## 4. **Getting the User ID from Headers**

To extract a custom user ID from the request headers:

```javascript
const userId = req.headers.get("xUserId");
```

### Explanation:
- **`xUserId`**: The custom header containing the user ID.

## 5. **Handling Dynamic Routing in Next.js**

To get the dynamic `[id]` parameter from the URL:

```javascript
const _id = req.nextUrl.pathname.split('/').pop();
```

### Explanation:
- **`req.nextUrl.pathname`**: The full path of the current URL.
- **`.split('/').pop();`**: Splits the path into segments and retrieves the last segment, which is typically the dynamic ID.

## 6. **Extracting Keywords from the URL**

To extract query parameters (e.g., keywords) from the request URL:

```javascript
const { searchParams } = new URL(req.url);
const keyword = searchParams.get('keyword') || "";
```

### Explanation:
- **`new URL(req.url)`**: Parses the request URL.
- **`searchParams.get('keyword')`**: Retrieves the value of the `keyword` query parameter.
- **`|| ""`**: Provides a default empty string if the keyword is not present.
