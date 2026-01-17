<h1 align="center">🚧 501 Not Implemented</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-501-orange?style=for-the-badge&logo=http" alt="501 Badge" />
  <img src="https://img.shields.io/badge/Type-Server%20Capability-critical?style=for-the-badge&logo=tool" alt="Not Implemented Badge" />
</p>

---

## 📖 Definition

The **501 Not Implemented** status code means that the server **does not support the functionality**  
required to fulfill the request.

This usually indicates that:

- The **HTTP method** is not supported, or
- The **feature/endpoint** is recognized but **not implemented yet**

> 💬 **In simple words:**  
> “I understand what you’re asking, but I don’t know how to do it.”

---

## 🧩 When Does 501 Occur?

A `501` error occurs when:

- An HTTP method is not supported by the server  
- A new feature is planned but not implemented  
- A server acts as a gateway and doesn’t support upstream behavior  
- Experimental or deprecated methods are used  

⚠️ This is about **server capability**, not overload or downtime.

---

## 💻 Example 1 — Unsupported HTTP Method

**Client Request:**

```http
BREW /coffee HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 501 Not Implemented
```

**🎯 Meaning:**

The server does not recognize or support the BREW method.

---

## 💻 Example 2 — Feature Not Implemented Yet

```http
POST /api/payments HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 501 Not Implemented

{
  "message": "Payment processing is not supported yet"
}
```

---

## 🧠 Real-Life Analogy

You ask a carpenter 🪚:

> “Can you build a spaceship?”

The carpenter replies:

> “I understand what that is — but I can’t do it.”

That’s 501 Not Implemented.

---

## 🚀 Common Use Cases

| Scenario                 | Why 501?                      |
| ------------------------ | ----------------------------- |
| Unsupported HTTP methods | Server capability missing     |
| Feature flags            | Feature planned but not built |
| API placeholders         | Endpoint stub                 |
| Gateway limitations      | Upstream not supported        |
| Experimental APIs        | Not available yet             |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 501 when:**

- Server does not support the requested method or feature

- Capability is missing, not temporarily unavailable

**❌ Do NOT use 501 when:**

- Server is overloaded → 503 Service Unavailable

- Dependency fails → 502 Bad Gateway

- Endpoint exists but method is invalid → 405 Method Not Allowed

- Feature exists but access is denied → 403 Forbidden

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 501 and 405?

**Answer:**

- **501** → Server does not support the method at all

- **405** → Method is supported by server, but not for this endpoint

---

## 🧪 Express.js Example (Not Implemented)

```js
app.post("/api/payments", (req, res) => {
  res.status(501).json({
    message: "Payments are not implemented yet",
  });
});
```

---

## 🔗 Related Codes

- [500 Internal Server Error](./500-internal-server-error.md)💥

- [501 Not Implemented](./501-not-implemented.md)🚧

- [502 Bad Gateway](./502-bad-gateway.md)🔌

- [503 Service Unavailable](./503-service-unavailable.md)🛑

- [504 Gateway Timeout](./504-gateway-timeout.md)⏳

- [505 HTTP Version Not Supported](./505-http-version-not-supported.md)🌐

---

## 📚 References

- MDN Docs — 501 Not Implemented

- RFC 9110 — Server Error Responses
