<h1 align="center">🚫 306 (Unused)</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-306-grey?style=for-the-badge&logo=http" alt="306 Badge" />
  <img src="https://img.shields.io/badge/Type-Deprecated-red?style=for-the-badge&logo=ban" alt="Deprecated Badge" />
</p>

---

## ⚠️ Important Notice

The **306 status code** is **no longer used** and has been **reserved** in the HTTP specification.  
It **previously indicated** that a client should switch to a different proxy,  
but this behavior was removed due to lack of real-world use and security concerns.

> 💬 **In simple terms:**  
> “This code exists in the history books — but not in real-world HTTP.”

---

## 📖 Background

Originally, **306** was defined in early HTTP drafts as:

> “Switch Proxy” — indicating that subsequent requests should use a new proxy server.

But the idea was considered too unclear and potentially unsafe,  
so it was completely **abandoned** before major browsers ever implemented it.

---

## 🧩 Why 306 Was Abandoned

- No clear benefit in practice  

- Confusing semantics  

- Security risks (proxy redirection issues)  

- Never adopted by user agents  

- Replaced by safer, more explicit mechanisms (307, 308)

**The code was kept reserved to avoid reassigning it in the future**,  
which prevents breaking old software or documentation.

---

## 🧠 Real-Life Analogy

Imagine a page in a rulebook that says:

> “This section intentionally left blank.”

That’s **306** — it exists, but does nothing.

---

## 🚀 How Servers Handle 306 Today

Modern servers and browsers treat 306 as:

- **Invalid**

- **Unused**

- **Not actionable**

- **Not returned under any normal circumstances**

Tools like Postman, cURL, Chrome, and Node.js **do not use** or **recognize** 306 in active responses.

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

- RFC 2616 (Historic)  

- RFC 7231 — Officially marks 306 as unused  

- MDN — 306 Status (Unused)  
