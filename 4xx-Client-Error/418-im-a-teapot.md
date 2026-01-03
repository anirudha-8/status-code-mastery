<h1 align="center">🫖 418 I’m a Teapot</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-418-red?style=for-the-badge&logo=http" alt="418 Badge" />
  <img src="https://img.shields.io/badge/Type-Easter%20Egg-fun?style=for-the-badge&logo=coffee" alt="Teapot Badge" />
</p>

---

## ☕ A Bit of Fun History

The **418 I’m a Teapot** status code was defined as an **April Fools’ joke**  
in **RFC 2324 — Hyper Text Coffee Pot Control Protocol (HTCPCP)**.

Despite being a joke, it became **famous**, **widely recognized**,  
and is often used humorously in APIs and interviews.

> 🫖 The server refuses to brew coffee because it is, permanently, a teapot.

---

## 📖 Definition

The **418 I’m a Teapot** status code indicates that the server **refuses to perform the requested action**  
because it is **not capable of doing so**, in a humorous or symbolic sense.

> 💬 **In simple words:**  
> “I can’t do that — and I never will.”

---

## 🧩 When Does 418 Occur? (Practically)

In real-world projects, `418` is sometimes used:

- As an **Easter egg**
- For **humorous error handling**
- In demos or learning projects
- To signal “this endpoint should never be called”
- In rate-limiting jokes or bot detection

⚠️ **418 should NOT be used in serious production APIs.**

---

## 💻 Example — Coffee vs Teapot

**Client Request:**

```http
BREW /coffee HTTP/1.1
```

**Server Response:**

```http
HTTP/1.1 418 I’m a Teapot

{
  "error": "I’m a teapot, not a coffee machine ☕❌"
}
```

---

## 🧠 Real-Life Analogy

You ask a teapot 🫖:

> “Make me a coffee.”

The teapot replies:

> “I’m a teapot.”

That’s **418** — request rejected, with attitude 😄.

---

## 🚀 Why Developers Love 418

| Reason             | Explanation              |
| ------------------ | ------------------------ |
| Memorable          | Everyone remembers it    |
| Interview-friendly | Fun discussion starter   |
| Easter eggs        | Adds personality         |
| Teaching HTTP      | Makes learning enjoyable |
| Community culture  | Classic RFC joke         |

---

## ⚙️ Developer Notes

**✅ Acceptable Uses**

- Learning projects

- Demo APIs

- Easter eggs

- Playful error handling

**❌ Avoid Using 418 For**

- Authentication errors

- Validation errors

- Production REST APIs

- Serious client-server communication

---

## 🔥 Interview Tip

**💬 Question:**

> Is 418 a real HTTP status code?

**Answer:**

Yes — it is officially documented in RFC 2324,
but it’s meant as a joke and not for serious use.

---

## 🧪 Express.js Fun Example

```js
app.get("/coffee", (req, res) => {
  res.status(418).json({
    message: "I’m a teapot 🫖 — I can’t brew coffee!",
  });
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

- RFC 2324 — HTCPCP

- MDN Docs — 418 I’m a Teapot
