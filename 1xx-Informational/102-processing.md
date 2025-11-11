<h1 align="center">⚙️ 102 Processing</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-102-blue?style=for-the-badge&logo=http" alt="102 Processing Badge" />
  <img src="https://img.shields.io/badge/Type-Informational-lightblue?style=for-the-badge&logo=gear" alt="Informational Type Badge" />
</p>

---

## 📖 Definition

The **102 Processing** status code means the server has received the request and is **still working on it**,  
but no final response is ready **yet**.

This is used by servers that **take a long time** to process a request — for example, when handling a large database operation or multiple sub-requests.

> 💬 It’s like saying: “Hang tight! I’m still working on your request ⏳.”

---

## ⚙️ Typical Use Case

When a server knows the request will take some time (like processing large uploads or complex queries),  
it sends `HTTP/1.1 102 Processing` to let the client know that:

- The request is valid ✅  
- The server is still working 🛠️  
- The client should **not timeout or retry yet** 🕐  

---

## 💻 Example Request & Response

**Client Request:**

```http
DELETE /api/users/42 HTTP/1.1
Host: example.com
```

**Server Response (initial):**

```http
HTTP/1.1 102 Processing
```

**Server Response (final, after completion):**

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "message": "User deleted successfully!"
}
```

---

## 🧠 Real-Life Analogy

Imagine you’re waiting at a pizza counter 🍕:
You place your order, and the chef says —

> “Got it, it’s in the oven! 🔥 Please wait a bit.”

That “in progress” message is your 102 Processing — confirmation that your order is being handled!

---

## 🚀 Common Use Cases

| Use Case                   | Description                                                      |
| -------------------------- | ---------------------------------------------------------------- |
| 🗂️ Long-running requests  | Servers processing big data or large uploads.                    |
| 🧰 WebDAV operations       | Commonly used with WebDAV protocol (e.g., file synchronization). |
| 🕐 Prevent client timeouts | Keeps clients from resending the same request.                   |

---

## 🧩 Developer Notes

- Mostly used in WebDAV and advanced REST APIs.

- Rarely seen in typical web applications.

- Can be useful when requests involve chained backend operations.

- The client should wait for the final 2xx, 4xx, or 5xx response before proceeding.

---

## 💡 Example with Express.js (Conceptual)

```js
app.post("/process-data", (req, res) => {
  res.status(102).end(); // tell client we're processing

  setTimeout(() => {
    // simulate long processing
    res.status(200).json({ message: "Processing complete!" });
  }, 5000);
});
```

🧩 In reality, most frameworks don’t send multiple responses easily —
but this demonstrates how a `102 Processing` would conceptually work.

---

## 🔗 Related Codes

- 100 Continue 🩵

- 101 Switching Protocols 🔁

---

## 🧩 References

- [MDN Docs – 102 Processing](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/102)

- [RFC 2518 – HTTP Extensions for Distributed Authoring (WebDAV)](https://datatracker.ietf.org/doc/html/rfc2518#section-10.1)

---

<p align="center">💚 <strong>Next Section:</strong> <a href="../2xx-Success/README.md">2xx – Success Codes →</a></p>
