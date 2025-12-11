<h1 align="center">🔄 307 Temporary Redirect</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-307-orange?style=for-the-badge&logo=http" alt="307 Badge" />
  <img src="https://img.shields.io/badge/Type-Temporary%20Redirect-yellow?style=for-the-badge&logo=redo" alt="Temporary Redirect Badge" />
</p>

---

## 📖 Definition

The **307 Temporary Redirect** status code indicates that the requested resource  
is **temporarily located** at a different URL, and the client must **repeat the request exactly as it was**,  
including **HTTP method** and **body**.

Unlike 302, 307 **does NOT allow changing the method**.

> 💬 **In simple words:**  
> “Use this temporary URL — but send the request exactly the same way.”

---

## 🧩 Why 307 Exists

Historically, **302 Found** caused confusion because browsers often changed:

- POST → GET  
- PUT → GET  

To fix this ambiguity, **307** was created with strict rules:

### ✔ Method must remain the same  

### ✔ Body must remain unchanged  

### ✔ Redirection is temporary  

This makes 307 ideal for **APIs** and **sensitive operations**.

---

## 💻 Example — API Redirect With POST

**Client Request:**

```http
POST /api/upload HTTP/1.1
Content-Type: application/json

{
  "file": "resume.pdf"
}
```

**Server Response:**

```http
HTTP/1.1 307 Temporary Redirect
Location: /api/upload-temp
```

**➡️ The client must send:**

```http
POST /api/upload-temp
(same body)
```

**🎯 Meaning:**

“This is temporary — send the exact same request to this new URL.”

---

## 💻 Example — Temporary Maintenance Redirect

```http
GET /login HTTP/1.1
```

**Response:**

```http
HTTP/1.1 307 Temporary Redirect
Location: /maintenance/login
```

Browser will fetch /maintenance/login but still using GET.

---

## 🧠 Real-Life Analogy

Imagine going to a shop and seeing a sign:

> “We’re temporarily working in the shop next door.
Please bring the same documents and request.”

That's **307 Temporary Redirect** — temporary change, same action.

---

## 🚀 When to Use 307 (Best Use Cases)

| Scenario                   | Why 307?                         |
| -------------------------- | -------------------------------- |
| API redirects              | Must preserve POST, PUT, DELETE  |
| Authentication flows       | Sensitive method must not change |
| Upload endpoints           | Body must remain intact          |
| Temporary server migration | Clients should retry exactly     |
| Load balancers             | Route traffic temporarily        |

---

⚙️ Developer Notes

- 307 is preferred over 302 when method integrity is required.

- Browsers and HTTP clients must not alter:

  - Method

  - Body

  - Headers

- For permanent redirects that preserve method, use 308 Permanent Redirect.

---

## ❗Important Difference

| Code    | Preserves Method? | Permanent? |
| ------- | ----------------- | ---------- |
| **302** | ❌ No              | No         |
| **303** | ❌ No (forces GET) | No         |
| **307** | ✅ Yes             | No         |
| **308** | ✅ Yes             | Yes        |

---

## 🧪 Node.js Example

```js
app.post("/upload", (req, res) => {
    res.redirect(307, "/upload-temp");
});
```

---

## 🔗 Related Codes

- [300 Multiple Choices](./300-multiple-choices.md)📚

- [301 Moved Permanently](./301-moved-permanently.md)🔒

- [302 Found](./302-found.md)🔁

- [303 See Other](./303-see-other.md)🔗

- [304 Not Modified](./304-not-modified.md)🗂️

- [305 Use Proxy](./305-use-proxy.md) | 🖧

- [306 Switch Proxy](./306-switch-proxy.md)🚫

- [307 Temporary Redirect](./307-temporary-redirect.md)🔄

- [308 Permanent Redirect](./308-permanent-redirect.md)📌

---

## 📚 References

- MDNDocs — 307 Temporary Redirect

- RFC 9110 — Redirection Semantics
