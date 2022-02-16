# /auth

## POST /

관리자 비번을 인증하고, 성공시 관리자 세션을 제공해주는 jwt토큰을 제공합니다.

- request

```json
{
  "password": ".env ADMIN_PASSWORD"
}
```

- response

```json
{
  "success" : true// or false
  "token": "some jwt token"
}

```
