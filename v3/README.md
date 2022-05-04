# API version 3

게시물의 상태는 다음과 같이 네가지로 나뉩니다.

```tsx
| "PENDING"
| "ACCEPTED"
| "REJECTED"
| "REPORTED"
```

기본적인 경로는 다음과 같습니다.
https://server.joog-lim.info/apiV3

데이터 직렬화는 json으로 통일합니다.

다음 res에 해당하는 값들은 `data` 에 들어가게됩니다.
`default response value` 는 다음과 같습니다.

```json
{
	"success":true,
	"code":"JL000",
	"message":"요청이 성공적으로 이루어졌습니다.",
	"data":...
}
```

## 변경사항

```diff
+ 어드민 로그인을 유저로그인과 통일, isAdmin 값을 통해 구분함
+ 토큰을 jwt를 이용해 관리하며 액세스토큰과 리프레쉬토큰을 사용하는 방식으로 변경
+ 몇 몇 인자값의 네이밍에 변경사항이 생김
+ 에러코드가 생겼으며 이는 다음에서 확인 가능함
https://github.com/joog-lim/API_Document/blob/main/error_code.md
```

## API List

### /algorithm

[POST /](./algorithm.md#post-)  
[GET /count](./algorithm.md#get-count)  
[GET /rule](./algorithm.md#get-rule)  
[GET /rule/web](./algorithm.md#get-ruleweb)  
[GET /list/{type}/admin](./algorithm.md#get-listtypeadmin)  
[GET /list/{type}](./algorithm.md#get-listtype)  
[DELETE /{id}](./algorithm.md#delete-id)  
[PATCH /{id}](./algorithm.md#patch-id)  
[PATCH /{id}/status](./algorithm.md#patch-idstatus)

### /leaf

[POST /]()  
[DELETE /]()

## /comment

[POST /{idx}](./comment.md#post-idx)
[DELETE /{idx}](./comment.md#delete-idx)

## /profile

[PATCH /](./profile.md#patch)

### MISC

[GET /verify](./MISC.md#get-verify)  
[POST /token](./MISC.md#post-token)  
[POST /authentication/mail](./MISC.md#post-authenticationmail)  
[PATCH /authentication/mail](./MISC.md#patch-authenticationmail)
[POST /signup](./MISC.md#post-signup)  
[POST /login](./MISC.md#post-login)

---

API v3.1

```diff
- DELETE baseURL/algorithm/{id}
- PATCH baseURL/algorithm/{id}
- PATCH baseURL/algorithm/{id}/status
+ DELETE baseURL/algorithm/information/{id}
+ PATCH baseURL/algorithm/content/{id}
+ PATCH baseURL/algorithm/status/{id}
```

### /algorithm

[POST /](./algorithm.md#post-)  
[GET /count](./algorithm.md#get-count)  
[GET /rule](./algorithm.md#get-rule)  
[GET /rule/web](./algorithm.md#get-ruleweb)  
[GET /list/{type}/admin](./algorithm.md#get-listtypeadmin)  
[GET /list/{type}](./algorithm.md#get-listtype)  
[DELETE /information/{id}](./algorithm.md#delete-id)  
[PATCH /content/{id}](./algorithm.md#patch-id)  
[PATCH /status/{id}](./algorithm.md#patch-idstatus)
