<h1 align="center">🩵 100 Continue</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-100-blue?style=for-the-badge&logo=http" alt="100 Continue Badge" />
  <img src="https://img.shields.io/badge/Type-Informational-lightblue?style=for-the-badge&logo=bookstack" alt="Informational Type Badge" />
</p>

---

## 📖 Definition

The **100 Continue** status code means the server has **received the request headers** and the client should **proceed to send the request body**.

It’s used when the client wants to **check if the server is ready** before sending a large payload (like a big file upload).

> 🧠 **In short:** The server is saying — “✅ Got your headers, go ahead and send the rest!”

---

## ⚙️ Typical Scenario

1. 🧍 The client sends a request with the header `Expect: 100-continue`.  
2. 🖥️ The server replies with `HTTP/1.1 100 Continue` — meaning it’s okay to continue.  
3. 📦 The client then sends the request body (e.g., a file or form data).  

---

## 💻 Example Request & Response

**Client Request:**

```http
POST /api/upload HTTP/1.1
Host: example.com
Content-Length: 10240
Expect: 100-continue
Content-Type: application/json
```

**Server Response:**

```http
HTTP/1.1 100 Continue
```

➡️ Then the client sends the rest of the body:

```http
{
  "fileName": "profile-picture.png",
  "fileSize": "10MB"
}
```

Finally, after successful upload:

```http
HTTP/1.1 201 Created
```

---

## 🍔 Real-Life Analogy

Imagine you’re at a restaurant:

- You: “Can I place a big order?” 🍔

- Waiter: “Sure, go ahead!” ✅
   That “Sure, go ahead!” is your 100 Continue — permission to proceed.

---

## 🚀 Common Use Cases

| Use Case                        | Description                                            |
| ------------------------------- | ------------------------------------------------------ |
| 🪣 Large file uploads           | Helps avoid wasting bandwidth if server refuses early. |
| 🔒 API requests with validation | Client ensures the server is ready to process.         |
| 🧠 Efficient communication      | Prevents sending huge bodies unnecessarily.            |

---

## ⚠️ Developer Tips

- Always use Expect: 100-continue when sending large requests.

- Some servers automatically handle it, others may skip this step.

- If you never send large payloads, you might never see this code.

---

## 🔗 Related Codes

- 101 Switching Protocols 🔁

- 102 Processing ⚙️

## 🧩 Reference

- [MDN Docs – 100 Continue](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/100)

- [RFC 9110, Section 15.2.1 – 100 Continue](https://datatracker.ietf.org/doc/html/rfc9110#name-100-continue)

---

<p align="center">🩵 <strong>Next:</strong> <a href="./101-switching-protocols.md">101 Switching Protocols →</a></p>
