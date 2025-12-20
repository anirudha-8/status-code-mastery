<h1 align="center">🎭 406 Not Acceptable</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-406-red?style=for-the-badge&logo=http" alt="406 Badge" />
  <img src="https://img.shields.io/badge/Type-Content%20Negotiation-critical?style=for-the-badge&logo=sliders" alt="Content Negotiation Error Badge" />
</p>

---

## 📖 Definition

The **406 Not Acceptable** status code means that the server **cannot generate a response**  
that matches the criteria specified in the client’s request headers.

This usually happens due to **content negotiation** issues involving headers like:

- `Accept`
- `Accept-Language`
- `Accept-Encoding`
- `Accept-Charset`

> 💬 **In simple words:**  
> “I have the data, but not in the format you asked for.”

---

## 🧩 When Does 406 Occur?

A `406` error occurs when:

- Client requests a response format the server does not support
- Requested language is unavailable
- Requested encoding (gzip, br) is not supported
- Requested media type cannot be produced

⚠️ The resource **exists**, but the **representation doesn’t match** client expectations.

---

## 💻 Example 1 — Unsupported Media Type Requested

**Client Request:**

```http
GET /api/users HTTP/1.1
Accept: application/xml
```

**Server supports only:**

```bash
application/json
```

```http
**Server Response:**
```

HTTP/1.1 406 Not Acceptable

**🎯 Meaning:**
The server can’t return XML — only JSON is available.

---

## 💻 Example 2 — Language Not Supported

```http
GET /homepage HTTP/1.1
Accept-Language: fr-FR
```

**Server supports:**

```bash
en-US, hi-IN
```

**Response:**

```http
HTTP/1.1 406 Not Acceptable
```

---

🧠 Real-Life Analogy

You go to a restaurant 🍽️ and say:

> “I want only Italian food 🇮🇹.”

The restaurant replies:

> “Sorry, we only serve Indian and Chinese.”

That’s **406 Not Acceptable**.

---

## 🚀 Common Use Cases

| Scenario                    | Why 406?                  |
| --------------------------- | ------------------------- |
| Wrong `Accept` header       | Format not supported      |
| Unsupported language        | No matching localization  |
| Invalid encoding            | Compression not available |
| Strict APIs                 | Enforced response formats |
| Content negotiation failure | No overlap                |

---

## ⚙️ Developer Notes (Important)

### ✅ Use 406 when

- Resource exists

- Client constraints cannot be satisfied

- Content negotiation fails

### ❌ Do NOT use 406 when

- Resource does not exist → 404 Not Found

- Media type of request body is unsupported → 415 Unsupported Media Type

- Request syntax is invalid → 400 Bad Request

### 406 vs 415 (Interview Gold ⭐)

| Code    | Meaning                                      |
| ------- | -------------------------------------------- |
| **406** | Server cannot produce acceptable response    |
| **415** | Server cannot understand request body format |

---

## 🧪 Express.js Example (Strict Content Negotiation)

```js
app.get("/api/data", (req, res) => {
  if (!req.accepts("json")) {
    return res.status(406).send("Only JSON is supported");
  }

  res.json({ data: "Hello World" });
});
```

---

## 📚 References

- MDN Docs — 406 Not Acceptable

- RFC 9110 — Content Negotiation
