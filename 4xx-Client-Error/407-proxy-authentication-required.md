<h1 align="center">🖧 407 Proxy Authentication Required</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-407-red?style=for-the-badge&logo=http" alt="407 Badge" />
  <img src="https://img.shields.io/badge/Type-Proxy%20Authentication-critical?style=for-the-badge&logo=shield-lock" alt="Proxy Authentication Error Badge" />
</p>

---

## 📖 Definition

The **407 Proxy Authentication Required** status code means that the client must  
**authenticate itself with a proxy server** before the request can be forwarded.

It is similar to **401 Unauthorized**, but instead of authenticating with the **origin server**,  
the client must authenticate with an **intermediate proxy**.

> 💬 **In simple words:**  
> “You must log in to the proxy before accessing this resource.”

---

## 🧩 When Does 407 Occur?

A `407` error occurs when:

- The request passes through a **proxy server**
- The proxy requires authentication
- The client did not provide valid proxy credentials
- The `Proxy-Authorization` header is missing or invalid

This commonly happens in:

- Corporate networks  
- Restricted Wi-Fi environments  
- Enterprise security gateways  

---

## 💻 Example 1 — Missing Proxy Credentials

**Client Request:**

```http
GET http://example.com HTTP/1.1
```

**Proxy Response:**

```http
HTTP/1.1 407 Proxy Authentication Required
Proxy-Authenticate: Basic realm="Corporate Proxy"
```

**🎯 Meaning:**

The client must authenticate with the proxy first.

---

## 💻 Example 2 — Providing Proxy Authentication

```http
GET http://example.com HTTP/1.1
Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==
```

➡️ If credentials are valid, the proxy forwards the request to the target server.

---

## 🧠 Real-Life Analogy

You try to access the internet from your office 🏢.
Before anything loads, IT asks:

> “Please enter your employee credentials.”

That checkpoint is the proxy, and failing it results in **407**.

---

## 🚀 Common Use Cases

| Scenario                 | Why 407?                      |
| ------------------------ | ----------------------------- |
| Corporate proxy networks | Proxy authentication required |
| School/college networks  | Controlled internet access    |
| ISP-level filtering      | Gateway auth needed           |
| Secure enterprise APIs   | Traffic routed via proxy      |

---

## ⚙️ Developer Notes (Important)

### ✅ Use 407 when

- A proxy requires authentication

- Request cannot proceed without proxy credentials

### ❌ Do NOT use 407 when

- Authentication is required by the origin server → use 401 Unauthorized

- User lacks permission → use 403 Forbidden

### 401 vs 407 (Interview Favorite ⭐)

| Code    | Authentication Target |
| ------- | --------------------- |
| **401** | Origin server         |
| **407** | Proxy server          |

---

## 🧪 Example — cURL with Proxy Authentication

```bash
curl -x http://proxy.example.com:8080 \
     -U username:password \
     http://example.com
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

- MDN Docs — 407 Proxy Authentication Required

- RFC 9110 — Proxy Authentication
