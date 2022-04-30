# /comment

인증헤더 모두 필요!

## POST /{idx}

댓글을 생성합니다.  
`idx`는 각 `algorithm(피드)`의 고유 `idx`값을 의미합니다.  

### req

```json
{
  "content" : "string"
}
```

### res

```ts
"JL000" | "JL003"
```

## DELETE /{idx}

댓글을 삭제합니다.  
Admin 또는 작성자만 삭제 가능합니다.  

### req

`idx` param  
이는 `algorithm(피드)`의 고유 `idx`값을 의미합니다.

### res

```ts
"JL000" | "JL003"
```
