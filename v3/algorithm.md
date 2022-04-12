# /algorithm

1. [POST /](#post-)
2. [GET /count](#get-count)
3. [GET /rule](#get-rule)
4. [GET /rule/web](#get-ruleweb)
5. [GET /list/{type}](#get-listtype)
6. [GET /list/{type}/admin](#get-listtypeadmin)
7. [DELETE /{id}](#delete-id)
8. [PATCH /{id}](#patch-id)
9. [PATCH /{id}/status](#patch-idstatus)

## POST /

피드를 생성합니다.
만약 로그인이 되어있다면 `verify` 요소가 필요하지않습니다.

### req

```json
{
  "title": "타이틀입니다",
  "content": "내용입니다.",
  "tag": "태그입니다.",
  "verify": { "id": "e092fce6-4982-4c1d-a5eb-b94b289b733a", "answer": "#softmeister01" }
}
```

### res

> base response

> JL003

> JL011

## GET /count

게시물 갯수 조회
값이 없는 타입은 안나타날 수도 있음

### res

```json
[
 { status: 'PENDING', count: '11' }
 { status: 'ACCEPTED', count: '11' }
 { status: 'REJECTED', count: '11' }
 { status: 'REPORTED', count: '11' }
]
```

## GET /rule

join rule
### res

```json
{
    "content" : "규칙 복붙",
    "bold13" : ["폰트15 1", "폰트 15 2", ...],
    "bold15" : ["폰트18 1", "폰트 18 2", ...]
}
```

## GET /rule/web

join rule of web

### res

```json
[
  {
    _id: 1,
    title: "제 1조 목적",
    content:
    "본 규칙은 광주소프트웨어마이스터고등학교 대나무숲 규칙으로, 대나무숲의 투명한 운영 및 익명성 보장을 목적으로 한다.",
  },
  {
    _id: 2,
    title: "제 2조 게시글 게시에 관한 규칙",
    content: "",
    subContent: [
      {
      _id: 1,
      title: "제 1항",
      content:
      "다음과 같은 게시물의 경우 반려 처리가 되거나, 삭제가 될 수 있다.",
      subContent: [
      {
        _id: 1,
        title: "1호",
        content: "다른 사용자에게 불편함을 줄 수 있는 경우",
        subContent: [
        {
  .
  .
  .
```

## GET /list/{type}
## GET /list/{type}/admin
## DELETE /{id}
## PATCH /{id}
## PATCH /{id}/status
