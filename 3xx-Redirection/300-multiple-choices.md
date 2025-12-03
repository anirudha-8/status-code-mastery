<h1 align="center">📚 300 Multiple Choices</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-300-yellow?style=for-the-badge&logo=http" alt="300 Badge" />
  <img src="https://img.shields.io/badge/Type-Redirection-gold?style=for-the-badge&logo=list" alt="Redirection Type Badge" />
</p>

---

## 📖 Definition

The **300 Multiple Choices** status code indicates that the requested resource  
has **more than one possible representation**, and the client must choose between them.

The server returns a list of available options — usually URLs — that represent  
different versions or formats of the resource.

> 💬 **In simple words:**  
> “This resource has multiple versions. Which one do you want?”

---

## 🧩 When Is 300 Used?

This code appears when a resource exists in **multiple formats**, such as:

- Different file types (JSON, XML, HTML)  
- Different resolutions (480p, 720p, 1080p)  
- Different languages (en, hi, fr)  
- Multiple available endpoints for the same resource  
- API version choices  

Modern browsers rarely show 300-based UI,  
but APIs and intelligent systems can use it to guide user decisions.

---

## 💻 Example — Multiple Representations

**Client Request:**

```http
GET /api/docs HTTP/1.1
Host: example.com
```

**Server Response:**

```http
HTTP/1.1 300 Multiple Choices
Content-Type: application/json

{
  "options": [
    { "type": "application/json", "url": "/api/docs.json" },
    { "type": "application/xml", "url": "/api/docs.xml" },
    { "type": "text/html", "url": "/api/docs.html" }
  ]
}
```

**🎯 Meaning:** The client must choose which version they want.

---

## 🧠 Real-Life Analogy

Imagine visiting a restaurant and getting a message:

“We have three types of coffee:

- Hot Coffee

- Cold Coffee

- Iced Latte
Please choose one ☕❄️”

That’s **300 Multiple Choices** — multiple valid options.

---

## 🚀 Common Use Cases

| Scenario                      | Example                     |
| ----------------------------- | --------------------------- |
| API returns different formats | JSON / XML / HTML           |
| Media selection               | Different video resolutions |
| Localized content             | Multiple language versions  |
| Versioned APIs                | v1 / v2 / beta              |
| Multi-file download options   | zip, tar, 7z                |

---

## ⚙️ Developer Notes

- Rarely used in common web apps.

- More relevant for:

  - API gateways

  - Content negotiation

  - File servers

  - Versioned resources

- The server should include:

  - A list of valid choices

  - Preferred/Recommended option (optional)

### Important Headers

- `Content-Location`

- `Link` headers listing alternate URLs

- `Accept` & `Accept-Language` influence the choice

---

## 💻 Example With curl (Content Negotiation)

```bash
curl -H "Accept: application/xml" https://example.com/resource
```

If the server supports multiple representations, it may return:

```http
HTTP/1.1 300 Multiple Choices
```

And provide a list of options.

---

## 🔗 Related Codes

---

## 📚 References

- MDN — 300 Multiple Choices

- RFC 9110 — HTTP Semantics (Redirection Responses)
