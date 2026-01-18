<h1 align="center">🛑 503 Service Unavailable</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-503-orange?style=for-the-badge&logo=http" alt="503 Badge" />
  <img src="https://img.shields.io/badge/Type-Temporary%20Failure-critical?style=for-the-badge&logo=alert-triangle" alt="Service Unavailable Badge" />
</p>

---

## 📖 Definition

The **503 Service Unavailable** status code means that the server  
**is currently unable to handle the request**, but **may become available again later**.

This is a **temporary condition**, unlike many other 5xx errors.

> 💬 **In simple words:**  
> “The server is down or overloaded right now — please try again later.”

---

## 🧩 When Does 503 Occur?

A `503` error occurs when:

- Server is overloaded (high traffic)
- Server is temporarily down for maintenance
- Application instances are restarting
- Database or dependency is temporarily unavailable
- Autoscaling has not yet caught up

⚠️ This error is **temporary by design**.

---

## 💻 Example 1 — Maintenance Mode

**Client Request:**

```http
GET /api/products HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 503 Service Unavailable
Retry-After: 120
```

🎯 Meaning:

The service is down for maintenance. Retry after 2 minutes.

---

## 💻 Example 2 — Traffic Spike

A sudden traffic spike 💥
Server reaches capacity.

Response:

```http
HTTP/1.1 503 Service Unavailable
```

---

## 🧠 Real-Life Analogy

You visit a shop 🏪
There’s a sign saying:

> “Temporarily closed — please come back later.”

That’s **503 Service Unavailable**.

---

## 🚀 Common Use Cases

| Scenario            | Why 503?             |
| ------------------- | -------------------- |
| Server overload     | Too many requests    |
| Maintenance window  | Planned downtime     |
| Autoscaling delay   | No healthy instances |
| Dependency outage   | Temporary failure    |
| Deployment restarts | Rolling updates      |

---

## ⚙️ Developer Notes (VERY IMPORTANT)

**✅ Use 503 when:**

- Failure is temporary

- Clients should retry later

- Server is overloaded or under maintenance

**❌ Do NOT use 503 when:**

- Upstream returns bad response → 502 Bad Gateway

- Upstream times out → 504 Gateway Timeout

- Server crashes → 500 Internal Server Error

---

## 🔥 Interview Tip (System Design Gold ⭐)

**💬 Question:**

> How should clients handle 503?

**Answer:**

- Implement retries with exponential backoff

- Respect Retry-After header

- Use circuit breakers

---

## 🧪 Express.js Example (Maintenance Mode)

```js
const maintenanceMode = true;

app.use((req, res, next) => {
  if (maintenanceMode) {
    return res.status(503).set("Retry-After", "120").json({
      message: "Service temporarily unavailable",
    });
  }
  next();
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

- MDN Docs — 503 Service Unavailable

- RFC 9110 — Server Error Responses
