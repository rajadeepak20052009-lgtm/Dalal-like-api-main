# Free Fire Like API

Flask-based API for sending likes and automatically refreshing JWT tokens every 8 hours.

## Features

- Like API endpoint
- API Key protection
- Automatic JWT generation
- Automatic token refresh every 8 hours
- Supports IND, BD, BR servers
- Rotating token batches
- Random token batches
- Profile checking before and after likes

---

# Installation

```bash
pip install flask requests aiohttp pycryptodome protobuf urllib3
```

---

# File Structure

```text
.
├── app.py
├── account_ind.json
├── account_bd.json
├── account_br.json
├── token_ind.json
├── token_bd.json
├── token_br.json
├── like_pb2.py
├── like_count_pb2.py
├── uid_generator_pb2.py
└── README.md
```

---

# Account Files

## account_ind.json

```json
[
    {
        "uid": "123456789",
        "password": "password1"
    },
    {
        "uid": "987654321",
        "password": "password2"
    }
]
```

## account_bd.json

```json
[
    {
        "uid": "111111111",
        "password": "password1"
    }
]
```

## account_br.json

```json
[
    {
        "uid": "222222222",
        "password": "password2"
    }
]
```

---

# Auto Generated Token Files

## token_ind.json

```json
[
    {
        "token": "eyJhbGciOi..."
    }
]
```

## token_bd.json

```json
[
    {
        "token": "eyJhbGciOi..."
    }
]
```

## token_br.json

```json
[
    {
        "token": "eyJhbGciOi..."
    }
]
```

---

# JWT Auto Refresh

JWT tokens are automatically regenerated every 8 hours.

Source:

```text
account_ind.json → token_ind.json
account_bd.json → token_bd.json
account_br.json → token_br.json
```

JWT API:

```text
https://ff-ob54-jwt-api.vercel.app/guest_to_jwt
```

Example:

```text
https://ff-ob54-jwt-api.vercel.app/guest_to_jwt?uid=123456789&password=test123
```

---

# Start Server

```bash
python app.py
```

Server:

```text
http://0.0.0.0:1000
```

---

# Like Endpoint

```http
GET /like
```

Parameters:

| Parameter | Required |
| ---------- | ---------- |
| uid | Yes |
| server_name | Yes |
| api_key | Yes |

Example:

```text
http://localhost:1000/like?uid=123456789&server_name=IND&api_key=YOUR_API_KEY
```

---

# Random Batch Mode

```text
&random=true
```

Example:

```text
http://localhost:1000/like?uid=123456789&server_name=IND&random=true&api_key=YOUR_API_KEY
```

---

# Token Information Endpoint

```http
GET /token_info
```

Example:

```text
http://localhost:1000/token_info
```

Response:

```json
{
    "IND": {
        "regular_tokens": 500,
        "visit_tokens": 500
    },
    "BD": {
        "regular_tokens": 400,
        "visit_tokens": 400
    }
}
```

---

# API Key

Default:

```text
YOUR_API_KEY
```

Header:

```http
X-API-KEY: YOUR_API_KEY
```

Or:

```text
?api_key=YOUR_API_KEY
```

---

# Supported Servers

| Server |
|----------|
| IND |
| BD |
| BR |
| US |
| SAC |
| NA |

---

# Any Problem Contact Owner

```text
@XEROX_MODS
```

Telegram Channel:

```text
@SEXTYMODS
```