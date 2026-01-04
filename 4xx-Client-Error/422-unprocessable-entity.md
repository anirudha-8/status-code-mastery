<h1 align="center">🧠 422 Unprocessable Entity</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-422-red?style=for-the-badge&logo=http" alt="422 Badge" />
  <img src="https://img.shields.io/badge/Type-Validation%20Error-critical?style=for-the-badge&logo=check-circle" alt="Validation Error Badge" />
</p>

---

## 📖 Definition

The **422 Unprocessable Entity** status code means that the server **understands the request**  
and the **syntax is correct**, but it **cannot process the request due to semantic errors**.

In short, the request is *well-formed* — but **fails validation or business rules**.

> 💬 **In simple words:**  
> “I understand your data, but it doesn’t make sense.”

---

## 🧩 When Does 422 Occur?

A `422` error occurs when:

- Input data is syntactically valid JSON
- Required business rules are violated
- Field values are logically incorrect
- Validation fails after parsing
- Constraints beyond syntax are not met

This is **very common in REST APIs**.

---

## 💻 Example 1 — Validation Error

**Client Request:**

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "email": "not-an-email",
  "age": 12
}
```

**Server Validation Rules:**

- Email must be valid

- Age must be ≥ 18

**Server Response:**

```http
HTTP/1.1 422 Unprocessable Entity

{
  "errors": {
    "email": "Invalid email format",
    "age": "Must be at least 18"
  }
}
```

---

## 💻 Example 2 — Business Rule Violation

```http
POST /api/orders HTTP/1.1
Content-Type: application/json

{
  "quantity": 0
}
```

**Response:**

```http
HTTP/1.1 422 Unprocessable Entity

{
  "error": "Quantity must be greater than zero"
}
```

---

## 🧠 Real-Life Analogy

You fill out a form perfectly 📝

but you enter age = 3 for a driving license 🚗.

The form is readable, but logically wrong.

That’s **422 Unprocessable Entity**.

---

## 🚀 Common Use Cases

| Scenario             | Why 422?               |
| -------------------- | ---------------------- |
| Form validation      | Semantic errors        |
| Business rules       | Logical constraints    |
| API input validation | Parsed but invalid     |
| ORM validation       | Fails model rules      |
| GraphQL errors       | Field-level validation |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 422 when:**

- JSON is valid

- Syntax is correct

- Validation or business rules fail

**❌ Do NOT use 422 when:**

- JSON is malformed → 400 Bad Request

- Authentication fails → 401 Unauthorized

- Conflict exists → 409 Conflict

- Media type unsupported → 415 Unsupported Media Type

---

## 🔥 Interview Tip (Very Popular)

**💬 Question:**

> Difference between 400 and 422?

**Answer:**

- **400** → Invalid syntax or malformed request

- **422** → Valid syntax, invalid data semantics

---

## 🧪 Express.js Example (Validation)

```js
app.post("/api/users", (req, res) => {
  const { email, age } = req.body;

  if (!email.includes("@")) {
    return res.status(422).json({
      error: "Invalid email format",
    });
  }

  if (age < 18) {
    return res.status(422).json({
      error: "Age must be at least 18",
    });
  }

  res.status(201).json({ message: "User created" });
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
🧪

---

## 📚 References

- MDN Docs — 422 Unprocessable Entity

- RFC 4918 — WebDAV Extensions
