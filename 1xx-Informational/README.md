<h1 align="center">🩵 1xx - Informational Responses</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Category-Informational-blue?style=for-the-badge&logo=icloud" alt="1xx Informational" />
  <img src="https://img.shields.io/badge/HTTP%20Status%20Codes-1xx-lightblue?style=for-the-badge&logo=http" alt="HTTP 1xx Codes" />
</p>

---

## 🧠 What Are 1xx Informational Codes?

These status codes indicate that **the request has been received** and the server is **continuing the process**.  
They are **temporary responses** — not the final status of the request.

> 💡 Think of them as *“Hold on, I got your request, processing it…”* signals from the server.

---

## 🧩 Quick Summary

| Code | Name | Description |
|------|------|--------------|
| [100 Continue](./100-continue.md) | ✅ Continue | The server has received the request headers and the client should proceed to send the body. |
| [101 Switching Protocols](./101-switching-protocols.md) | 🔁 Switching Protocols | The requester asked the server to switch protocols, and the server agreed. |
| [102 Processing](./102-processing.md) | ⚙️ Processing | The server has received and is processing the request, but no response is available yet. |

---

## ⚙️ How They Work

1. 🧍 **Client** sends a request to the server (sometimes large, like file uploads).  
2. 🖥️ **Server** responds with a 1xx code — confirming it got the headers and is ready.  
3. 📦 **Client** continues sending the rest of the data or waits for the final status (2xx, 4xx, 5xx).  

---

## 💬 Real-Life Analogy

Imagine ordering food 🍔 at a restaurant:

- You place your order (request sent)
- The waiter says “Got it, we’re preparing it!” → that’s **1xx**
- Later, they bring your meal → that’s **2xx**

---

## 💻 Example Flow

```http
POST /upload HTTP/1.1
Host: example.com
Expect: 100-continue
Content-Length: 348

[file data...]
```

## Server Response

```http
HTTP/1.1 100 Continue
```

➡️ Then the client continues sending the file.
After successful upload:

```http
HTTP/1.1 201 Created
```

---

## 🧩 Related Codes in This Category

| Code File                                                  |Summary |
| ---------------------------------------------------------- | ------------------------------------------------------------ |
| 🩵 [100 Continue](./100-continue.md)                       | Basic acknowledgment to continue sending request data.       |
| 🔁 [101 Switching Protocols](./101-switching-protocols.md) | Indicates protocol change accepted (e.g., HTTP → WebSocket). |
| ⚙️ [102 Processing](./102-processing.md)                   | Informs that the server is still working on your request.    |

---

## 🪄 Developer Tips

- 💬 These codes are not often seen directly by end-users.

- ⚙️ They help in large data transfers and protocol upgrades.

- 🔍 Tools like Postman or cURL can show 1xx responses if you enable verbose logs.

---

## 🔗 Learn More

- [MDN Web Docs – HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status)

- [RFC 9110 – HTTP Semantics (IETF)](https://datatracker.ietf.org/doc/html/rfc9110#section-15.2)

---

<p align="center">🩵 <strong>Next Up:</strong> <a href="../2xx-Success/README.md">2xx – Success Codes →</a></p>
