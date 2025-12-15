<h1 align="center">❌ 400 Bad Request</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-400-red?style=for-the-badge&logo=http" alt="400 Badge" />
  <img src="https://img.shields.io/badge/Type-Client%20Error-critical?style=for-the-badge&logo=alert-circle" alt="Client Error Badge" />
</p>

---

## 📖 Definition

The **400 Bad Request** status code means that the server **cannot process the request**  
because it is **invalid, malformed, or incorrect**.

The request reached the server successfully —  
but the server **rejected it due to client-side mistakes**.

> 💬 **In simple words:**  
> “Your request doesn’t make sense — please fix it.”

---

## 🧩 Common Reasons for 400 Errors

A `400 Bad Request` is usually caused by one or more of the following:

- ❌ Invalid JSON body  
- ❌ Missing required fields  
- ❌ Wrong data types (string instead of number)  
- ❌ Malformed URL or query parameters  
- ❌ Invalid request headers  
- ❌ Failed input validation  

---

## 💻 Example 1 — Invalid JSON Payload

**Client Request:**

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "email": "anirudha@example.com",
  "age": "twenty"
}
```

**Server Response:**

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
  "error": "Invalid data type for age"
}
```

**🎯 Problem:**

`age` should be a number, not a string.

---

## 💻 Example 2 — Missing Required Field

```http
POST /api/register HTTP/1.1
Content-Type: application/json

{
  "password": "secret123"
}
```

**Response:**

```http
HTTP/1.1 400 Bad Request

{
  "error": "Email is required"
}
```

---

## 🧠 Real-Life Analogy

You go to a railway ticket counter 🚆 and say:

> “Give me a ticket.”

The clerk asks:

> “Where to? Which date? Which class?”

You gave **incomplete or unclear information** -
that’s **400 Bad Request**.

---

## 🚀 Common Use Cases

| Scenario                | Why 400 is used          |
| ----------------------- | ------------------------ |
| Invalid form submission | Input validation failed  |
| Bad JSON body           | Parsing error            |
| Missing parameters      | Required fields not sent |
| Invalid query string    | Unsupported or malformed |
| Incorrect headers       | Missing Content-Type     |

---

## ⚙️ Developer Notes (Very Important)

### ✅ When to Use 400

- Client sends invalid input

- Request syntax is wrong

- Validation fails

### ❌ When NOT to Use 400

- Authentication issues → **401 Unauthorized**

- Authorization issues → **403 Forbidden**

- Resource not found → **404 Not Found**

- Semantic validation errors → **422 Unprocessable Entity**(preferred in some APIs)

---

## 🧪 Example — Express.js Validation

```js
app.post("/api/users", (req, res) => {
  const { email } = req.body;

  if (!email) {
    return res.status(400).json({
      error: "Email is required",
    });
  }

  res.status(201).json({ message: "User created" });
});
```

---

## 🔥 Interview Tip

💬 Question:

When do you use 400 vs 422?

**Answer:**

- **400** → Syntax or format is invalid

- **422** → Syntax is valid, but data fails business rules

---

## 📚 References

- MDN Docs — 400 Bad Request

- RFC 9110 — Client Error Responses
