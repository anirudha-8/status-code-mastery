<h1 align="center">💛 3xx – Redirection Responses</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Category-Redirection-gold?style=for-the-badge&logo=redirect" alt="3xx Redirection Badge" />
  <img src="https://img.shields.io/badge/HTTP%20Status%20Codes-3xx-yellow?style=for-the-badge&logo=googlechrome" alt="HTTP 3xx Codes" />
</p>

---

## 🧠 What Are 3xx Redirection Codes?

The **3xx class** of HTTP status codes indicates that further action must be taken by the client  
— usually **to reach a different URL**.

This can mean:

- Moving a resource to another location  
- Telling the client to use a cached version  
- Informing the browser to fetch a different URL automatically  
- Permanent or temporary redirects  

> 💬 **In simple words:**  
> “Go there instead — this resource has moved or requires another step.”

---

## 🧩 Quick Summary of 3xx Codes

| Code | Name | Description |
|------|------|-------------|
| [300 Multiple Choices](./300-multiple-choices.md) | 📚 Multiple Options | More than one representation available. |
| [301 Moved Permanently](./301-moved-permanently.md) | 🔒 Permanent Redirect | Resource is at a new URL forever. |
| [302 Found](./302-found.md) | 🔁 Temporary Redirect | Resource temporarily resides at a different URL. |
| [303 See Other](./303-see-other.md) | 🔗 Redirect Using GET | Client must fetch another URL with GET. |
| [304 Not Modified](./304-not-modified.md) | 🗂️ Use Cached Copy | Cached version is still valid — no need to re-download. |
| [305 Use Proxy](./305-use-proxy.md) | 🖧 Deprecated | Must use a proxy (now unused for security reasons). |
| **306** | 🚫 No Longer Used | Previously used but now reserved. |
| [307 Temporary Redirect](./307-temporary-redirect.md) | 🔄 Redirect Without Changing Method | Same as 302 but preserves the HTTP method. |
| [308 Permanent Redirect](./308-permanent-redirect.md) | 📌 Permanent Redirect Without Method Change | Like 301 but method and body are preserved. |

---

## 💻 How Redirection Works (Simple Flow)

1. Client requests a URL  
2. Server responds with **3xx** + a `Location` header  
3. Browser automatically performs the redirect  
4. Client fetches the new URL  

Example:

```http
HTTP/1.1 301 Moved Permanently
Location: https://newsite.com/newpage
```

🎯 Browser automatically navigates to the new URL.

---

## 🧠 Real-Life Analogy

Imagine going to your favorite coffee shop ☕
but a sign outside says:

> “We moved! Visit our new shop 200 meters ahead →”

That’s exactly how 301, 302, and 307/308 work.

---

## 🚀 Common Use Cases

| Scenario                          | Useful Code        |
| --------------------------------- | ------------------ |
| Switching domain (`http → https`) | **301**            |
| Temporarily redirecting a route   | **302** or **307** |
| Forcing GET after form submission | **303 See Other**  |
| Browser caching validation        | **304**            |
| Permanent URL restructuring       | **308**            |

---

## 🔥 SEO Impact (Very Important)

| Code        | SEO Effect                                     |
| ----------- | ---------------------------------------------- |
| **301**     | Passes ~90–99% link equity (good for SEO).     |
| **302**     | Temporary — search engines may not update URL. |
| **307/308** | Modern equivalents with clearer semantics.     |
| **304**     | Improves page load times through caching.      |

---

## 🧩 Developer Tips

- Use **301** for long-term changes

- Use **302**/**307** for short-term

- Use **303** after POST to avoid resubmission

- Use **304** for caching optimization

- Avoid **305** (deprecated)

- **306** is unused — only kept for historic reasons

---

## 💻 Example of 301 Redirect (Node.js)

```js
app.get("/old-route", (req, res) => {
  res.redirect(301, "/new-route");
});
```

---

## 🔗 References

- MDN Web Docs – Redirection Responses

- RFC 9110 – HTTP Semantics
