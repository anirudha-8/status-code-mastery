<h1 align="center">🗑️ 410 Gone</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-410-red?style=for-the-badge&logo=http" alt="410 Badge" />
  <img src="https://img.shields.io/badge/Type-Permanent%20Removal-critical?style=for-the-badge&logo=trash-2" alt="Gone Error Badge" />
</p>

---

## 📖 Definition

The **410 Gone** status code means that the requested resource **used to exist**,  
but has been **permanently removed** and **will not be available again**.

Unlike **404 Not Found**, the server explicitly knows that the resource is gone forever.

> 💬 **In simple words:**  
> “This resource existed earlier — but it’s permanently deleted now.”

---

## 🧩 When Does 410 Occur?

A `410 Gone` error is returned when:

- A resource has been intentionally and permanently removed  
- The server wants to tell clients **not to retry**  
- Old content is retired and should not be indexed  
- An API endpoint is sunset and replaced  

This is a **stronger signal** than 404.

---

## 💻 Example 1 — Deleted Resource

**Client Request:**

```http
GET /api/posts/123 HTTP/1.1
```

**Server Response:**

HTTP/1.1 410 Gone

```http
{
  "error": "This post has been permanently deleted"
}
```

**🎯 Meaning:**

The post existed earlier, but is intentionally removed.

---

## 💻 Example 2 — Deprecated API Endpoint

```http
GET /api/v1/users HTTP/1.1
```

**Response:**

```http
HTTP/1.1 410 Gone

{
  "message": "This API version has been retired. Use /api/v2/users"
}
```

---

## 🧠 Real-Life Analogy

You visit a shop that used to exist 🏪
There’s a sign saying:

> “This store has permanently closed.”

That’s **410 Gone** — not “maybe later”, but never again.

---

## 🚀 Common Use Cases

| Scenario               | Why 410?                        |
| ---------------------- | ------------------------------- |
| Deleted posts/comments | Permanently removed             |
| Sunset APIs            | Old versions retired            |
| Legal takedowns        | Content removed forever         |
| Cleanup of stale URLs  | Explicit removal                |
| SEO de-indexing        | Strong signal to search engines |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 410 when:**

- Resource is intentionally removed

- You want clients to stop retrying

- You want search engines to de-index faster

**❌ Do NOT use 410 when:**

- Resource may come back → 404 Not Found

- User lacks permission → 403 Forbidden

- Resource never existed → 404 Not Found

---

## 🔥 SEO Tip (Interview Gold ⭐)

- **404** → “I don’t know if this existed”

- **410** → “This definitely existed and is gone forever”

Search engines remove 410 URLs faster than 404s.

---

## 🧪 Express.js Example

```js
app.get("/api/old-post/:id", (req, res) => {
  return res.status(410).json({
    error: "This resource has been permanently removed",
  });
});
```

---

## 📚 References

- MDN Docs — 410 Gone

- RFC 9110 — Client Error Responses
