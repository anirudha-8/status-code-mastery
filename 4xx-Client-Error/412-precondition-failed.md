<h1 align="center">❗ 412 Precondition Failed</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-412-red?style=for-the-badge&logo=http" alt="412 Badge" />
  <img src="https://img.shields.io/badge/Type-Conditional%20Request%20Error-critical?style=for-the-badge&logo=alert-octagon" alt="Precondition Failed Badge" />
</p>

---

## 📖 Definition

The **412 Precondition Failed** status code means that **one or more conditions** specified  
in the request headers **were not met** by the server.

These conditions are typically expressed using **conditional headers**, such as:

- `If-Match`
- `If-None-Match`
- `If-Modified-Since`
- `If-Unmodified-Since`

> 💬 **In simple words:**  
> “Your request depends on a condition — and that condition failed.”

---

## 🧩 When Does 412 Occur?

A `412` error occurs when:

- Client sends conditional headers
- The condition does not match the current resource state
- Server refuses to perform the operation

This is commonly used to:

- Prevent accidental overwrites  
- Handle concurrent updates  
- Enforce optimistic locking  

---

## 💻 Example 1 — ETag Mismatch

**Client Request:**

```http
PUT /api/profile HTTP/1.1
If-Match: "v1"
```

Current resource ETag: "v2"

**Server Response:**

```http
HTTP/1.1 412 Precondition Failed

{
  "error": "Resource has been modified"
}
```

**🎯 Meaning:**

Client tried to update stale data.

---

## 💻 Example 2 — Conditional Delete Failed

```http
DELETE /api/post/42 HTTP/1.1
If-Unmodified-Since: Wed, 10 Jan 2024 10:00:00 GMT
```

But the resource was modified later.

**Response:**

```http
HTTP/1.1 412 Precondition Failed
```

---

🧠 Real-Life Analogy

You tell someone:

> “Only update this document if nobody touched it since yesterday.”

They check and say:

> “Sorry, it was updated today.”

That’s **412 Precondition Failed**.

---

## 🚀 Common Use Cases

| Scenario                | Why 412?                     |
| ----------------------- | ---------------------------- |
| Optimistic locking      | Prevent overwrites           |
| Concurrent updates      | Detect race conditions       |
| Safe deletes            | Avoid deleting modified data |
| Cache validation        | Conditional processing       |
| Version-controlled APIs | State consistency            |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 412 when:**

- Conditional headers are present

- Condition check fails

- Request is valid but unsafe to execute

**❌ Do NOT use 412 when:**

- Resource does not exist → 404 Not Found

- Conflict exists → 409 Conflict

- Validation fails → 422 Unprocessable Entity

---

## 🔥 Interview Tip

💬 Question:

> Difference between 409 and 412?

Answer:

- **409** → Conflict with resource state

- **412** → Conditional request failed

---

## 🧪 Express.js Example (ETag Check)

```js
app.put("/api/profile", (req, res) => {
    if (req.headers["if-match"] !== currentETag) {
        return res.status(412).json({
            error: "Precondition failed",
    });
  }

  // update resource
  res.json({ message: "Updated" });
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

- MDN Docs — 412 Precondition Failed

- RFC 9110 — Conditional Requests
