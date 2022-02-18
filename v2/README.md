# API version 2

게시물의 상태는 다음과 같이 네가지로 나뉩니다.

```tsx
| "PENDING"
| "ACCEPTED"
| "REJECTED"
| "DELETED"
```

기본적인 경로는 다음과 같습니다.
https://server.joog-lim.info/**apiV2**

데이터 직렬화는 json으로 통일합니다.

헤더에 `Auth`가 들어갈 경우 관리자 토큰이 필요합니다.
하지만 `continue`가 `true`일 경우, 관리자 토큰이 없어도 됩니다.

관리자 세션은 `Authorization header`에 넣어주시면 됩니다

```diff
+ /count, 기존 알고리즘 갯수들을 카운팅하는 기능추가
+ /rule, 룰 페이지에 나오는 룰 값들을 리턴해주는 기능추가

- /get-list 삭제
+ 대신 /AlgorithmList, /AlgorithmPage 추가

- /patch/{id}의 역할 분할
+ /{id}/setStatus, /{id}/modify, /{id}/report

+ login 및 logout 추가
+ emoji 추가
```
## /post

[GET /count]()

[GET /rule]()

[GET /AlgorithemList (Auth, continue : true)]()

[GET /AlgorithemPage]()

[POST /create]()

[POST /{id}/setStatus]()

[PATCH /{id}/modify]()

[PATCH /{id}/report]()

[DELETE /{id}/delete]()

## /auth

[POST ]()

## /verify

[GET ]()

## /account

[POST /login]()

[POST /logout]()

## /emoji

[GET /]()

두개 다 Authorization에 토큰 넣어주세용~

[POST /{emoji}]()

[DELETE /{emoji}]()
