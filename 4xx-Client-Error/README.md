<h1 align="center">❤️ 4xx – Client Error Responses</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Category-Client%20Error-red?style=for-the-badge&logo=bug" alt="4xx Client Error Badge" />
  <img src="https://img.shields.io/badge/HTTP%20Status%20Codes-4xx-critical?style=for-the-badge&logo=googlechrome" alt="HTTP 4xx Codes" />
</p>

---

## 🧠 What Are 4xx Client Error Codes?

The **4xx class** of HTTP status codes indicates that **the client made a mistake**  
— the request is invalid, unauthorized, malformed, or cannot be processed by the server.

> 💬 **In simple words:**  
> “The server received your request, but *you* need to fix something.”

These errors are extremely common during:

- API development  
- Frontend-backend integration  
- Authentication & authorization  
- Input validation  
- Debugging production issues  

---

## 🧩 Quick Summary of 4xx Codes

| Code | Name | Meaning |
|------|------|--------|
| [400 Bad Request](./400-bad-request.md) | ❌ Bad Request | Invalid syntax or malformed request |
| [401 Unauthorized](./401-unauthorized.md) | 🔐 Unauthorized | Authentication required or failed |
| [403 Forbidden](./403-forbidden.md) | 🚫 Forbidden | You don’t have permission |
| [404 Not Found](./404-not-found.md) | 🔍 Not Found | Resource does not exist |
| [405 Method Not Allowed](./405-method-not-allowed.md) | 🧱 Method Not Allowed | HTTP method not supported |
| [406 Not Acceptable](./406-not-acceptable.md) | 🎭 Not Acceptable | Cannot generate acceptable response |
| [407 Proxy Authentication Required](./407-proxy-authentication-required.md) | 🖧 Proxy Auth Required | Proxy authentication needed |
| [408 Request Timeout](./408-request-timeout.md) | ⏱️ Timeout | Client took too long |
| [409 Conflict](./409-conflict.md) | ⚔️ Conflict | Request conflicts with server state |
| [410 Gone](./410-gone.md) | 🗑️ Gone | Resource permanently removed |
| [411 Length Required](./411-length-required.md) | 📏 Length Required | Missing Content-Length |
| [412 Precondition Failed](./412-precondition-failed.md) | ❗ Precondition Failed | Conditional headers failed |
| [413 Payload Too Large](./413-payload-too-large.md) | 📦 Too Large | Request body too big |
| [414 URI Too Long](./414-uri-too-long.md) | 🔗 URI Too Long | URL length exceeded |
| [415 Unsupported Media Type](./415-unsupported-media-type.md) | 🧪 Unsupported Media Type | Invalid content-type |
| [416 Range Not Satisfiable](./416-range-not-satisfiable.md) | 📉 Invalid Range | Bad range request |
| [417 Expectation Failed](./417-expectation-failed.md) | 🤔 Expectation Failed | Expect header not met |
| [418 I'm a Teapot](./418-im-a-teapot.md) | 🫖 Teapot | Fun / Easter egg |
| [422 Unprocessable Entity](./422-unprocessable-entity.md) | 🧠 Validation Error | Semantic errors |
| [429 Too Many Requests](./429-too-many-requests.md) | 🚦 Rate Limited | Too many requests |
| [431 Request Header Fields Too Large](./431-request-header-fields-too-large.md) | 📜 Headers Too Large | Headers exceeded limit |
| [451 Unavailable For Legal Reasons](./451-unavailable-for-legal-reasons.md) | ⚖️ Legal Restriction | Blocked by law |

---

## 💻 Common 4xx Error Example

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "email": "not-an-email"
}
```

**Response:**

```http
HTTP/1.1 400 Bad Request

{
  "error": "Invalid email format"
}
```

**🎯 Meaning:**

The request reached the server, but input validation failed.

---

## 🧠 Real-Life Analogy

Imagine going to an ATM 🏧:

- Enter wrong PIN → **401 Unauthorized**

- Try to withdraw more than allowed → **403 Forbidden**

- Request non-existing service → **404 Not Found**

- Hit withdraw button too fast repeatedly → **429 Too Many Requests**

That’s the **4xx family** in action.

---

## 🚀 Why 4xx Codes Matter (Very Important)

| Reason               | Benefit                     |
| -------------------- | --------------------------- |
| Better debugging     | Clear error cause           |
| Secure APIs          | Prevent unauthorized access |
| Better UX            | Meaningful error messages   |
| Interview questions  | Frequently asked            |
| Clean backend design | Proper REST practices       |

---

## ⚙️ Developer Best Practices

- Never return 200 OK for errors ❌

- Always include:

  - Clear error message

  - Error code

  - Optional error details

- Use correct codes:

  - Auth issue → 401 / 403

  - Validation → 400 / 422

  - Rate limiting → 429

- Log 4xx errors for debugging, but don’t panic - they’re client-side issues.

---

## 🔥 Interview Tip

💬 If interviewer asks:

> “What’s the difference between 401 and 403?”

**Answer:**

- 401 → Who are you? (Authentication missing/invalid)

- 403 → I know who you are, but you’re not allowed

---

## 🔗 References

- MDN Web Docs — Client Error Responses

- RFC 9110 — HTTP Semantics
