# API v1

게시물의 상태는 다음과 같이 네가지로 나뉩니다.

```ts
| "PENDING"
| "ACCEPTED"
| "REJECTED"
| "DELETED"
```

기본적인 경로는 다음과 같습니다.
https://server.joog-lim.info/**api**

데이터 직렬화는 json으로 통일합니다.

헤더에 `Auth`가 들어갈 경우 관리자 토큰이 필요합니다.
하지만 `continue`가 `true`일 경우, 관리자 토큰이 없어도 됩니다.

관리자 세션은 `Authorization header`에 넣어주시면 됩니다.

# route

## /post

**GET** [/get-list](./post.md#get-get-list-auth-continue--true) (Auth, continue : true)  
**POST** [/create](./post.md#post-create)  
**DELETE** [delete/{id}](./post.md#delete-deleteid-auth-continuetrue) (Auth, continue : false)  
**PATCH** [/patch/{id}](./post.md#patch-patchid) (Auth, continue : false)

## /auth

**POST** [/](./auth.md#post-)

## /verify

**GET** [/](./verify.md#get-)
