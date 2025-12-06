<h1 align="center">🔁 302 Found</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-302-orange?style=for-the-badge&logo=http" alt="302 Badge" />
  <img src="https://img.shields.io/badge/Type-Temporary%20Redirect-yellow?style=for-the-badge&logo=refresh-cw" alt="Temporary Redirect Badge" />
</p>

---

## 📖 Definition

The **302 Found** status code means that the resource requested is **temporarily located**  
at a different URL. The client should continue using the **original URL** for future requests.

This redirection is **temporary**, unlike **301 Moved Permanently**.

> 💬 **In simple terms:**  
> “Go to this other URL for now — but don’t update your bookmarks.”

---

## 🧩 When Is 302 Used?

Use **302 Found** when:

- A page is temporarily unavailable  
- A route has a short-term replacement  
- Maintenance or A/B testing is happening  
- A login page redirects users after authentication  
- A website performs temporary restructuring  

Browsers and crawlers treat it as a **non-permanent** change.

---

## 💻 Example — Basic 302 Redirect

**Client Request:**

```http
GET /pricing HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 302 Found
Location: /pricing-temp
```

**🎯 Meaning:** Use /pricing-temp for now, but /pricing remains the real URL.

---

## 💻 Example — Login Redirect After Authentication

```http
POST /login HTTP/1.1
```

**Response:**

```http
HTTP/1.1 302 Found
Location: /dashboard
```

🎉 After successful login, the user is redirected to their dashboard.

---

## 🧠 Real-Life Analogy

Imagine visiting your favorite café, but they tell you:

> “The main seating area is closed right now.
> Please sit in our temporary area.”

That’s 302 Found — temporary but functional.

---

## ⚙️ Important Notes About 302

## 🔥 Browsers often change the HTTP method

A POST request may be converted into a GET when redirected with 302.

This caused confusion historically, which led to the creation of:

| Code                       | Fix                           |
| -------------------------- | ----------------------------- |
| **303 See Other**          | Forces GET method             |
| **307 Temporary Redirect** | Preserves the original method |

---

## 🚀 Common Use Cases

| Scenario             | Why 302?                            |
| -------------------- | ----------------------------------- |
| Maintenance mode     | Temporarily redirect users          |
| Temporary promo page | Redirect /sale → /sale-2025         |
| After login          | Move users to dashboard             |
| A/B testing          | Route traffic to different variants |
| Beta pages           | Limited-time redirects              |

---

## ⚙️ Developer Tips

- Use 302 only for temporary redirects

- For permanent redirects, always use 301

- To preserve POST → POST, use 307 Temporary Redirect

- For API redirects, 302 is less predictable because of method changes

---

## 🧪 Node.js Example

```js
app.get("/old-temp", (req, res) => {
  res.redirect(302, "/temporary-location");
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

- MDN Docs — 302 Found

- RFC 9110 — Redirection Semantics
