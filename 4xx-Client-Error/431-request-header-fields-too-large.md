<h1 align="center">📜 431 Request Header Fields Too Large</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-431-red?style=for-the-badge&logo=http" alt="431 Badge" />
  <img src="https://img.shields.io/badge/Type-Header%20Size%20Error-critical?style=for-the-badge&logo=file-text" alt="Header Size Error Badge" />
</p>

---

## 📖 Definition

The **431 Request Header Fields Too Large** status code means that the server  
**refuses to process the request** because **one or more HTTP request headers are too large**.

This can happen due to:

- A single oversized header, or
- The **combined size** of all headers exceeding server limits.

> 💬 **In simple words:**  
> “Your request headers are too big — please reduce them.”

---

## 🧩 When Does 431 Occur?

A `431` error occurs when:

- Cookies grow too large (very common cause 🍪)
- Authorization headers are oversized
- Too many custom headers are sent
- Reverse proxy (NGINX, CDN) enforces strict header limits
- Repeated redirects accumulate headers

⚠️ The request is valid — only the **headers are the problem**.

---

## 💻 Example 1 — Cookie Explosion 🍪

**Client Request:**

```http
GET /dashboard HTTP/1.1
Cookie: session_id=very_long_value_here; preferences=huge_json_blob; tracking=...
```

**Server Response:**

```http
HTTP/1.1 431 Request Header Fields Too Large

{
  "error": "Request headers too large"
}
```

**🎯 Meaning:**

Cookies exceeded server header size limits.

---

## 💻 Example 2 — Fixing the Issue

- Clear browser cookies

- Reduce cookie payload

- Avoid storing large data in cookies

- Use server-side sessions instead

➡️ Retry request successfully.

---

## 🧠 Real-Life Analogy

You submit a form 📄 with too many attachments stapled on top.
The office replies:

> “Please remove some papers — this is too bulky.”

That’s **431 Request Header Fields Too Large**.

---

## 🚀 Common Use Cases

| Scenario         | Why 431?              |
| ---------------- | --------------------- |
| Cookie bloat     | Cookies exceed limits |
| Auth headers     | Tokens too large      |
| Custom headers   | Excessive metadata    |
| CDN/proxy limits | Header size exceeded  |
| Redirect loops   | Header accumulation   |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 431 when:**

- Header size exceeds server limits

- Client can fix by trimming headers

**❌ Do NOT use 431 when:**

- Payload body is too large → 413 Payload Too Large

- URL is too long → 414 URI Too Long

- Media type unsupported → 415 Unsupported Media Type

---

## 🔥 Interview Tip

💬 Question:

> What’s the most common real-world cause of 431?

Answer:

**Oversized cookies** — especially in large web apps.

---

## 🧪 Express.js Example (Header Size Check)

```js
app.use((req, res, next) => {
  const headersSize = JSON.stringify(req.headers).length;

  if (headersSize > 8192) {
    return res.status(431).send("Request Header Fields Too Large");
  }

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

- MDN Docs — 431 Request Header Fields Too Large

- RFC 6585 — Additional HTTP Status Codes
