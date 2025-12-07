<h1 align="center">🔗 303 See Other</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-303-orange?style=for-the-badge&logo=http" alt="303 Badge" />
  <img src="https://img.shields.io/badge/Type-Redirect%20(after%20POST)-yellow?style=for-the-badge&logo=arrow-right" alt="Redirect Badge" />
</p>

---

## 📖 Definition

The **303 See Other** status code tells the client that the response to the current request  
can be found **at a different URL**, and the client **must use the GET method** to retrieve it —  
even if the original request was POST, PUT, or DELETE.

This code is commonly used after **form submissions** or **actions that modify data**.

> 💬 **In simple terms:**  
> “Your request was successful — now go to this other page using GET.”

---

## 🧩 Why 303 Exists

To fix the confusion caused by **302 Found**, which often changed POST → GET automatically,  
the HTTP standard introduced **303** with clear meaning:

### ✔ Always redirect using **GET**  

### ✔ Never repeat the previous method  

### ✔ Prevent duplicate form submissions  

---

## 💻 Example — After Form Submission

**Request:**

```http
POST /upload HTTP/1.1
Content-Type: application/json

{
  "fileName": "resume.pdf"
}
```

**Server Response:**

```http
HTTP/1.1 303 See Other
Location: /upload/success
```

**➡️ The client must now perform:**

```http
GET /upload/success
```

This avoids accidental re-submission if the user refreshes the success page.

---

## 💻 Example — Payment or Checkout

```http
POST /checkout HTTP/1.1
```

**Response:**

```http
HTTP/1.1 303 See Other
Location: /order/summary
```

**🎯 User flow:**
Submit payment → Redirect → View summary page.

---

## 🧠 Real-Life Analogy

Imagine submitting a form at a counter. The staff says:

> “Great, you're done here.
> Now go to counter number 3 to see your result.”

That’s 303 See Other — switch counters (URLs) to see the output.

---

## 🚀 Common Use Cases

| Scenario              | Why 303?                      |
| --------------------- | ----------------------------- |
| After form submission | Avoid POST resubmission       |
| Checkout systems      | Redirect to payment summary   |
| Upload success page   | Show confirmation via GET     |
| API workflows         | Chain actions predictably     |
| OAuth workflows       | Redirect back to callback URL |

---

## ⚙️ Developer Notes

- 303 is specifically designed for POST → GET redirections.

- Ensures that reloading the result page does NOT re-run the action.

- Prefer 303 for:

  - Form submissions

  - Payment handling

  - Actions that create/update data

- Avoid using 302 for POST redirection — 303 is safer.

---

## 🧪 Node.js Example

```js
app.post("/submit-form", (req, res) => {
    // Process the form...
  res.redirect(303, "/thank-you");
});
```

---

## 📚 References

- MDN Docs — 303 See Other

- RFC 9110 — Redirection Semantics
