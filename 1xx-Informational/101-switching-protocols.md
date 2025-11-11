<h1 align="center">🔁 101 Switching Protocols</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-101-blue?style=for-the-badge&logo=http" alt="101 Switching Protocols Badge" />
  <img src="https://img.shields.io/badge/Type-Informational-lightblue?style=for-the-badge&logo=cloudflare" alt="Informational Type Badge" />
</p>

---

## 📖 Definition

The **101 Switching Protocols** status code indicates that the server understands the client's request to **change the communication protocol**, and has agreed to switch.

This is most commonly used when a client requests to upgrade from **HTTP → WebSocket**, or **HTTP/1.1 → HTTP/2**.

> 💬 It’s like saying: “Okay, let’s switch gears and continue in a new way!” ⚙️

---

## ⚙️ How It Works

1. 🧍 **Client** sends a request with the header `Upgrade: <new-protocol>`.  
2. 🖥️ **Server** agrees and replies with `HTTP/1.1 101 Switching Protocols`.  
3. 🔄 Both parties now communicate using the new protocol.

---

## 💻 Example Request & Response

**Client Request:**

```http
GET /chat HTTP/1.1
Host: example.com
Upgrade: websocket
Connection: Upgrade
```

**Server Response:**

```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
```

➡️ After this, both the client and server start communicating via the WebSocket protocol instead of HTTP.

---

## 🧠 Real-Life Analogy

Imagine you’re talking to someone in English 🇬🇧, and midway you both agree to switch to Hindi 🇮🇳 for better understanding.
That moment of agreement is 101 Switching Protocols — same people, new way of communicating 🗣️✨

---

## 🚀 Common Use Cases

| Use Case                   | Description                                            |
| -------------------------- | ------------------------------------------------------ |
| 💬 **WebSocket upgrade**   | Switch from HTTP to a persistent WebSocket connection. |
| 🌐 **HTTP version change** | Moving from HTTP/1.1 to HTTP/2 (rare in real world).   |
| 🔄 **Protocol handshake**  | When server supports multiple communication methods.   |

---

## 🧩 Developer Notes

- The request must include both headers:

  - Upgrade: protocol-name

  - Connection: Upgrade

- Once switched, HTTP headers no longer apply — communication happens under the new protocol rules.

- If the server does not support the upgrade, it simply ignores the header and continues normally.

---

## 🔍 Example (Node.js WebSocket Server)

```js
import http from "http";
import { WebSocketServer } from "ws";

const server = http.createServer();

const wss = new WebSocketServer({ server });

wss.on("connection", (ws) => {
  ws.send("Connected via WebSocket!");
});

server.listen(3000, () => console.log("Listening on :3000"));
```

In this setup, when the client sends an Upgrade: websocket header,
the server replies with 101 Switching Protocols and establishes a WebSocket connection. ⚡

---

## 🔗 Related Codes

- 100 Continue 🩵

- 102 Processing ⚙️

---

## 🧩 References

- [MDN Docs – 101 Switching Protocols](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/101)

- [RFC 9110, Section 15.2.2 – 101 Switching Protocols](https://datatracker.ietf.org/doc/html/rfc9110#name-101-switching-protocols)

---

<p align="center">⚙️ <strong>Next:</strong> <a href="./102-processing.md">102 Processing →</a></p>
