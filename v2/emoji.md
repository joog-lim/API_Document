# /emoji

## GET ?num=

num : 조회할 알고리즘 번호

- request
- response
    
    ```jsx
    {emoji: []}
    ```
    
    ```jsx
    {"emoji": [{"_id": "thumbsdown", "count": 1}]}
    ```

## POST /{emoji}

emoji = ["leaf"]

- 추가할 이모지

num = 추가할 게시물 넘버

- request
    
    ```json
    {
    	"num" : 1
    }
    ```
    
- response
    - 200 success
        
        headers
        
        ```json
        "Set-Cookie": "token={TOKEN}; Secure; HttpOnly; Domain=server.joog-lim.info; Path=/"
        ```
        
        ```json
        {"message": "success"}
        ```
        
    - 400 error
        
        ```json
        {"message": "Bad Request"}
        ```
        
    - 401 error
      
      ```json
      {"message": "토큰이 만료되었습니다."}
      ```
## DELETE /{emoji}

emoji = ["leaf"]

num = 추가할 게시물 넘버

- request
    
    ```json
    {
    	"num" : 1
    }
    ```
    
- response
    - 200 success
        
        headers
        
        ```json
        "Set-Cookie": "token={TOKEN}; Secure; HttpOnly; Domain=server.joog-lim.info; Path=/"
        ```
        
        ```json
        {"message": "success"}
        ```
        
    - 400 error
        
        ```json
        {"message": "Bad Request"}
        ```
        
    - 401 error
        
        ```json
        {"message": "토큰이 만료되었습니다."}
        ```
