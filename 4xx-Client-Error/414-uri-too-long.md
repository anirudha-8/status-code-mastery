<h1 align="center">🔗 414 URI Too Long</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-414-red?style=for-the-badge&logo=http" alt="414 Badge" />
  <img src="https://img.shields.io/badge/Type-Request%20URI%20Error-critical?style=for-the-badge&logo=link" alt="URI Too Long Badge" />
</p>

---

## 📖 Definition

The **414 URI Too Long** status code means that the server **refuses to process the request**  
because the **URI (URL)** provided by the client is **longer than the server is willing to handle**.

> 💬 **In simple words:**  
> “Your URL is too long for me to process.”

---

## 🧩 When Does 414 Occur?

A `414` error occurs when:

- Query parameters are excessively long  
- Large amounts of data are sent via the URL instead of the body  
- GET requests are misused for large payloads  
- Browser or proxy URL length limits are exceeded  
- Security rules block overly long URLs  

⚠️ This often indicates **incorrect API usage**.

---

## 💻 Example 1 — Excessively Long Query String

**Client Request:**

```http
GET /api/search?q=very_long_query_string_with_lots_of_data_here HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 414 URI Too Long
```

**🎯 Meaning:**

The query string exceeded server limits.

---

## 💻 Example 2 — Fixing the Issue

**❌ Bad:**

```http
GET /api/users?data=huge_json_payload_here
```

**✅ Good:**

```http
POST /api/users/search
Content-Type: application/json

{
  "filters": { "role": "admin" }
}
```

---

## 🧠 Real-Life Analogy

You try to write an entire paragraph on a short address label 🏷️.
The label simply can’t fit that much text.

That’s **414 URI Too Long**.

---

## 🚀 Common Use Cases

| Scenario              | Why 414?                  |
| --------------------- | ------------------------- |
| Long query parameters | URL length exceeded       |
| Misusing GET requests | Payload should be in body |
| Tracking parameters   | Too many URL params       |
| Browser limitations   | Max URL size hit          |
| Security protection   | Prevent URL abuse         |

---

## ⚙️ Developer Notes (Important)

**✅ Use 414 when:**

- URL length exceeds server limits

- Request line is too long

**❌ Do NOT use 414 when:**

- Payload body is too large → 413 Payload Too Large

- Request syntax is invalid → 400 Bad Request

- Media type is unsupported → 415 Unsupported Media Type

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 413 and 414?

**Answer:**

- **413** → Request body is too large

- **414** → URL (URI) is too long

---

## 🧪 Express.js Example (URL Length Check)

```js
app.use((req, res, next) => {
    if (req.originalUrl.length > 2048) {
        return res.status(414).send("URI Too Long");
  }
  next();
});
```

---

## 📚 References

- MDN Docs — 414 URI Too Long

- RFC 9110 — Client Error Responses
