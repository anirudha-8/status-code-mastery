<h1 align="center">💥 500 Internal Server Error</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-500-orange?style=for-the-badge&logo=http" alt="500 Badge" />
  <img src="https://img.shields.io/badge/Type-Server%20Failure-critical?style=for-the-badge&logo=server" alt="Server Error Badge" />
</p>

---

## 📖 Definition

The **500 Internal Server Error** status code means that the server  
**encountered an unexpected condition** that prevented it from fulfilling the request.

The request sent by the client is **valid**, but something **broke inside the server**.

> 💬 **In simple words:**  
> “Something went wrong on our side.”

---

## 🧩 When Does 500 Occur?

A `500` error occurs when:

- Unhandled exceptions are thrown  
- Application crashes or bugs exist  
- Database queries fail unexpectedly  
- Null/undefined access errors happen  
- Misconfigured environment variables  
- Logic errors in backend code  

⚠️ `500` is a **generic fallback error** — it should not be overused.

---

## 💻 Example 1 — Unhandled Exception

**Client Request:**

```http
GET /api/users HTTP/1.1
```

**Server Code (Buggy):**

```http
app.get("/api/users", (req, res) => {
  const users = getUsers(); // throws error
  res.json(users);
});
```

**Server Response:**

```http
HTTP/1.1 500 Internal Server Error

{
  "error": "Internal server error"
}
```

**🎯 Meaning:**

An exception occurred that wasn’t handled properly.

---

## 💻 Example 2 — Database Failure

```http
POST /api/orders HTTP/1.1
```

Database connection fails ❌

**Response:**

```http
HTTP/1.1 500 Internal Server Error
```

---

## 🧠 Real-Life Analogy

You place an order at a restaurant 🍽️
Your order is clear and correct.

But the kitchen suddenly loses power 🔌.

That’s **500 Internal Server Error**.

---

## 🚀 Common Use Cases

| Scenario                | Why 500?               |
| ----------------------- | ---------------------- |
| Application bug         | Unexpected crash       |
| Database error          | Query failure          |
| Third-party API failure | Unhandled exception    |
| Misconfiguration        | Missing env variables  |
| Logic errors            | Edge cases not handled |

---

## ⚙️ Developer Notes (VERY IMPORTANT)

**✅ Use 500 when:**

- An unexpected error occurs

- Server cannot determine a more specific error

- Failure is internal and not client-related

**❌ Avoid using 500 when:**

- Input is invalid → 400 Bad Request

- Authentication fails → 401 Unauthorized

- Authorization fails → 403 Forbidden

- Resource not found → 404 Not Found

- Dependency is down → 502 / 503 / 504

---

## 🔥 Interview Tip (Top Question)

💬 Question:

> Is it okay to always return 500 for server errors?

Answer:
No.
Use specific 5xx codes when possible (502, 503, 504).
`500` should be a last resort fallback.

---

## 🛠️ Best Practices (Production-Grade)

- ❌ Never expose stack traces to clients

- ✅ Log full error details internally

- ✅ Return generic messages externally

- ✅ Use centralized error handling

- ✅ Add monitoring & alerts

---

## 🧪 Express.js Example (Global Error Handler)

```js
app.use((err, req, res, next) => {
  console.error(err.stack); // log internally

  res.status(500).json({
    error: "Internal Server Error",
  });
});
```

---

## 📚 References

- MDN Docs — 500 Internal Server Error

- RFC 9110 — Server Error Responses
