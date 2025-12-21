<h1 align="center">⏱️ 408 Request Timeout</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-408-red?style=for-the-badge&logo=http" alt="408 Badge" />
  <img src="https://img.shields.io/badge/Type-Client%20Timeout-critical?style=for-the-badge&logo=clock" alt="Timeout Error Badge" />
</p>

---

## 📖 Definition

The **408 Request Timeout** status code means that the server **did not receive a complete request**  
from the client within the allowed time.

The server closed the connection because the client took **too long** to send the request.

> 💬 **In simple words:**  
> “You took too long — please try again.”

---

## 🧩 When Does 408 Occur?

A `408` error occurs when:

- The client starts a request but does not finish it
- Network is slow or unstable
- Client is idle for too long
- Request body upload stalls
- Server timeout threshold is exceeded

⚠️ This error is about **request transmission**, not response processing.

---

## 💻 Example 1 — Slow Client Upload

**Client Request (incomplete):**

```http
POST /api/upload HTTP/1.1
Content-Length: 5000000
```

⏳ Client delays sending body…

**Server Response:**

```http
HTTP/1.1 408 Request Timeout
```

**🎯 Meaning:**
The server waited, but the client didn’t finish sending the request.

---

## 💻 Example 2 — Idle Connection

```http
GET /api/data HTTP/1.1
```

Client opens connection but sends nothing else.

**Response:**

```http
HTTP/1.1 408 Request Timeout
```

---

## 🧠 Real-Life Analogy

You call customer support 📞
They answer and say:

> “Hello?”

You stay silent for too long…
They hang up.

That’s **408 Request Timeout**.

---

## 🚀 Common Use Cases

| Scenario          | Why 408?                 |
| ----------------- | ------------------------ |
| Slow internet     | Request not completed    |
| Large uploads     | Client stalled           |
| Idle connections  | No data sent             |
| Poor network      | Request interrupted      |
| Security timeouts | Prevent resource hogging |

---

## ⚙️ Developer Notes (Important)

### ✅ Use 408 when

- Client fails to complete request in time

- Connection stays idle too long

### ❌ Do NOT use 408 when

- Server is slow → 504 Gateway Timeout

- Request is valid but long-running → 202 Accepted

- Rate limit exceeded → 429 Too Many Requests

---

## 🔥 Interview Tip

**💬 Difference between 408 and 504?**

- **408** → Client was too slow

- **504** → Server/upstream was too slow

---

## 🧪 Express.js Example (Timeout Handling)

```js
app.use((req, res, next) => {
  req.setTimeout(5000, () => {
    res.status(408).send("Request Timeout");
  });
  next();
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

- MDN Docs — 408 Request Timeout

- RFC 9110 — Client Error Semantics
