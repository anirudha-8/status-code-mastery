<h1 align="center">🚫 204 No Content</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-204-green?style=for-the-badge&logo=http" alt="204 Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=serverless" alt="Success Badge" />
</p>

---

## 📖 Definition

The **204 No Content** status code means the server successfully processed the request,  
but **there is no response body to return**.

Everything worked perfectly — there’s just nothing to show.

> 💬 In simple words:  
> “Your request succeeded, but I have nothing to send back.” ✔️

---

## 🧩 When Is 204 Used?

Use **204** when an action succeeds but does **not require** returning any content.

Common cases:

- Deleting a resource  
- Updating something without returning additional data  
- Logging out / invalidating tokens  
- Saving auto-updates (like preferences)  
- Clearing notifications  

It is the **cleanest**, most lightweight response for such actions.

---

## 💻 Example 1 — DELETE Request

**Client Request:**

```http
DELETE /api/users/15 HTTP/1.1
Host: example.com
```

**Server Response:**

```http
HTTP/1.1 204 No Content
```

🎯 Meaning: User deleted successfully, nothing else to return.

---

## 💻 Example 2 — Update Without Returning Payload

**Request:**

```http
PUT /api/settings/theme HTTP/1.1
Content-Type: application/json

{
  "theme": "dark"
}
```

**Response:**

```http
HTTP/1.1 204 No Content
```

✔️ The setting was updated — no further info needed.

---

## 🧠 Real-Life Analogy

Imagine turning on a light using a switch.
You flip the switch — and that’s it.
No confirmation message, no beeps.
The action simply works.

That’s 204 No Content 🌙💡

---

## 🚀 Common Use Cases

| Scenario                    | Why 204?                         |
| --------------------------- | -------------------------------- |
| **Deleting resources**      | Clean, no-body success           |
| **Updating preferences**    | Results are implicit             |
| **Logging out**             | Nothing to return except success |
| **Marking items as read**   | No need to return data           |
| **Empty success responses** | Reduces bandwidth                |

---

## ⚙️ Developer Notes

- Never include a response body with 204 — browsers will ignore it.

- If you want to return some metadata, prefer:

  - 200 OK with body

  - 202 Accepted (for async jobs)

- HEAD requests often return 204.

- Saving bandwidth makes 204 ideal for high-traffic APIs.

---

## 🧪 cURL Example

```bash
curl -i -X DELETE https://example.com/api/products/31
```

Output:

```http
HTTP/1.1 204 No Content
```

---

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

---

## 📚 References

- MDN Docs – 204 No Content

- RFC 9110 – HTTP Semantics (Success Responses)
