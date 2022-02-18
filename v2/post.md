# /post

## GET /count

알고리즘 상태별 갯수를 가져옴  

```json
_id는 해당 게시물의 status를 뜻함

[
    {
        "_id": "REJECTED",
        "count": 17
    },
    {
        "_id": "DELETED",
        "count": 1
    },
    {
        "_id": "ACCEPTED",
        "count": 20
    },
    {
        "_id": "PENDING",
        "count": 18
    }
]
```

## GET /rule

알고리즘 규칙 값을 가져옵니다.

```json
{
    "content" : "규칙 복붙",
    "bold13" : ["폰트15 1", "폰트 15 2", ...],
    "bold15" : ["폰트18 1", "폰트 18 2", ...]
}
```

## GET /AlgorithemList (Auth, continue : true)

조건에 부합하는 알고리즘 리스트를 가져옵니다.

- request
    
    ```
    baselink/apiV2/post/AlgorithemList?count=20&cursor=60b8407473d81a1b4cc591a5&status=PENDING
    ```
    

`count`는 한번에 몇개를 가져올지를 나타냅니다.
`cursor`은 현재 어디에 위치했고, 어디 이후부터 게시물을 가져올지에 대해 나타냅니다.
`status`는 어떤 상태의 게시물을 가져올지를 나타냅니다.(관리자 세션이 없을 경우에 `ACCEPTED` 상태의 게시물만 가져올 수 있습니다.)

- response
    
    ```json
    {
        "posts": [
            {
                "id": "6125d75ec718010009ca3af7",
                "number": 4,
                "title": "제목",
                "content": "내용",
                "tag": "공부",
                "createdAt": 1629869918612,
                "status": "ACCEPTED"
            },
            {
                "id": "6123a77d36e50400093a59b7",
                "number": 3,
                "title": "rmaksgkrpTek",
                "content": "욕은 하지말도록 하게;;",
                "tag": "학교",
                "createdAt": 1629726589652,
                "status": "ACCEPTED"
            },
            {
                "id": "6123a74d36e50400093a59ab",
                "number": 2,
                "title": "534a",
                "content": "fafaf",
                "tag": "기타",
                "createdAt": 1629726541308,
                "status": "ACCEPTED"
            },
            {
                "id": "6123a73a36e50400093a59a7",
                "number": 1,
                "title": "ii",
                "content": "tlqkf",
                "tag": "유머",
                "createdAt": 1629726522318,
                "status": "ACCEPTED"
            },
            {
                "id": "61277ada5f407700095812b4",
                "number": 1,
                "title": "공부.",
                "content": "ㅎㅇ1",
                "tag": "공부",
                "createdAt": 1629977306078,
                "status": "DELETED"
            }
        ],
        "count": 56,
        "cursor": "1",
        "hasNext": false
    }
    ```
    

`posts`는 가져온 `posts` 게시물들의 리스트입니다.
`cursor`은 가져온 `posts` 게시물들 중, 가장 작은 `number`를 가진 `posts`의 `number`를 나타냅니다.
`hasNext`는 다음에 더 게시물을 가져올 수 있는지에 대한 답변입니다.

## GET /AlgorithemPage

조건에 부합하는 게시물 페이지를 가져옵니다.

- request

```
baselink/apiV2/post/AlgorithemPage?page=1&status=ACCEPTED

```

`page` 는 몇 페이지의 값을 가져올지를 나타냅니다.
`status`는 어떤 상태의 게시물을 가져올지를 나타냅니다.(관리자 세션이 없을 경우에 `ACCEPTED` 상태의 게시물만 가져올 수 있습니다.)

- response
- 200
    
    ```json
    {
        "posts": [
            {
                "id": "61369f250f124200088219cf",
                "number": 125,
                "title": "ㅎㅎ",
                "content": "ㅇㅇ",
                "tag": "일상",
                "createdAt": 1630969637040,
                "status": "ACCEPTED"
            },
            {
                "id": "613472f50a88380008a82798",
                "number": 124,
                "title": "하이",
                "content": "바이",
                "tag": "학교",
                "createdAt": 1630827253331,
                "status": "ACCEPTED"
            },
    
    				.
    				.
    				.
    
            {
                "id": "6125db2ec718010009ca3be3",
                "number": 90,
                "title": "공부.",
                "content": "뭘까12",
                "tag": "공부",
                "createdAt": 1629870894484,
                "status": "ACCEPTED"
            }
        ],
        "totalPage": 4
    }
    ```
    
    `posts`는 가져온 `posts` 게시물들의 리스트입니다.
    `totalPage` 는 총 페이지 수 입니다.
    
    - 400
    
    ```json
    {
        "success": false,
        "message": "page값은 1부터 시작합니다."
    }
    ```
    
