<h1 align="center">🗂️ 304 Not Modified</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-304-yellow?style=for-the-badge&logo=http" alt="304 Badge" />
  <img src="https://img.shields.io/badge/Type-Caching%20Redirect-gold?style=for-the-badge&logo=folder" alt="Caching Badge" />
</p>

---

## 📖 Definition

The **304 Not Modified** status code tells the client that the resource  
**has not changed** since it was last requested and that the client  
should use the **cached version** instead of downloading it again.

> 💬 **In simple terms:**  
> “Nothing changed — use your cached copy!”

---

## 🧩 Why 304 Exists

To save:

- **Bandwidth**  
- **Server load**  
- **Network time**  
- **Browser re-downloading large resources**  

Modern websites rely heavily on **caching** — images, CSS, JS bundles, fonts —  
and **304 Not Modified** is the backbone of that system.

---

## 💻 Example — Cache Validation with `If-Modified-Since`

**Client Request:**

```http
GET /styles/main.css HTTP/1.1
If-Modified-Since: Tue, 20 Jan 2025 10:30:00 GMT
```

**Server Response:**

```http
HTTP/1.1 304 Not Modified
```

**🎯 Meaning:**

"Your version is still fresh — use it."

---

## 💻 Example — ETag-Based Cache Check

**Client Request:**

```http
GET /app.js HTTP/1.1
If-None-Match: "file-hash-xyz123"
```

**Server Response:**

```http
HTTP/1.1 304 Not Modified
```

🎉 No need to resend the entire JavaScript file.

---

## 🧠 Real-Life Analogy

Imagine asking your friend:

> “Did anything change since the last time I checked?”

Your friend replies:

> “Nope, everything is the same.”

So you don’t need the information again — that’s 304 Not Modified.

---

## 🚀 Performance Benefits

| Benefit                   | Why It Matters              |
| ------------------------- | --------------------------- |
| ⚡ Faster load times       | No new data downloaded      |
| 🧮 Less bandwidth         | Especially for large assets |
| 🖥️ Reduced server load   | CDN + browser caching       |
| 🌐 Better user experience | Instant reloads             |
| 🔋 Better for mobile data | Saves data costs            |

This is why large sites like YouTube, Amazon, and Instagram rely heavily on ETags & 304 responses.

---

🧩 How 304 Works

- Browser stores cached files (CSS, JS, images).

- On next visit, browser checks:

  - If-Modified-Since

  - If-None-Match (ETag)

- Server compares timestamps/hashes.

- If unchanged → 304 Not Modified

- Browser loads instantly from local cache.

---

## ⚙️ Developer Notes

- 304 responses contain NO body.

- Must be used with:

  - `ETag`

  - `Last-Modified`

  - `Cache-Control`

- Server must return correct caching headers.

- Never use 304 for dynamic pages unless you manage cache validation.

---

## 📦 Example Response with Caching Headers

```http
HTTP/1.1 200 OK
ETag: "abc123"
Last-Modified: Tue, 20 Jan 2025 10:30:00 GMT
Cache-Control: max-age=86400
```

**Next request:**

```http
GET /app.js
If-None-Match: "abc123"
```

**→ Server responds:**

```http
304 Not Modified
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

- MDN Docs — 304 Not Modified

- RFC 9110 — HTTP Caching
