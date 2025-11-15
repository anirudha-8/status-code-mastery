<h1 align="center">🧾 203 Non-Authoritative Information</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-203-green?style=for-the-badge&logo=http" alt="203 Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=info" alt="Success Badge" />
</p>

---

## 📖 Definition

The **203 Non-Authoritative Information** status code means that the request was successful,  
but the **returned metadata or response headers** may be **modified by a proxy or intermediary**,  
and are **not the original, authoritative information** from the server.

> 💬 In simple words:  
> “Here’s the data you requested — but it’s *not exactly* what the original server sent.”

---

## 🧩 When Is 203 Used?

- When a **proxy** modifies the response before sending it to the client  
- When the server returns **transformed**, **sanitized**, or **filtered** information  
- Used in cases where **cached** or **altered** metadata is returned  
- Client receives **valid** data, but **not guaranteed to be original**  

---

## 🧻 Real-World Example

Many CDN services (like Cloudflare, Akamai, Fastly) may:

- Add headers  
- Remove sensitive headers  
- Normalize cookies  
- Add compression metadata  

When this happens, the CDN may return:  
**203 Non-Authoritative Information**

---

## 💻 Example — Proxy-Modified Response

**Client Request:**

```http
GET /api/user-profile HTTP/1.1
Host: example.com
```

**Origin Server Response (original):**

```http
HTTP/1.1 200 OK
X-Origin: Direct
```

**Proxy Modified Response:**

```http
HTTP/1.1 203 Non-Authoritative Information
X-Proxy: CloudProxy
```

🎯 The client gets the data — but through a modified lens.

---

## 🧠 Real-Life Analogy

Imagine asking your friend:

> "What did the teacher say about the assignment?"

Your friend gives you the information,
but adds or removes some details before telling you 😅

That’s **203 Non-Authoritative Information** — correct info, but not straight from the original source.

---

## 🚀 Common Use Cases

| Scenario                  | Explanation                              |
| ------------------------- | ---------------------------------------- |
| CDN or Cache modification | Output passes through a proxy server     |
| Data sanitization         | Sensitive headers stripped by middleware |
| Response transformation   | Format or metadata converted             |
| Third-party middle layers | API gateways altering responses          |

---

## ⚙️ Developer Notes

- You will rarely see 203 in normal REST API usage.

- Mostly shows up in proxy-heavy architectures.

- Safe to treat it like 200 OK, but with caution about metadata integrity.

- Browsers do not handle it differently — they accept it as a success.

---

🧪 Example With a Proxy

If a proxy modifies a header:

**Original Header:**

```http
Server: Apache/2.4
```

**Modified Header From Proxy:**

```http
Server: API-Gateway-v3
```

**The proxy may respond:**

```http
HTTP/1.1 203 Non-Authoritative Information
```

---

## 🔗 Related Codes

- [200 OK](./200-ok.md) ✅ OK

- [201 Created](./201-created.md) | 🏗️

- [202 Accepted](./202-accepted.md) | ⏳

- [203 Non-Authoritative Information](./203-non-authoritative-information.md) | 🧾

- [204 No Content](./204-no-content.md) | 🚫

- [205 Reset Content](./205-reset-content.md) | 🔄

- [206 Partial Content](./206-partial-content.md) | 📦

- [207 Multi-Status](./207-multi-status.md) | 🧩

- [208 Already Reported](./208-already-reported.md) | 🔁

- [226 IM Used](./226-im-used.md) | 🧮
 📦

---

## 📚 References

- MDN Docs — 203 Non-Authoritative Information

- RFC 9110 — HTTP Semantics (Success Responses)
