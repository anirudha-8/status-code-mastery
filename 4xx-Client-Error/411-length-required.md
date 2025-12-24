<h1 align="center">📏 411 Length Required</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-411-red?style=for-the-badge&logo=http" alt="411 Badge" />
  <img src="https://img.shields.io/badge/Type-Request%20Metadata%20Error-critical?style=for-the-badge&logo=ruler" alt="Length Required Badge" />
</p>

---

## 📖 Definition

The **411 Length Required** status code means that the server **refuses to accept the request**  
because it **requires a `Content-Length` header**, and the client did not provide one.

> 💬 **In simple words:**  
> “Tell me how big your request body is.”

---

## 🧩 When Does 411 Occur?

A `411` error occurs when:

- The request includes a body (e.g., POST/PUT)
- The server requires `Content-Length`
- The client omits the `Content-Length` header
- Chunked transfer encoding is not allowed

This is common in **strict servers**, **older systems**, or **security-hardened APIs**.

---

## 💻 Example 1 — Missing Content-Length

**Client Request:**

```http
POST /api/upload HTTP/1.1
Content-Type: application/json

{
  "file": "data"
}
```

**Server Response:**

```http
HTTP/1.1 411 Length Required
```

**🎯 Meaning:**

The server expects a Content-Length header.

---

## 💻 Example 2 — Corrected Request

```http
POST /api/upload HTTP/1.1
Content-Type: application/json
Content-Length: 18

{
  "file": "data"
}
```

➡️ Server now processes the request successfully.

---

## 🧠 Real-Life Analogy

You send a package 📦 without mentioning its weight.
The courier replies:

> “Please tell us the weight before shipping.”

That’s 411 Length Required.

---

## 🚀 Common Use Cases

| Scenario            | Why 411?                     |
| ------------------- | ---------------------------- |
| Strict HTTP servers | Require known body size      |
| File uploads        | Prevent unknown payload size |
| Security controls   | Avoid streaming attacks      |
| Legacy systems      | No chunked encoding support  |
| Proxies/gateways    | Enforce content rules        |

---

## ⚙️ Developer Notes (Important)

**✅ Use 411 when:**

- Server requires Content-Length

- Client omits it

- Chunked requests are not supported

**❌ Do NOT use 411 when:**

- Body size is too large → 413 Payload Too Large

- Media type is unsupported → 415 Unsupported Media Type

- Request syntax is invalid → 400 Bad Request

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 411 and 413?

**Answer:**

- 411 → Missing size information

- 413 → Size provided but too large

---

## 🧪 Express.js Example (Strict Length Check)

```js
app.use((req, res, next) => {
    if (["POST", "PUT", "PATCH"].includes(req.method) && !req.headers["content-length"]) {
        return res.status(411).send("Content-Length required");
  }
  next();
});
```

---

## 📚 References

- MDN Docs — 411 Length Required

- RFC 9110 — Client Error Semantics
