<h1 align="center">🔍 404 Not Found</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-404-red?style=for-the-badge&logo=http" alt="404 Badge" />
  <img src="https://img.shields.io/badge/Type-Client%20Error-critical?style=for-the-badge&logo=search" alt="Client Error Badge" />
</p>

---

## 📖 Definition

The **404 Not Found** status code means that the server **could not find the requested resource**.  
The request was valid, but the URL or resource **does not exist** on the server.

> 💬 **In simple words:**  
> “I understood your request, but there’s nothing here.”

---

## 🧩 When Does 404 Occur?

A `404` error happens when:

- The URL is incorrect or misspelled  
- The resource has been deleted  
- The endpoint does not exist  
- The route is not implemented on the server  
- The client requests an invalid ID  

The server **does not know** whether the resource existed before — only that it’s not available now.

---

## 💻 Example 1 — Non-Existing API Route

**Client Request:**

```http
GET /api/products/99999 HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 404 Not Found

{
  "error": "Product not found"
}
```

**🎯 Meaning**:

The product with ID 99999 does not exist.

---

## 💻 Example 2 — Wrong URL Path

```http
GET /api/usres HTTP/1.1
```

**Response:**

```http
HTTP/1.1 404 Not Found
```

❌ Typo in /api/users.

---

## 🧠 Real-Life Analogy

You go to a library 📚 and ask for a book by its ID.
The librarian checks the system and says:

> “That book isn’t in our catalog.”

That’s 404 Not Found.

---

## 🚀 Common Use Cases

| Scenario             | Why 404?                |
| -------------------- | ----------------------- |
| Invalid API endpoint | Route does not exist    |
| Deleted resource     | ID no longer available  |
| Broken link          | Page was removed        |
| Typo in URL          | Incorrect path          |
| Wrong HTTP route     | Backend not implemented |

---

## ⚙️ Developer Notes (Very Important)

### ✅ Use 404 when

- Resource truly does not exist

- URL is incorrect

- ID is not found in database

### ❌ Do NOT use 404 when

- User is not authenticated → 401 Unauthorized

- User is authenticated but forbidden → 403 Forbidden

- Resource existed but was removed permanently → 410 Gone

---

## 🔥 SEO Tip

- **404 pages should be user-friendly**, not blank.

- For websites:

  - Show helpful message

  - Provide navigation links

  - Suggest similar pages

- Search engines expect valid 404s for missing pages.

---

## 🧪 Express.js Example

```js
app.get("/api/users/:id", (req, res) => {
  const user = users.find(u => u.id === req.params.id);

  if (!user) {
    return res.status(404).json({
      error: "User not found",
    });
  }

  res.status(200).json(user);
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

---

## 📚 References

- MDN Docs — 404 Not Found

- RFC 9110 — Client Error Responses
