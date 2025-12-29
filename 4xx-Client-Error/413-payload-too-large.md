<h1 align="center">📦 413 Payload Too Large</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-413-red?style=for-the-badge&logo=http" alt="413 Badge" />
  <img src="https://img.shields.io/badge/Type-Request%20Size%20Error-critical?style=for-the-badge&logo=package" alt="Payload Too Large Badge" />
</p>

---

## 📖 Definition

The **413 Payload Too Large** status code means that the server **refuses to process the request**  
because the **request body is larger than the server is willing or able to handle**.

> 💬 **In simple words:**  
> “Your request is valid — but it’s too big.”

---

## 🧩 When Does 413 Occur?

A `413` error occurs when:

- Client uploads a file larger than allowed
- Request body exceeds server limits
- API enforces strict payload size rules
- Reverse proxy (NGINX, CDN) blocks large bodies
- Security rules prevent large uploads

⚠️ The request is syntactically correct — size is the only issue.

---

## 💻 Example 1 — File Upload Too Large

**Client Request:**

```http
POST /api/upload HTTP/1.1
Content-Type: multipart/form-data
Content-Length: 15000000
```

Server Limit: 5MB

**Server Response:**

```http
HTTP/1.1 413 Payload Too Large

{
  "error": "Maximum upload size is 5MB"
}
```

---

## 💻 Example 2 — JSON Payload Too Large

```http
POST /api/logs HTTP/1.1
Content-Type: application/json
```

Body: Huge JSON array

Response:

```http
HTTP/1.1 413 Payload Too Large
```

---

## 🧠 Real-Life Analogy

You try to send a huge parcel 📦 via courier.
The courier replies:

> “We can’t accept packages over 10kg.”

That’s 413 Payload Too Large.

---

## 🚀 Common Use Cases

| Scenario           | Why 413?               |
| ------------------ | ---------------------- |
| File uploads       | Size exceeds limit     |
| API request limits | Protect server         |
| Reverse proxies    | Enforced max body size |
| Security controls  | Prevent abuse          |
| Cloud storage      | Upload quota exceeded  |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 413 when:**

- Request body exceeds allowed size

- Client can fix the issue by reducing payload

- Size limits are intentional

**❌ Do NOT use 413 when:**

- Content-Length is missing → 411 Length Required

- Media type is unsupported → 415 Unsupported Media Type

- Request format is invalid → 400 Bad Request

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 411 and 413?

**Answer:**

- 411 → Size info missing

- 413 → Size info present, but too large

---

## 🧪 Express.js Example (Body Size Limit)

```js
app.use(express.json({ limit: "1mb" }));

app.post("/api/data", (req, res) => {
  res.json({ message: "Accepted" });
});
```

If payload exceeds 1MB → Express automatically returns 413.

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

- MDN Docs — 413 Payload Too Large

- RFC 9110 — Client Error Responses
