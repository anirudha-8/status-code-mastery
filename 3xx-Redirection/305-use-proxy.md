<h1 align="center">🖧 305 Use Proxy</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-305-orange?style=for-the-badge&logo=http" alt="305 Badge" />
  <img src="https://img.shields.io/badge/Type-Deprecated-red?style=for-the-badge&logo=warning" alt="Deprecated Badge" />
</p>

---

## ⚠️ Important Notice

The **305 Use Proxy** status code is **deprecated** due to serious **security vulnerabilities**  
and is **not used by modern browsers or servers**.

Most systems treat it as **invalid**.

> ⚠️ **Do NOT use 305 in real-world applications.**

---

## 📖 Historical Definition

Originally, **305 Use Proxy** meant:

> “To access this resource, the client **must use the proxy** specified in the `Location` header.”

Example from the old RFC:

```http
HTTP/1.1 305 Use Proxy
Location: http://proxy.example.com:8080
```

This forced clients to route their request through a specific proxy server.

---

## 🧩 Why 305 Was Deprecated

### 🚨 Major Security Concerns

- A malicious server could force clients to use a dangerous proxy

- Users could be unknowingly exposed to:

  - Man-in-the-middle attacks

  - Data injection

  - Credential theft

- Browsers refused to implement it due to high risk

Hence, 305 is disabled in all major browsers (Chrome, Firefox, Edge, Safari).

---

## 🧠 Real-Life Analogy

Imagine a shop telling you:

> “You can only buy through this middleman.”

But the middleman is unknown, untrusted, and possibly dangerous.

That’s why the 305 code was abandoned.

---

## 💻 Example (Historical Only)

**Request:**

```http
GET /private-data HTTP/1.1
```

**Hypothetical Response:**

```http
HTTP/1.1 305 Use Proxy
Location: http://proxy.example.com:8080
```

🔴 Modern browsers will ignore this response.

---

## 🚀 Modern Alternatives

| Use Case                        | Modern Approach                         |
| ------------------------------- | --------------------------------------- |
| Routing traffic through a proxy | Client configuration, not HTTP response |
| Load balancing                  | Reverse proxies (NGINX, HAProxy)        |
| Authentication proxy            | 407 Proxy Authentication Required       |
| Network security                | VPNs, firewalls                         |

---

## ⚙️ Developer Notes

- Never use 305 in APIs or apps

- Browsers do not obey the redirect

- Most HTTP libraries ignore or reject it

- Exists only for historical completeness

- Rarely seen outside old RFC examples

---

## 🔗 Related Codes

- [300 Multiple Choices](./300-multiple-choices.md)📚

- [301 Moved Permanently](./301-moved-permanently.md)🔒

- [302 Found](./302-found.md)🔁

- [303 See Other](./303-see-other.md)🔗

- [304 Not Modified](./304-not-modified.md)🗂️

- [305 Use Proxy](./305-use-proxy.md) | 🖧

- [306 Switch Proxy](./306-switch-proxy.md)🚫

- [307 Temporary Redirect](./307-temporary-redirect.md)🔄

- [308 Permanent Redirect](./308-permanent-redirect.md)📌

---

## 📚 References

- MDN Docs — 305 Use Proxy

- RFC 2616 (Deprecated)

- RFC 7231 — Removal of 305 support
