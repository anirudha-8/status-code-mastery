<h1 align="center">⚖️ 451 Unavailable For Legal Reasons</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-451-red?style=for-the-badge&logo=http" alt="451 Badge" />
  <img src="https://img.shields.io/badge/Type-Legal%20Restriction-critical?style=for-the-badge&logo=scale" alt="Legal Restriction Badge" />
</p>

---

## 📖 Definition

The **451 Unavailable For Legal Reasons** status code means that the server  
**cannot provide access to the requested resource due to legal constraints**.

This could include:

- Court orders  
- Government censorship  
- Copyright restrictions  
- Regulatory compliance  

> 💬 **In simple words:**  
> “I’m not allowed by law to show you this.”

---

## 🧩 When Does 451 Occur?

A `451` error occurs when:

- Content is blocked by government regulations  
- Website is restricted in certain countries  
- Copyright takedown requests are enforced  
- Legal injunctions prevent content delivery  
- Compliance rules forbid access  

⚠️ The server **knows the resource exists**, but **law prevents access**.

---

## 💻 Example 1 — Government Restriction

**Client Request:**

```http
GET /news/article-123 HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 451 Unavailable For Legal Reasons

{
  "error": "This content is not available in your region due to legal restrictions"
}
```

---

## 💻 Example 2 — Copyright Takedown

```http
GET /movies/pirated-content HTTP/1.1
```

**Response:**

```http
HTTP/1.1 451 Unavailable For Legal Reasons

{
  "notice": "Removed in response to a legal request"
}
```

---

## 🧠 Real-Life Analogy

You go to a library 📚
The librarian says:

> “This book exists — but it’s banned by law.”

That’s 451 Unavailable For Legal Reasons.

## 🚀 Common Use Cases

| Scenario              | Why 451?         |
| --------------------- | ---------------- |
| Government censorship | Legal mandate    |
| Geo-blocked content   | Regional laws    |
| Copyright enforcement | DMCA takedown    |
| Court injunctions     | Legal compliance |
| ISP restrictions      | Regulatory order |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 451 when:**

- Access is denied explicitly due to legal reasons

- You want transparency instead of hiding content

- The resource exists but is legally restricted

**❌ Do NOT use 451 when:**

- User lacks permission → 403 Forbidden

- Resource is deleted → 410 Gone

- Resource doesn’t exist → 404 Not Found

---

## 🔥 Interview Tip (High Impact ⭐)

**💬 Question:**

Why use 451 instead of 403?

**Answer:**

- **403** → Access denied (policy/permission)

- **451** → Access denied due to law or regulation

451 improves **transparency and legal clarity**.

---

## 🧪 Express.js Example (Geo / Legal Block)

```js
app.get("/restricted-content", (req, res) => {
  const country = req.headers["x-country"];

  if (country === "BlockedCountry") {
    return res.status(451).json({
      error: "Unavailable for legal reasons",
    });
  }

  res.send("Content available");
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

- MDN Docs — 451 Unavailable For Legal Reasons

- RFC 7725 — Legal Restrictions Status Code
