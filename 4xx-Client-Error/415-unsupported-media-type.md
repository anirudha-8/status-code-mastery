<h1 align="center">🧪 415 Unsupported Media Type</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-415-red?style=for-the-badge&logo=http" alt="415 Badge" />
  <img src="https://img.shields.io/badge/Type-Media%20Type%20Error-critical?style=for-the-badge&logo=beaker" alt="Unsupported Media Type Badge" />
</p>

---

## 📖 Definition

The **415 Unsupported Media Type** status code means that the server **refuses to process the request**  
because the **media type of the request body is not supported** by the server.

This usually happens when the `Content-Type` header is:

- Missing
- Incorrect
- Unsupported by the API

> 💬 **In simple words:**  
> “I don’t understand this data format.”

---

## 🧩 When Does 415 Occur?

A `415` error occurs when:

- Client sends data in an unsupported format  
- `Content-Type` header does not match expected type  
- Server only accepts specific media types  
- JSON is expected but XML or plain text is sent  
- File uploads use incorrect MIME types  

⚠️ The request body exists — but the server can’t parse it.

---

## 💻 Example 1 — Wrong Content-Type

**Client Request:**

```http
POST /api/users HTTP/1.1
Content-Type: text/plain

name=Anirudha
```

**Server expects:** `application/json`

Server Response:

```http
HTTP/1.1 415 Unsupported Media Type

{
  "error": "Only application/json is supported"
}
```

---

## 💻 Example 2 — Corrected Request

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "name": "Anirudha"
}
```

➡️ Server now processes the request successfully.

---

## 🧠 Real-Life Analogy

You submit a document 📄 written in a language the reader doesn’t understand.
They respond:

> “Please send this in English.”

That’s **415 Unsupported Media Type**.

---

## 🚀 Common Use Cases

| Scenario                | Why 415?             |
| ----------------------- | -------------------- |
| Wrong `Content-Type`    | Format not supported |
| Sending XML to JSON API | Parser mismatch      |
| Invalid file MIME type  | Upload rejected      |
| Missing Content-Type    | Server can’t parse   |
| Strict APIs             | Enforce formats      |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 415 when:**

- Request body format is unsupported

- Content-Type is invalid or missing

- Client must change data format

**❌ Do NOT use 415 when:**

- Response format not acceptable → 406 Not Acceptable

- Payload is too large → 413 Payload Too Large

- Request body is invalid JSON → 400 Bad Request

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 406 and 415?

**Answer:**

- **406** → Server can’t produce acceptable response

- **415** → Server can’t process request body format

---

## 🧪 Express.js Example (Content-Type Validation)

```js
app.post("/api/users", (req, res, next) => {
  if (!req.is("application/json")) {
    return res.status(415).json({
      error: "Unsupported Media Type",
    });
  }
  next();
});
```

---

## 📚 References

- MDN Docs — 415 Unsupported Media Type

- RFC 9110 — Client Error Responses
