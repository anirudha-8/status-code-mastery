<h1 align="center">⏳ 504 Gateway Timeout</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-504-orange?style=for-the-badge&logo=http" alt="504 Badge" />
  <img src="https://img.shields.io/badge/Type-Gateway%20Timeout-critical?style=for-the-badge&logo=clock" alt="Gateway Timeout Badge" />
</p>

---

## 📖 Definition

The **504 Gateway Timeout** status code means that a server acting as a **gateway or proxy**  
**did not receive a response in time** from an **upstream server**.

The request was valid — but **one server waited too long for another server to reply**.

> 💬 **In simple words:**  
> “I asked another server for help — it took too long to respond.”

---

## 🧩 When Does 504 Occur?

A `504` error occurs when:

- Backend service is too slow
- Database queries take too long
- Third-party API does not respond in time
- Network latency is high
- Timeout thresholds are exceeded
- Microservices are overloaded

⚠️ The upstream server **might still be working**, just **too slowly**.

---

## 💻 Example 1 — API Gateway Timeout

**Client → API Gateway → User Service**

```http
GET /api/users HTTP/1.1
```

User service takes too long to respond.

**Gateway Response:**

```http
HTTP/1.1 504 Gateway Timeout
```

🎯 Meaning:

The gateway gave up waiting.

---

## 💻 Example 2 — Slow Database Query

```http
GET /api/reports HTTP/1.1
```

Database query runs for 30 seconds, but timeout is 5 seconds.

**Response:**

```http
HTTP/1.1 504 Gateway Timeout
```

---

## 🧠 Real-Life Analogy

You order food through a delivery app 🍔
The app waits for the restaurant to confirm.

After waiting too long, the app says:

> “The restaurant is not responding.”

That’s **504 Gateway Timeout**.

---

## 🚀 Common Use Cases

| Scenario           | Why 504?             |
| ------------------ | -------------------- |
| Slow microservices | Timeout exceeded     |
| Third-party APIs   | No timely response   |
| Database latency   | Query timeout        |
| Network delays     | High latency         |
| Heavy computation  | Long processing time |

---

## ⚙️ Developer Notes (VERY IMPORTANT)

**✅ Use 504 when:**

- Server acts as gateway or proxy

- Upstream server did not respond in time

- Timeout thresholds are exceeded

**❌ Do NOT use 504 when:**

- Upstream returns invalid response → 502 Bad Gateway

- Upstream is down → 503 Service Unavailable

- Your own server crashes → 500 Internal Server Error

---

## 🔥 Interview Tip (System Design Gold ⭐)

**💬 Question:**

> Difference between 502 and 504?

**Answer:**

- **502** → Upstream responded, but response was invalid

- **504** → Upstream did not respond in time

---

## 🧪 NGINX Timeout Example

```nginx
proxy_connect_timeout 5s;
proxy_read_timeout 5s;
proxy_send_timeout 5s;
```

If backend exceeds these limits → **504 Gateway Timeout**

---

## ## 🔗 Related Codes

- [500 Internal Server Error](./500-internal-server-error.md)💥

- [501 Not Implemented](./501-not-implemented.md)🚧

- [502 Bad Gateway](./502-bad-gateway.md)🔌

- [503 Service Unavailable](./503-service-unavailable.md)🛑

- [504 Gateway Timeout](./504-gateway-timeout.md)⏳

- [505 HTTP Version Not Supported](./505-http-version-not-supported.md)🌐

---

## 📚 References

MDN Docs — 504 Gateway Timeout

RFC 9110 — Server Error Responses
