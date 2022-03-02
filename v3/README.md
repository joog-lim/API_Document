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

[POST /]()  
[GET /count]()  
[GET /rule]()  
[GET /rule/web]()  
[GET /list/{type}/admin]()  
[GET /list/{type}]()  
[DELETE /{id}]()  
[PATCH /{id}]()  
[PATCH /{id}/status]()  

### /leaf
[POST /]()  
[DELETE /]()  


### MISC
[GET /verify]()  
[POST /login]()  
[POST /token]()  
[POST /apple/login]()  
[POST /authentication/number]()  
[POST /authentication/mail]()  

### only developer
[POST /verify]()  
