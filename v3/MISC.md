# /

## GET /verify
인증 질문 조회  

### res 

```json
{
  "id": "e092fce6-4982-4c1d-a5eb-b94b289b733a",
  "question": "GSM 와이파이 비번"
}
```

## POST /token
토큰 리프레쉬, 1주일 남은 리프레쉬토큰도 리프레쉬해드림


### req

```
Authorization : RefreshToken
```

### res

```json
{
  "accessToken" : "token",
  "refreshToken": "token",
  "isAdmin" : false
}
```

## POST /authentication/mail

메일 인증을 위한 메일 발송


### req

```json
{
  "type" : "signup | changepw"
  "email" : "s20048@gsm.hs.kr"
}
```

`type`의 `signup`의 경우 회원가입시를 이야기하며, `changepw`의 경우 비밀번호 교체 시 인증을 의미한다.  

### res

```ts
"JL003" | "JL019" | "JL007" | "JL000"
```

## PATCH /authentication/mail

메일 인증을 위한 인증번호 입력

### req

```json
{
  "email" : "s20048@gsm.hs.kr",
  "number" : "1234"
}
```

### res

```ts
"JL011" | "JL000"
```

## POST /signup

회원가입을 위한 무스비  
단, 이메일은  ` /authentication/mail`를 통해 미리 검증되어 있는 이메일만 가능하다.  

### req

```json
{
  "emali" : "s20048@gsm.hs.kr",
  "nickname" : "오병진",
  "stdGrade" : 3,
  "stdClass" : 1,
  "stdNumber" : 12,
  "pw" : "1q2w3e4r"
}
```

### res

```ts
"JL003" | "JL018" | "JL000"
```

if success:
```json
{
  "accessToken" : "asdfasdfs.asdfasdf.asdfasfd",
  "refreshToken" : "asdfasfd.asdfasdf.asdfasfd",
  "isAdmin" : false
}
```


## POST /login

로그인

### req

```json
{
  "email" : "s20048@gsm.hs.kr",
  "pw" : "asdfasdfAS"
}
```

### res

```ts
"JL003" | "JL017" | "JL000"
```

if sucess : 
```json
{
  "accessToken" : "asdfasdfs.asdfasdf.asdfasfd",
  "refreshToken" : "asdfasfd.asdfasdf.asdfasfd",
  "isAdmin" : false
}
```

## POST /password

비밀번호 찾기

아이디 찾기는 [다음 이슈](https://github.com/joog-lim/bamboo-front/issues/111)를 참고해주시길 바랍니다.

### req

```json
{
  "email" : "s20048@gsm.hs.kr",
  "number" : "123456",
  "password" "server.joog-lim.info"
}
```

### res

```ts
"JL000" | "JL007"
```