## POST /create

알고리즘을 생성합니다. 

- request
    
    ```json
    {
      "title": "타이틀입니다.",
      "content": "내용입니다.",
      "tag": "태그입니다.",
      "verifier": { "id": "question id", "answer": "question answer" }
    }
    
    ----
    verifier는 질문 객체입니다.
    ```
    
- response
1. 200
    
    ```json
    {
      "id": "대충 해당 게시글의 id값"
    }
    
    ```
    
2. 400 BadRequest
    
    ```json
    {
        "success": false,
        "message": "필숫값이 제대로 전달되지 않았습니다."
    }
    ```
    
3. 401 Unauthorized
    
    ```json
    {
        "success": false,
        "message": "인증을 실패하였습니다."
    }
    ```
    
## POST /{id}/setStatus

`id` 는 상태를 변경시킬 게시물의 고유 아이디값입니다.

- request
    
    ```json
    {
      "status" : "REJECTED",
    	"reason"? : "대충 사유"
    	}
    ```
    
- response
    - 200
        
        ```json
        {
            "title": "test",
            "content": "asdf",
            "tag": "유머",
            "beforeStatus": "PENDING",
            "afterStatus": "REJECTED"
        }
        ```
        
    - 400
        
        ```json
        {
            "success": false,
            "message": "status값이 선언되지않았습니다.\n다시 값을 확인해주시길 바랍니다."
        }
        ```
        
        ```json
        {
            "success": false,
            "message": "status값이 부적절합니다.\nstatus값에 오타가 없는지 확인해주시길 바랍니다."
        }
        ```
    
## PATCH /{id}/modify

`id`는 알고리즘의 고유 아이디값입니다.

- request
    
    ```json
    {
    	"title" : "타이틀 입니다.",
    	"content" : "알고리즘 내용입니다.",
    	"tag" : "태그입니다."
    }
    ```
    
- response
    - 200
        
        ```json
        {
            "createdAt": 1629977314286,
            "title": "게시물 무단 수정해버리기~",
            "status": "ACCEPTED",
            "_id": "61277ae25f407700095812d8",
            "content": "무야호~",
            "tag": "정신줄 놓아버리기~",
            "number": 47,
            "updatedAt": "2021-08-27T13:53:28.087Z",
            "__v": 0,
            "reason": "",
            "cursorId": "61277ae25f407700095812d8",
            "id": "61277ae25f407700095812d8"
        }
        ```
        
    - 404
        
        ```json
        {
            "success": false,
            "message": "해당 게시물을 찾을 수 없습니다."
        }
        ```
        
## PATCH /{id}/report

`arg`는 삭제할 게시물의 고유 아이디값입니다.

- request

```json
{
  "reason": "조금 꼴받네요"
}
```

- response

```json
{
    "createdAt": 1629977314286,
    "title": "dkssud",
    "status": "DELETED",
    "_id": "61277ae25f407700095812d8",
    "content": "gktpdy",
    "tag": "공부",
    "number": 2,
    "updatedAt": "2021-08-27T05:13:29.142Z",
    "__v": 0,
    "reason": "조금 꼴받네요",
    "cursorId": "61277ae25f407700095812d8",
    "id": "61277ae25f407700095812d8"
}
```

## DELETE /{id}/delete

`arg` 는 삭제할 게시물의 고유 아이디 값입니다.

- request

```json
{
    "reason" : "배고프기때문이랄까..?."
}
```

- response

```json
{
    "createdAt": 1629977307992,
    "title": "공부.",
    "status": "ACCEPTED",
    "_id": "61277adb5f407700095812bc",
    "content": "ㅎㅇ1",
    "tag": "공부",
    "number": 36,
    "updatedAt": "2021-08-26T11:35:39.181Z",
    "__v": 0,
    "reason": "",
    "cursorId": "61277adb5f407700095812bc",
    "id": "61277adb5f407700095812bc"
}
```
