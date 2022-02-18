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

## /post

[GET /count](https://www.notion.so/GET-count-cce8a77a997e4659ad6d762e727cbd49)

[GET /rule](https://www.notion.so/GET-rule-90b72389903240c4a164623819a307f4)

[GET /AlgorithemList (Auth, continue : true)](https://www.notion.so/GET-AlgorithemList-Auth-continue-true-19bee6b6feaa41f498bd49af1599dab0)

[GET /AlgorithemPage](https://www.notion.so/GET-AlgorithemPage-b961ad2c677b4dbfbe8441ff52d34a85)

[POST /create](https://www.notion.so/POST-create-4208b8b4b2fc4a57ac7a5a81cf4ebefa)

[POST /{id}/setStatus](https://www.notion.so/POST-id-setStatus-8b7f75c6848c4a0c9d9fe4a4c649c109)

[PATCH /{id}/modify](https://www.notion.so/PATCH-id-modify-4840b98ff1024b3183bdaf41cdbf1457)

[PATCH /{id}/report](https://www.notion.so/PATCH-id-report-a66e228505044f4bba96d15f46525308)

[DELETE /{id}/delete](https://www.notion.so/DELETE-id-delete-cecd00b717cb45949f44488a84c5893d)

## /auth

[POST ](https://www.notion.so/POST-4753af691be1455f9c8c12c879cea709)

## /verify

[GET ](https://www.notion.so/GET-62a997cdbf824e378821c68aad39c1fe)

## /account

---

[POST /login](https://www.notion.so/POST-login-6456534045a24f58842fa8c0ceddfa3f)

[POST /logout](https://www.notion.so/POST-logout-1488be18da734d9fb8d1a055a1bfc8c1)

## /emoji

[GET /](https://www.notion.so/GET-88d9add039834821942bbf88ddc12d7f)

두개 다 Authorization에 토큰 넣어주세용~

[POST /{emoji}](https://www.notion.so/POST-emoji-929b52057b6c4687a449f6f4aff3a980)

[DELETE /{emoji}](https://www.notion.so/DELETE-emoji-bd3bb230335748059134d0ec2beefdbc)
