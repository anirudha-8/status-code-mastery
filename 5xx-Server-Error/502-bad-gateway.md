<h1 align="center">🔌 502 Bad Gateway</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-502-orange?style=for-the-badge&logo=http" alt="502 Badge" />
  <img src="https://img.shields.io/badge/Type-Gateway%20Error-critical?style=for-the-badge&logo=shuffle" alt="Bad Gateway Badge" />
</p>

---

## 📖 Definition

The **502 Bad Gateway** status code means that a server acting as a **gateway or proxy**  
received an **invalid response** from an **upstream server**.

The request was valid — but **one server failed while talking to another server**.

> 💬 **In simple words:**  
> “I asked another server for data, and it replied incorrectly.”

---

## 🧩 When Does 502 Occur?

A `502` error occurs when:

- Backend service crashes or returns invalid data  
- Reverse proxy (NGINX, CDN) can’t understand upstream response  
- Microservice returns malformed HTTP response  
- DNS resolution issues occur  
- Upstream server closes connection unexpectedly  

⚠️ This error is common in **distributed systems** and **microservices**.

---

## 💻 Example 1 — Reverse Proxy Failure

**Client → NGINX → Backend API**

```http
GET /api/orders HTTP/1.1
```

Backend crashes or returns garbage

**NGINX Response:**

```http
HTTP/1.1 502 Bad Gateway
```

**🎯 Meaning:**

NGINX is healthy — the backend service failed.

---

## 💻 Example 2 — Invalid Upstream Response

**Backend returns:**

```http
<random non-http text>
```

Gateway cannot parse it → 502 Bad Gateway

---

## 🧠 Real-Life Analogy

You ask a delivery agent 🚚 to bring food from a restaurant 🍽️
The restaurant hands over spoiled food.

The agent says:

> “Sorry, the restaurant gave me something unusable.”

That’s 502 Bad Gateway.

---

## 🚀 Common Use Cases

| Scenario       | Why 502?                   |
| -------------- | -------------------------- |
| Reverse proxy  | Invalid backend response   |
| Microservices  | Downstream service failure |
| API gateways   | Bad upstream response      |
| CDN errors     | Origin server issue        |
| Load balancers | Backend unhealthy          |

---

## ⚙️ Developer Notes (VERY IMPORTANT)

**✅ Use 502 when:**

- Server acts as gateway or proxy

- Upstream server responds incorrectly

- Dependency failure causes invalid response

**❌ Do NOT use 502 when:**

- Upstream server is down → 503 Service Unavailable

- Upstream server times out → 504 Gateway Timeout

- Your own server crashes → 500 Internal Server Error

---

## 🔥 Interview Tip (System Design Favorite ⭐)

**💬 Question:**

> Difference between 502, 503, and 504?

**Answer:**

- **502** → Bad response from upstream

- **503** → Upstream is unavailable

- **504** → Upstream took too long

---

## 🧪 Express + NGINX Example

**NGINX config (simplified):**

```nginx
location /api/ {
  proxy_pass http://backend-service;
}
```

If `backend-service` returns invalid HTTP → 502

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

- MDN Docs — 502 Bad Gateway

- RFC 9110 — Server Error Responses
