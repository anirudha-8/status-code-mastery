<h1 align="center">🌐 505 HTTP Version Not Supported</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-505-orange?style=for-the-badge&logo=http" alt="505 Badge" />
  <img src="https://img.shields.io/badge/Type-Protocol%20Error-critical?style=for-the-badge&logo=globe" alt="HTTP Version Error Badge" />
</p>

---

## 📖 Definition

The **505 HTTP Version Not Supported** status code means that the server  
**does not support the HTTP protocol version** used in the client’s request.

The request is valid in structure, but the **protocol version itself is unsupported**.

> 💬 **In simple words:**  
> “I don’t understand this HTTP version.”

---

## 🧩 When Does 505 Occur?

A `505` error occurs when:

- Client uses an unsupported HTTP version  
- Server only supports older/newer protocol versions  
- Legacy systems reject modern HTTP versions  
- Experimental or invalid HTTP versions are sent  
- Proxy/gateway enforces strict protocol rules  

⚠️ This is **rare**, but important at the protocol level.

---

## 💻 Example 1 — Unsupported HTTP Version

**Client Request:**

```http
GET /api/data HTTP/2.0
```

Server supports only: `HTTP/1.1`

**Server Response:**

```http
HTTP/1.1 505 HTTP Version Not Supported
```

🎯 Meaning:

The server cannot handle HTTP/2 requests.

---

## 💻 Example 2 — Invalid HTTP Version

```http
GET /api/data HTTP/9.9
```

**Response:**

```http
HTTP/1.1 505 HTTP Version Not Supported
```

---

## 🧠 Real-Life Analogy

You try to play a Blu-ray disc 📀
in a VHS player 📼.

The player replies:

> “I don’t support this format.”

That’s **505 HTTP Version Not Supported**.

---

## 🚀 Common Use Cases

| Scenario              | Why 505?             |
| --------------------- | -------------------- |
| Legacy servers        | No HTTP/2 support    |
| Strict gateways       | Protocol enforcement |
| Experimental clients  | Invalid versions     |
| Misconfigured proxies | Version mismatch     |
| Custom HTTP stacks    | Limited support      |

---

## ⚙️ Developer Notes (Important)

**✅ Use 505 when:**

- HTTP version is unsupported

- Server explicitly rejects the protocol version

**❌ Do NOT use 505 when:**

- Request method is unsupported → 501 Not Implemented

- Server crashes → 500 Internal Server Error

- Gateway fails upstream → 502 / 504

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 505 and 400?

**Answer:**

- **505** → HTTP protocol version is unsupported

- **400** → Request syntax is malformed

---

## 🧪 Server Configuration Example

Apache (example):

```apache
Protocols h2 http/1.1
```

If client requests unsupported version → 505

---

## 🔗 Related Codes

- [500 Internal Server Error](./500-internal-server-error.md)💥

- [501 Not Implemented](./501-not-implemented.md)🚧

- [502 Bad Gateway](./502-bad-gateway.md)🔌

- [503 Service Unavailable](./503-service-unavailable.md)🛑

- [504 Gateway Timeout](./504-gateway-timeout.md)⏳

- [505 HTTP Version Not Supported](./505-http-version-not-supported.md)🌐

---

## 📚 References

- MDN Docs — 505 HTTP Version Not Supported

- RFC 9110 — HTTP Semantics
