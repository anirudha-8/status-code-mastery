<h1 align="center">📌 308 Permanent Redirect</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-308-orange?style=for-the-badge&logo=http" alt="308 Badge" />
  <img src="https://img.shields.io/badge/Type-Permanent%20Redirect-yellow?style=for-the-badge&logo=pin" alt="Permanent Redirect Badge" />
</p>

---

## 📖 Definition

The **308 Permanent Redirect** status code indicates that the requested resource  
**has been permanently moved** to a new URL, and future requests should use that URL.

**Unlike 301**, the **HTTP method and body must NOT be changed** when redirecting.

> 💬 **In simple terms:**  
> “This resource has moved forever — and use the exact same request at the new URL.”

---

## 🧩 Why 308 Exists

Older redirect codes had serious issues:

- **301** → Might convert POST → GET  
- **302** → Usually converts POST → GET  
- **307** → Temporary but preserves method  

To fix this, HTTP introduced:

### ✔ **308 Permanent Redirect**

- Permanent (like **301**)  
- Preserves method + body (like **307**)  
- Clear, predictable behavior  

---

## 💻 Example — Permanent API Migration

**Client Request:**

```http
POST /api/v1/upload HTTP/1.1
Content-Type: application/json

{ "file": "avatar.png" }
```

**Server Response:**

```http
HTTP/1.1 308 Permanent Redirect
Location: /api/v2/upload
```

**➡️ The client must now send:**

```http
POST /api/v2/upload
(with the same body)
```

**🎯 Important:**
The method stays POST, unlike with 301.

---

## 💻 Example — Domain Migration

```http
GET http://example.com/blog
```

**Response:**

```http
HTTP/1.1 308 Permanent Redirect
Location: https://newdomain.com/blog
```

**Browser permanently updates:**

- Bookmarks

- SEO indexing

- Redirect cache

---

## 🧠 Real-Life Analogy

Imagine your office moves to a new building permanently.
HR sends a memo:

> “This is our new permanent address —
continue sending all your documents here exactly as before.”

That’s 308 Permanent Redirect.

---

## 🚀 When to Use 308

| Scenario                    | Why 308?                               |
| --------------------------- | -------------------------------------- |
| New API version             | Don't break POST, PUT, DELETE requests |
| HTTPS migration             | Safe, method-preserving redirect       |
| Permanent route redesign    | Predictable behavior                   |
| Moving from `/old` → `/new` | Without method rewriting               |
| Load balancer migrations    | Stable redirect semantics              |

## ⚙️ Developer Notes

### ✔ Preserves

- HTTP method

- Request body

- Headers

### ✔ Permanent — cached like 301

### ❌ Browsers treat 308 differently than 301

- No method switching

- No accidental GET conversions

### SEO Benefits (like 301)

- Link equity preserved

- Search engines update URLs

- Permanent mapping stored

### 301 vs 308 (Important)

| Code    | Permanent? | Preserves Method? | Use Case                        |
| ------- | ---------- | ----------------- | ------------------------------- |
| **301** | Yes        | ❌ No              | General website redirects       |
| **308** | Yes        | ✅ Yes             | APIs, form submissions, uploads |

---

## 🧪 Node.js Example

```js
app.post("/old", (req, res) => {
    res.redirect(308, "/new");
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

- MDN Docs — 308 Permanent Redirect

- RFC 7538 — Introduced the 308 Status Code
