<h1 align="center">🔒 301 Moved Permanently</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-301-orange?style=for-the-badge&logo=http" alt="301 Badge" />
  <img src="https://img.shields.io/badge/Type-Permanent%20Redirect-yellow?style=for-the-badge&logo=lock" alt="Permanent Redirect Badge" />
</p>

---

## 📖 Definition

The **301 Moved Permanently** status code means that the resource requested by the client  
**has been permanently moved** to a new URL, and all future requests should go to that new URL.

The response **must include** a `Location` header telling the client where to go.

> 💬 **In simple terms:**  
> “This page has a new home forever. Use this new link from now on.”

---

## 🧩 When to Use 301

- Permanent change of website domain  
- Moving a page to a new path permanently  
- Migrating from **HTTP → HTTPS**  
- SEO-friendly URL restructuring  
- Replacing old endpoints in APIs  
- Redirecting outdated documentation links  

301 is a **long-term** redirect.  
Browsers, search engines, and crawlers store this information permanently.

---

## 💻 Example — Permanent Redirect

**Client Request:**

```http
GET /old-blog/python-tutorial HTTP/1.1
Host: example.com
```

**Server Response:**

```http
HTTP/1.1 301 Moved Permanently
Location: https://example.com/blog/python-tutorial
```

**🎯 Meaning:** The resource lives at the new URL forever.

---

## 💻 Example — Force HTTPS

```http
GET http://example.com/account
```

**Response:**

```http
HTTP/1.1 301 Moved Permanently
Location: https://example.com/account
```

🔐 Now browsers update the bookmark AND always use HTTPS.

---

## 🧠 Real-Life Analogy

Imagine moving to a new home permanently.
You place a note outside your old house:

> “I’ve moved! My new address is XYZ.”

That’s exactly what 301 Moved Permanently does for URLs.

---

## 🚀 SEO Impact (Very Important)

| Aspect            | Behavior                        |
| ----------------- | ------------------------------- |
| Link equity       | ✅ Passed (90–99% ranking power) |
| Search indexing   | New URL replaces the old one    |
| Duplicate content | Eliminated                      |
| Browser caching   | Long-term or permanent          |

301 is the **best redirect** for SEO migrations.

---

## ⚙️ Developer Notes

- Browsers cache 301 redirects aggressively

- Use 302/307 only if redirect is temporary

- Always include the Location: header

- For APIs, ensure clients know the route changed

- Avoid redirect loops!

---

## 301 vs 308

| Code    | Meaning            | Preserves Method?         |
| ------- | ------------------ | ------------------------- |
| **301** | Permanent redirect | ❌ May change POST → GET   |
| **308** | Permanent redirect | ✅ Method + body preserved |

---

## 🧪 Node.js Example

```js
app.get("/old-route", (req, res) => {
    res.redirect(301, "/new-route");
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

- MDN Docs — 301 Moved Permanently

- RFC 9110 — Redirection Semantics
