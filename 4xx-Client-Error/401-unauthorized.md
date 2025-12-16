<h1 align="center">🔐 401 Unauthorized</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-401-red?style=for-the-badge&logo=http" alt="401 Badge" />
  <img src="https://img.shields.io/badge/Type-Authentication%20Error-critical?style=for-the-badge&logo=lock" alt="Authentication Error Badge" />
</p>

---

## 📖 Definition

The **401 Unauthorized** status code means that the request **lacks valid authentication credentials**  
for the target resource.

The server understands the request, but **refuses to fulfill it** because the client:

- Is **not authenticated**, or
- Provided **invalid/expired credentials**

> 💬 **In simple words:**  
> “Who are you? Please authenticate first.”

---

## 🧩 When Does 401 Occur?

A `401` is returned when:

- No authentication token is provided  
- Token is invalid, expired, or malformed  
- Username/password is incorrect  
- API key is missing or wrong  

⚠️ **Important:**  
401 is about **authentication**, not permission.

---

## 💻 Example 1 — Missing Token

**Client Request:**

```http
GET /api/profile HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 401 Unauthorized
WWW-Authenticate: Bearer
```

**🎯 Meaning:**

Authentication is required, but no credentials were sent.

---

## 💻 Example 2 — Invalid JWT Token

```http
GET /api/profile HTTP/1.1
Authorization: Bearer invalid_token_here
```

**Response:**

```http
HTTP/1.1 401 Unauthorized
Content-Type: application/json

{
  "error": "Invalid or expired token"
}
```

---

## 🧠 Real-Life Analogy

You try to enter a private office building 🏢
The guard asks:

> “ID card, please.”

You either:

Don’t have one ❌

Show an expired one ❌

That’s **401 Unauthorized**.

---

## 🚀 Common Use Cases

| Scenario                | Why 401?              |
| ----------------------- | --------------------- |
| Accessing protected API | No auth token         |
| Expired session         | Token timed out       |
| Invalid credentials     | Wrong password        |
| API key missing         | Authentication failed |
| OAuth failure           | Invalid access token  |

---

## ⚙️ Developer Notes (Very Important)

### ✅ Use 401 when

- Authentication is missing or invalid

- User is not logged in

- Token/session is expired

### ❌ Do NOT use 401 when

- User is authenticated but not allowed → use 403 Forbidden

### 401 vs 403 (Interview Gold ⭐)

| Code    | Meaning                                    |
| ------- | ------------------------------------------ |
| **401** | You are **not authenticated**              |
| **403** | You are authenticated, but **not allowed** |

---

## 🧪 Example — Express.js Auth Middleware

```js
function authMiddleware(req, res, next) {
  const token = req.headers.authorization;

  if (!token) {
    return res.status(401).json({
      error: "Authentication required",
    });
  }

  // validate token...
  next();
}
```

---

## 🔗 Related Codes

- [400 Bad Request](./400-bad-request.md)❌

- [401 Unauthorized](./401-unauthorized.md)🔐

- [403 Forbidden](./403-forbidden.md)🚫

- [404 Not Found](./404-not-found.md)🔍

- [405 Method Not Allowed](./405-method-not-allowed.md)🧱

- [406 Not Acceptable](./406-not-acceptable.md)🎭

- [407 Proxy Authentication Required](./407-proxy-authentication-required.md)🖧

- [408 Request Timeout](./408-request-timeout.md)⏱️

- [409 Conflict](./409-conflict.md)⚔️

- [410 Gone](./410-gone.md)🗑️
  
- [411 Length Required](./411-length-required.md)📏

- [412 Precondition Failed](./412-precondition-failed.md)❗

- [413 Payload Too Large](./413-payload-too-large.md)📦

- [414 URI Too Long](./414-uri-too-long.md)🔗

- [415 Unsupported Media Type](./415-unsupported-media-type.md)🧪

- [416 Range Not Satisfiable](./416-range-not-satisfiable.md)📉

- [417 Expectation Failed](./417-expectation-failed.md)🤔

- [418 I'm a Teapot](./418-im-a-teapot.md)🫖

- [422 Unprocessable Entity](./422-unprocessable-entity.md)🧠

- [429 Too Many Requests](./429-too-many-requests.md)🚦

- [431 Request Header Fields Too Large](./431-request-header-fields-too-large.md)📜

- [451 Unavailable For Legal Reasons](./451-unavailable-for-legal-reasons.md)⚖️

---

## 📚 References

- MDN Docs — 401 Unauthorized

- RFC 9110 — Authentication Challenges
