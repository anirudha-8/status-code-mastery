<h1 align="center">💥 5xx – Server Error Responses</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Category-Server%20Error-orange?style=for-the-badge&logo=server" alt="5xx Server Error Badge" />
  <img src="https://img.shields.io/badge/HTTP%20Status%20Codes-5xx-critical?style=for-the-badge&logo=cloudflare" alt="HTTP 5xx Codes" />
</p>

---

## 🧠 What Are 5xx Server Error Codes?

The **5xx class** of HTTP status codes indicates that **the server failed to fulfill a valid request**.

Unlike **4xx errors (client mistakes)**,  
**5xx errors mean the problem is on the server side** — not the client.

> 💬 **In simple words:**  
> “Your request was correct — something went wrong on *our* side.”

These errors are critical because they often indicate:

- Bugs in backend code  
- Infrastructure failures  
- Dependency outages  
- Misconfigured servers  
- Overloaded systems  

---

## 🧩 Quick Overview of 5xx Codes

| Code | Name | Meaning |
|------|------|--------|
| [500 Internal Server Error](./500-internal-server-error.md) | 💥 Internal Error | Generic server failure |
| [501 Not Implemented](./501-not-implemented.md) | 🚧 Not Implemented | Feature not supported |
| [502 Bad Gateway](./502-bad-gateway.md) | 🔌 Bad Gateway | Invalid upstream response |
| [503 Service Unavailable](./503-service-unavailable.md) | 🛑 Service Down | Server overloaded or offline |
| [504 Gateway Timeout](./504-gateway-timeout.md) | ⏳ Gateway Timeout | Upstream server timed out |
| [505 HTTP Version Not Supported](./505-http-version-not-supported.md) | 🌐 HTTP Version Error | Unsupported HTTP version |

---

## 💻 Example — Typical 5xx Error

```http
GET /api/orders HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 500 Internal Server Error

{
  "error": "Something went wrong on our end"
}
```

**🎯 Meaning:**

The request is valid — but the server crashed or failed internally.

---

## 🧠 Real-Life Analogy

You order food at a restaurant 🍽️
Your order is clear and valid.

But the kitchen says:

> “Sorry, the stove broke.”

That’s a 5xx Server Error.

---

## 🚀 Why 5xx Errors Are Extremely Important

| Reason                 | Why it matters           |
| ---------------------- | ------------------------ |
| Production reliability | Indicates system health  |
| Monitoring & alerts    | Triggers alarms          |
| System design          | Tests resilience         |
| Interviews             | Common backend questions |
| User trust             | Frequent 5xx = bad UX    |

---

## ⚙️ Developer Best Practices

- ❌ Never expose stack traces to users

- ✅ Log detailed errors internally

- ✅ Return generic messages to clients

- ✅ Use correct 5xx codes (don’t overuse 500)

- ✅ Add retries, fallbacks, and circuit breakers

---

## 🔥 Interview Gold Section

**💬 Common Question:**

> What’s the difference between 4xx and 5xx?

**Answer:**

- 4xx → Client made a mistake

- 5xx → Server failed to process a valid request

---

## 🛠️ Monitoring & Observability Tip

In production:

- Track 5xx error rate

- Alert when it spikes

- Correlate with:

  - CPU / memory usage

  - Database latency

  - Third-party service downtime

---

## 🔗 References

- MDN Web Docs — Server Error Responses

- RFC 9110 — HTTP Semantics
