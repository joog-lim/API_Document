# /account

## POST /login
- request
Authorization에 토큰값 담아야됨

```json
{}

```

- response
    - 200 success
        
        ```json
        { token : "token"}
        ```
        
    - 401 error
        
        ```json
        { message : "값이 뭔가 이상합니다." }
        ```
        
        
        
## POST /logout

- request
    
    Authorization 헤더에 토큰 넣어주세요~
    
- response
    - 200 success
        
        ```json
        {}
        ```
        
    - 401 not Authorizations
        
        ```json
        {"message": "권한이 없습니다."}
        ```
