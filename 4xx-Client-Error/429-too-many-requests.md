<h1 align="center">🚦 429 Too Many Requests</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-429-red?style=for-the-badge&logo=http" alt="429 Badge" />
  <img src="https://img.shields.io/badge/Type-Rate%20Limit-critical?style=for-the-badge&logo=traffic-light" alt="Rate Limit Badge" />
</p>

---

## 📖 Definition

The **429 Too Many Requests** status code means that the client has **sent too many requests  
in a given amount of time**, exceeding the server’s **rate limits**.

The request itself is valid — but the **frequency is too high**.

> 💬 **In simple words:**  
> “Slow down — you’re sending requests too fast.”

---

## 🧩 When Does 429 Occur?

A `429` error occurs when:

- Client exceeds API rate limits  
- Too many requests from the same IP  
- Bot or abuse protection triggers  
- Login attempts are too frequent  
- Free-tier API limits are exceeded  

Rate limiting helps protect:

- Server resources  
- Databases  
- Security systems  
- Fair usage policies  

---

## 💻 Example 1 — Rate Limit Exceeded

**Client Request:**

```http
GET /api/data HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 429 Too Many Requests
Retry-After: 60
```

**🎯 Meaning:**

Client must wait 60 seconds before retrying.

---

## 💻 Example 2 — API Usage Limit

```http
GET /api/weather HTTP/1.1
Authorization: Bearer free_plan_token
```

**Response:**

```http
HTTP/1.1 429 Too Many Requests

{
  "error": "API rate limit exceeded. Upgrade your plan."
}
```

---

## 🧠 Real-Life Analogy

You press an elevator button 🚪 repeatedly.

The system responds:

> “Please wait — the elevator is coming.”

That’s **429 Too Many Requests**.

---

## 🚀 Common Use Cases

| Scenario        | Why 429?             |
| --------------- | -------------------- |
| Public APIs     | Enforce fair usage   |
| Login endpoints | Prevent brute-force  |
| Payment APIs    | Protect transactions |
| Web scraping    | Block abuse          |
| Cloud services  | Tier-based limits    |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 429 when:**

- Request rate exceeds limits

- Client should retry later

- Throttling is intentional

**❌ Do NOT use 429 when:**

- Server is overloaded → 503 Service Unavailable

- Client is unauthorized → 401 Unauthorized

- Payload is invalid → 400 Bad Request

---

## 🔥 Interview Tip (Very Popular)

**💬 Question:**

> What header is commonly used with 429?

**Answer:**

- Retry-After → tells client when to retry

---

## 🧪 Express.js Example (Rate Limiting)

```js
import rateLimit from "express-rate-limit";

const limiter = rateLimit({
  windowMs: 1 * 60 * 1000, // 1 minute
  max: 100, // limit each IP to 100 requests per window
});

app.use("/api", limiter);
```

When limit is exceeded → Express automatically returns 429.

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

- MDN Docs — 429 Too Many Requests

- RFC 6585 — Additional HTTP Status Codes
