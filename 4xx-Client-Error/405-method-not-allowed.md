<h1 align="center">🧱 405 Method Not Allowed</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-405-red?style=for-the-badge&logo=http" alt="405 Badge" />
  <img src="https://img.shields.io/badge/Type-Client%20Error-critical?style=for-the-badge&logo=ban" alt="Client Error Badge" />
</p>

---

## 📖 Definition

The **405 Method Not Allowed** status code means that the **HTTP method used in the request  
is not supported for the requested resource**, even though the resource itself exists.

> 💬 **In simple words:**  
> “This URL exists — but you can’t use *this* HTTP method on it.”

---

## 🧩 When Does 405 Occur?

A `405` error occurs when:

- You use `POST` on a route that only supports `GET`
- You try `DELETE` on a read-only resource
- You send `PUT` where only `PATCH` is allowed
- The endpoint exists, but the method is restricted

⚠️ The key point:  
**The resource exists — the method is the problem.**

---

## 💻 Example 1 — Wrong HTTP Method

**Client Request:**

```http
POST /api/users HTTP/1.1
```

**But the server only supports:**

```http
GET /api/users
```

**Server Response:**

```http
HTTP/1.1 405 Method Not Allowed
Allow: GET
```

**🎯 Meaning:**

The client must use GET, not POST.

---

## 💻 Example 2 — Attempting DELETE on Read-Only Resource

```http
DELETE /api/settings HTTP/1.1
```

**Response:**

```http
HTTP/1.1 405 Method Not Allowed
Allow: GET, PUT
```

---

## 🧠 Real-Life Analogy

Imagine a door with a sign 🚪:

> “Push only.”

You try to pull it.

The door exists, it works —
but you’re using the wrong action.

That’s **405 Method Not Allowed**.

---

## 🚀 Common Use Cases

| Scenario                   | Why 405?                |
| -------------------------- | ----------------------- |
| POST on read-only endpoint | Method not supported    |
| DELETE on protected route  | Action not allowed      |
| PUT instead of PATCH       | Wrong update method     |
| API misuse                 | Invalid client behavior |
| Strict REST APIs           | Enforce correct methods |

---

## ⚙️ Developer Notes (Very Important)

**✅ Use 405 when:**

- Route exists

- Method is invalid for that route

- Server wants to inform allowed methods

**❌ Do NOT use 405 when**:

- Route does not exist → 404 Not Found

- User lacks permission → 403 Forbidden

- Request format is invalid → 400 Bad Request

---

## 🧪 Express.js Example

app.get("/api/profile", (req, res) => {
  res.json({ name: "Anirudha" });
});

app.post("/api/profile", (req, res) => {
  res.status(405).set("Allow", "GET").send();
});

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 404 and 405?

**Answer:**

- 404 → Route does not exist

- 405 → Route exists, but method is not allowed
  
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

- MDN Docs — 405 Method Not Allowed

- RFC 9110 — Client Error Semantics
