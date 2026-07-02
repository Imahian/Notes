# Introduction to Web Applications

Foundational concepts behind how web applications work — HTTP, HTML, JavaScript, cookies, and web architecture.

## HTTP Basics

```
# Request structure
GET /index.php?id=1 HTTP/1.1
Host: target.com
User-Agent: Mozilla/5.0
Cookie: session=abc123
Accept: text/html

# Response structure
HTTP/1.1 200 OK
Content-Type: text/html
Set-Cookie: session=abc123; HttpOnly; Secure
Content-Length: 1234
```

## Important HTTP Methods

| Method | Use |
|--------|-----|
| GET | Retrieve data (params in URL) |
| POST | Send data (body) |
| PUT | Create/update resource |
| DELETE | Delete resource |
| OPTIONS | List allowed methods |
| HEAD | Same as GET but no body |
| PATCH | Partial update |

## Security-Relevant Headers

| Header | Purpose |
|--------|---------|
| `Content-Security-Policy` | Restricts script/resource sources |
| `X-Frame-Options` | Prevents clickjacking |
| `X-XSS-Protection` | Legacy XSS filter |
| `Strict-Transport-Security` | Forces HTTPS |
| `Access-Control-Allow-Origin` | CORS policy |
| `HttpOnly` cookie flag | Cookie not accessible via JS |
| `Secure` cookie flag | Cookie only over HTTPS |
| `SameSite` cookie flag | CSRF protection |

## Common Status Codes

| Code | Meaning |
|------|---------|
| 200 | OK |
| 301/302 | Redirect |
| 401 | Unauthorized (needs auth) |
| 403 | Forbidden (has auth, no access) |
| 404 | Not Found |
| 500 | Server Error |

## Frontend vs Backend

```
Frontend (runs in browser):
  HTML → structure
  CSS  → presentation
  JS   → behavior, AJAX, DOM manipulation

Backend (runs on server):
  PHP, Python, Ruby, Java, Node.js
  Databases: MySQL, PostgreSQL, MSSQL, MongoDB
  Application logic, auth, data processing
```
