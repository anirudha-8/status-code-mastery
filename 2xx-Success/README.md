<h1 align="center">💚 2xx - Success Responses</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Category-Success-green?style=for-the-badge&logo=http" alt="2xx Success Badge" />
  <img src="https://img.shields.io/badge/HTTP%20Status%20Codes-2xx-brightgreen?style=for-the-badge&logo=googlechrome" alt="HTTP 2xx Codes" />
</p>

---

## 🧠 What Are 2xx Success Codes?

These codes indicate that the **client’s request was successfully received, understood, and accepted** by the server.  
They represent *success* in the HTTP world 🌍✨

> 💬 Think of them as: “🎉 Request completed — everything went smoothly!”

---

## 🧩 Quick Summary

| Code | Name | Description |
|------|------|--------------|
| [200 OK](./200-ok.md) | ✅ OK | The request was successful, and the response body contains the result. |
| [201 Created](./201-created.md) | 🏗️ Created | The request has been fulfilled, and a new resource has been created. |
| [202 Accepted](./202-accepted.md) | ⏳ Accepted | The request has been accepted but not yet processed. |
| [203 Non-Authoritative Information](./203-non-authoritative-information.md) | 🧾 Partial Info | The response was modified by a proxy or intermediary. |
| [204 No Content](./204-no-content.md) | 🚫 No Content | The request succeeded but there’s nothing to send back. |
| [205 Reset Content](./205-reset-content.md) | 🔄 Reset | The client should reset its view or form data. |
| [206 Partial Content](./206-partial-content.md) | 📦 Partial Content | The server is delivering only part of the resource (range requests). |
| [207 Multi-Status](./207-multi-status.md) | 🧩 Multi-Status | Multiple status codes might apply (mainly for WebDAV). |
| [208 Already Reported](./208-already-reported.md) | 🔁 Already Reported | The resource is already reported in a previous response. |
| [226 IM Used](./226-im-used.md) | 🧮 IM Used | The server has fulfilled a GET request using instance-manipulations. |

---

## 💻 Common Examples

### 🧩 Example 1: 200 OK

```http
GET /api/users HTTP/1.1
Host: example.com
```

Response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": 1,
  "name": "Anirudha Bele",
  "role": "Frontend Developer"
}
```

✅ Meaning: Request succeeded and returned expected data.

### 🧩 Example 2: 201 Created

```http
POST /api/users HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "name": "Anirudha",
  "email": "anirudha@example.com"
}
```

Response:

```http
HTTP/1.1 201 Created
Location: /api/users/10
```

🏗️ Meaning: A new resource (user) was successfully created on the server.

### 🧩 Example 3: 204 No Content

```http
DELETE /api/users/10 HTTP/1.1
Host: example.com
```

Response:

```http
HTTP/1.1 204 No Content
```

🚫 Meaning: Request succeeded, but there’s no response body to send back.

---

## 🧠 Real-Life Analogy

Think of a food delivery app 🍱:

- You place an order (request).

- You get confirmation and your food arrives (✅ success).

- That’s your 2xx — mission accomplished!

---

## 🚀 Common Use Cases

| Code | Real-World Use                                     |
| ---- | -------------------------------------------------- |
| 200  | Data retrieval (GET requests).                     |
| 201  | Creating users, products, or posts via POST.       |
| 204  | Deleting resources cleanly.                        |
| 206  | Streaming or range-based downloads (e.g., videos). |

---

## ⚙️ Developer Tips

- 2xx codes always mean your request succeeded (functionally).

- Not all 2xx codes return a body — e.g., 204 No Content.

- For REST APIs:

  - POST → 201 Created

  - GET → 200 OK

  - DELETE → 204 No Content

- Use appropriate 2xx codes — don’t send 200 OK for every action!

---

## 🔗 Related RFC References

- [RFC 9110 – HTTP Semantics (IETF)](https://datatracker.ietf.org/doc/html/rfc9110#section-15.3)

- [MDN Web Docs – HTTP 2xx Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status#successful_responses)
