<h1 align="center">📉 416 Range Not Satisfiable</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-416-red?style=for-the-badge&logo=http" alt="416 Badge" />
  <img src="https://img.shields.io/badge/Type-Invalid%20Range-critical?style=for-the-badge&logo=bar-chart-2" alt="Range Error Badge" />
</p>

---

## 📖 Definition

The **416 Range Not Satisfiable** status code means that the server **cannot fulfill the range request**  
because the **specified byte range is invalid or outside the size of the resource**.

This error occurs when the client sends a `Range` header that doesn’t match the actual content length.

> 💬 **In simple words:**  
> “You asked for a part of the file that doesn’t exist.”

---

## 🧩 When Does 416 Occur?

A `416` error occurs when:

- Requested byte range exceeds file size  
- Start byte is greater than end byte  
- File is smaller than the requested range  
- Client resumes a download from an invalid offset  
- Corrupted cache causes bad range requests  

This is common in **resume downloads** and **media streaming**.

---

## 💻 Example 1 — Invalid Byte Range

**Client Request:**

```http
GET /video.mp4 HTTP/1.1
Range: bytes=1000000-2000000
```

Actual file size: `800000 bytes`

**Server Response:**

```http
HTTP/1.1 416 Range Not Satisfiable
Content-Range: bytes */800000
```

**🎯 Meaning:**

The requested range is outside the file size.

---

## 💻 Example 2 — Resume Download Gone Wrong

```http
GET /file.zip HTTP/1.1
Range: bytes=999999-
```

But the file is only `500000 bytes`.

**Response:**

```http
HTTP/1.1 416 Range Not Satisfiable
```

---

## 🧠 Real-Life Analogy

You ask a librarian 📚:

> “Please give me pages 500–600.”

The book only has 300 pages.

That’s **416 Range Not Satisfiable**.

---

## 🚀 Common Use Cases

| Scenario                 | Why 416?          |
| ------------------------ | ----------------- |
| Resume downloads         | Invalid offset    |
| Video streaming          | Bad seek position |
| Large file transfer      | Corrupt range     |
| CDN caching              | Stale metadata    |
| Partial content requests | Range mismatch    |

---

## ⚙️ Developer Notes (Important)

**✅ Use 416 when:**

- Range header is present

- Range cannot be satisfied

- Client can retry with correct range

**❌ Do NOT use 416 when:**

- Resource does not exist → 404 Not Found

- Range header is missing → 200 OK

- Request body is invalid → 400 Bad Request

---

## 🔥 Interview Tip

**💬 Question:**

> Difference between 206 and 416?

**Answer:**

- **206** Partial Content → Valid range request

- **416** Range Not Satisfiable → Invalid range request

---

## 🧪 Express.js Example (Range Validation)

```js
app.get("/file", (req, res) => {
  const range = req.headers.range;
  const fileSize = 800000;

  if (!range) {
    return res.status(200).send("Full file");
  }

  const start = Number(range.replace(/\D/g, ""));
  if (start >= fileSize) {
    return res.status(416).set("Content-Range", `bytes */${fileSize}`).send();
  }

  res.status(206).send("Partial content");
});
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

- MDN Docs — 416 Range Not Satisfiable

- RFC 9110 — Range Requests
