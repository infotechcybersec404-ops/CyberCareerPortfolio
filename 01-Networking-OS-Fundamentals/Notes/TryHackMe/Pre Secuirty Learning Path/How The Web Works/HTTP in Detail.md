### What is HTTP(S)?

- **HTTP (HyperText Transfer Protocol):** A communication protocol created by Tim Berners-Lee (1989–1991) that defines how web browsers and servers exchange data such as HTML, images, and videos.
- **HTTPS (HyperText Transfer Protocol Secure):** The encrypted, secure version of HTTP. It protects data in transit from being intercepted and verifies that the user is connected to the legitimate web server rather than an imposter.

👉 In short: **HTTP moves web data; HTTPS moves it securely and with authentication.**

### Requests And Responses

### 🔑 What is a URL (Uniform Resource Locator)?

A URL is an instruction that tells the browser **how and where** to access a resource on the internet.

**Parts of a URL (example: `http://user:password@tryhackme.com:80/view-room?id=1#task3`):**

| Part | Purpose |
| --- | --- |
| **Scheme** | Protocol to use (e.g., HTTP, HTTPS, FTP). |
| **User** | Optional credentials for authentication (`user:password`). |
| **Host** | Domain name or IP address of the server. |
| **Port** | Network port (default: 80 for HTTP, 443 for HTTPS). |
| **Path** | File name or location of the resource. |
| **Query** | Extra info sent to the server (e.g., `?id=1`). |
| **Fragment** | Reference to a section within the page (e.g., `#task3`). |

### 📤 Making a Request

A browser sends an **HTTP request** to a server to fetch resources.

**Minimal request:**

```
GET / HTTP/1.1

```

**Example request with headers:**

```
GET / HTTP/1.1
Host: tryhackme.com
User-Agent: Mozilla/5.0 Firefox/87.0
Referer: https://tryhackme.com/

```

- **Line 1:** Method (`GET`), resource (`/`), protocol version (`HTTP/1.1`).
- **Line 2:** Host being requested.
- **Line 3:** Browser type/version.
- **Line 4:** Referring page.
- **Line 5:** Blank line = end of request.

### 📥 Example Response

```
HTTP/1.1 200 OK
Server: nginx/1.15.8
Date: Fri, 09 Apr 2021 13:34:03 GMT
Content-Type: text/html
Content-Length: 98

<html>
  <head><title>TryHackMe</title></head>
  <body>Welcome To TryHackMe.com</body>
</html>

```

- **Line 1:** Protocol + status code (`200 OK` = success).
- **Line 2:** Server software/version.
- **Line 3:** Date/time of response.
- **Line 4:** Content type (HTML, image, JSON, etc.).
- **Line 5:** Content length (size of response).
- **Line 6:** Blank line = end of headers.
- **Body:** The actual requested content (HTML in this case).

👉 In short:

- **URL** = the address + instructions for accessing a resource.
- **Request** = browser asking the server for something.
- **Response** = server sending back the requested data + metadata.

### HTTP Methods

| Method | Purpose | Typical Use Case |
| --- | --- | --- |
| **GET** | Retrieve information from a server | Loading a webpage, fetching an image, requesting API data |
| **POST** | Submit data to a server (often creates new records) | Submitting a form, uploading a file, creating a new user |
| **PUT** | Update or replace existing data on the server | Editing a profile, updating a record in a database |
| **DELETE** | Remove data from the server | Deleting a user account, removing a blog post |

👉 **Quick memory hook:**

- **GET** = “Give me data”
- **POST** = “Push new data”
- **PUT** = “Polish existing data”
- **DELETE** = “Drop the data”

### HTTP Status Codes

### 🔢 Status Code Ranges

| Range | Category | Meaning |
| --- | --- | --- |
| **100–199** | Informational | Request received, continue process (rarely used today). |
| **200–299** | Success | Request completed successfully. |
| **300–399** | Redirection | Client must take additional action (e.g., follow a new URL). |
| **400–499** | Client Errors | Problem with the client’s request (missing data, unauthorized, etc.). |
| **500–599** | Server Errors | Problem on the server side (server failed to handle the request). |

### ✅ Common Status Codes

| Code | Meaning | Example Use Case |
| --- | --- | --- |
| **200 OK** | Request succeeded | Loading a webpage successfully |
| **201 Created** | Resource created | New user or blog post added |
| **301 Moved Permanently** | Resource moved to a new URL | SEO redirects, permanent page move |
| **302 Found** | Temporary redirect | Login redirect, temporary page move |
| **400 Bad Request** | Invalid request | Missing parameter in form submission |
| **401 Unauthorized** | Authentication required | Login needed before access |
| **403 Forbidden** | Access denied | User lacks permission, even if logged in |
| **404 Not Found** | Resource doesn’t exist | Broken link, mistyped URL |
| **405 Method Not Allowed** | Wrong HTTP method used | Sending `GET` where `POST` is required |
| **500 Internal Server Error** | Generic server failure | Unexpected error on backend |
| **503 Service Unavailable** | Server overloaded or down | Maintenance mode, heavy traffic |

👉 **Quick memory trick:**

- **2xx = Success**
- **3xx = Go elsewhere**
- **4xx = You messed up**
- **5xx = Server messed up**

### Headers

Headers are **extra pieces of information** sent between client and server to provide context about the request or response. They aren’t strictly required, but without them, most websites won’t function properly.

### 📤 Common **Request Headers** (Client → Server)

| Header | Purpose |
| --- | --- |
| **Host** | Specifies which website/domain to access (important for servers hosting multiple sites). |
| **User-Agent** | Identifies the browser and version; helps servers tailor responses. |
| **Content-Length** | Tells the server how much data is being sent (e.g., form submissions). |
| **Accept-Encoding** | Lists compression methods the client supports (e.g., gzip, deflate). |
| **Cookie** | Sends stored data (like session IDs) back to the server for continuity. |

### 📥 Common **Response Headers** (Server → Client)

| Header | Purpose |
| --- | --- |
| **Set-Cookie** | Instructs the client to store data (e.g., session tokens, preferences). |
| **Cache-Control** | Defines how long the response can be cached before re-fetching. |
| **Content-Type** | Tells the client what type of data is being returned (HTML, JSON, image, etc.). |
| **Content-Encoding** | Specifies compression used on the response (gzip, br, etc.). |

👉 **Quick takeaway:**

- **Request headers** = “Here’s who I am and what I want.”
- **Response headers** = “Here’s what I’m giving you and how to handle it.”

### Cookies

### 🔑 What Are Cookies?

- Small pieces of data stored on your computer by a web server.
- Sent via the **`Set-Cookie`** header in a server response.
- Automatically included in future requests back to the same server.
- Solve the problem of HTTP being **stateless** by remembering who you are.

### 📌 Common Uses

- **Authentication** → Keep users logged in with session tokens.
- **Personalization** → Store user preferences (e.g., theme, language).
- **Tracking/Analytics** → Remember visits, behavior, or shopping cart items.

> Note: Cookies usually store tokens, not raw credentials like passwords.
> 

### 🔍 Viewing Cookies in Browser

1. Open **Developer Tools**.
2. Go to the **Network** tab.
3. Select a request → check the **Cookies** tab.
    - Shows cookies sent by your browser.
    - Shows cookies set by the server in the response.

👉 **Quick takeaway:**

- **Server → Client:** `Set-Cookie` header stores data.
- **Client → Server:** Cookie data is sent back with each request.
- **Purpose:** Maintain state, identity, and preferences across sessions.
