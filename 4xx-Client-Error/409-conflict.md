<h1 align="center">⚔️ 409 Conflict</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-409-red?style=for-the-badge&logo=http" alt="409 Badge" />
  <img src="https://img.shields.io/badge/Type-Resource%20Conflict-critical?style=for-the-badge&logo=alert-triangle" alt="Conflict Error Badge" />
</p>

---

## 📖 Definition

The **409 Conflict** status code means that the request **could not be completed**  
because it **conflicts with the current state of the resource** on the server.

The request itself is valid, but executing it would cause a **data or state conflict**.

> 💬 **In simple words:**  
> “Your request clashes with what already exists.”

---

## 🧩 When Does 409 Occur?

A `409 Conflict` occurs when:

- Creating a resource that already exists  
- Updating stale data (version mismatch)  
- Concurrent updates cause collision  
- Violating unique constraints  
- Duplicate operations  

⚠️ This is **not** a syntax error — it’s a **state problem**.

---

## 💻 Example 1 — Duplicate Resource Creation

**Client Request:**

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "email": "anirudha@example.com"
}
```

**Server Response:**

```http
HTTP/1.1 409 Conflict

{
  "error": "User with this email already exists"
}
```

**🎯 Meaning:**

The email must be unique — the resource already exists.

---

## 💻 Example 2 — Version Conflict (Optimistic Locking)

**Client Request:**

```http
PUT /api/profile HTTP/1.1
If-Match: "v1"
```

But the current version is: `v2`

**Response:**

```http
HTTP/1.1 409 Conflict

{
  "error": "Profile was updated by another user"
}
```

---

## 🧠 Real-Life Analogy

Two people try to book the same movie seat 🎬 at the same time.

The first booking succeeds.
The second gets told:

> “Sorry, that seat is already taken.”

That’s **409 Conflict**.

---

## 🚀 Common Use Cases

| Scenario                 | Why 409?                       |
| ------------------------ | ------------------------------ |
| Duplicate email/username | Unique constraint violated     |
| Concurrent updates       | Data version mismatch          |
| Booking systems          | Resource already reserved      |
| Inventory updates        | Stock conflict                 |
| Git merge conflicts      | Same concept, different domain |

---

## ⚙️ Developer Notes (Very Important)

### ✅ Use 409 when

- Request is valid

- Resource state prevents execution

- Conflict can be resolved by client

### ❌ Do NOT use 409 when

- Input is invalid → **400 Bad Request**

- Authentication issue → **401 Unauthorized**

- Authorization issue → **403 Forbidden**

- Resource not found → **404 Not Found**

---

## 🔥 Interview Tip

**💬 Question:**

> When should you use 409 vs 422?

**Answer:**

- **409** → Conflict with existing resource/state

- **422** → Validation failed on semantically correct request

---

## 🧪 Express.js Example

```js
app.post("/api/users", (req, res) => {
  const existingUser = users.find(u => u.email === req.body.email);

  if (existingUser) {
    return res.status(409).json({
      error: "User already exists",
    });
  }

  res.status(201).json({ message: "User created" });
});
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

- MDN Docs — 409 Conflict

- RFC 9110 — Client Error Semantics
