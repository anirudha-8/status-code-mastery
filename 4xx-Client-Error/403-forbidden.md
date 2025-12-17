<h1 align="center">🚫 403 Forbidden</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-403-red?style=for-the-badge&logo=http" alt="403 Badge" />
  <img src="https://img.shields.io/badge/Type-Authorization%20Error-critical?style=for-the-badge&logo=shield-x" alt="Authorization Error Badge" />
</p>

---

## 📖 Definition

The **403 Forbidden** status code means that the server **understands the request**  
and the client **is authenticated**, but **does not have permission** to access the resource.

> 💬 **In simple words:**  
> “I know who you are — but you’re not allowed to do this.”

---

## 🧩 When Does 403 Occur?

A `403 Forbidden` error happens when:

- User is logged in but lacks required role/permission  
- Accessing admin-only or restricted resources  
- IP address is blocked  
- Rate limits or security rules deny access  
- Server explicitly forbids the action  

⚠️ Authentication is **not the issue** here — authorization is.

---

## 💻 Example 1 — Insufficient Permissions

**Client Request:**

```http
DELETE /api/users/10 HTTP/1.1
Authorization: Bearer valid_admin_token
```

**Server Response:**

```http
HTTP/1.1 403 Forbidden

{
  "error": "You do not have permission to delete users"
}
```

**🎯 Meaning**:

User is authenticated, but lacks delete privileges.

---

## 💻 Example 2 — Accessing Admin Route as Normal User

```http
GET /admin/dashboard HTTP/1.1
Authorization: Bearer user_token
```

**Response**:

```http
HTTP/1.1 403 Forbidden
```

---

## 🧠 Real-Life Analogy

You enter an office building with a valid ID 🏢
You try to open the CEO’s cabin 🚪

Security says:

> “You’re allowed in the building — but not in this room.”

That’s 403 Forbidden.

---

## 🚀 Common Use Cases

| Scenario                  | Why 403?           |
| ------------------------- | ------------------ |
| Role-based access control | Missing permission |
| Admin-only endpoints      | Non-admin user     |
| IP restriction            | Blocked location   |
| Feature flags             | Access disabled    |
| Legal / compliance rules  | Access prohibited  |

---

## ⚙️ Developer Notes (Very Important)

### ✅ Use 403 when

- User is authenticated

- Server knows who the user is

- Access is intentionally blocked

### ❌ Do NOT use 403 when

- Authentication is missing → 401 Unauthorized

- Resource does not exist → 404 Not Found

### 401 vs 403 (Interview Favorite ⭐)

| Code    | Meaning                                       |
| ------- | --------------------------------------------- |
| **401** | Who are you? (Authentication missing/invalid) |
| **403** | I know you, but you can’t access this         |

---

## 🧪 Example — Role-Based Middleware (Express.js)

```js
function adminOnly(req, res, next) {
  if (req.user.role !== "admin") {
    return res.status(403).json({
      error: "Admin access required",
    });
  }
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

- MDN Docs — 403 Forbidden

- RFC 9110 — Authorization Semantics
