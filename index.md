# TripGenius API Planning & Documentation
URL: http://trigpen-api.com/{version}/{Group}/{endpoint}

-----------
## Group: Auth

### [1] - Register
- URL: 
    - http://rooturl-api.com/v1/auth/register
- Endpoint: 
    - `/register`  
- Method: 
    - `POST`
- Request Body:
    - `name` : string, `NOT NULL`,
    - `username`: string, `NOT NULL`, Must Unique,
    - `email` : string, `Unique`
    - `hp-num`: string, Tidak harus di isi  
    - `address`: string, Tidak harus di isi  
  ```
  {
    name: "jhon doe",
    username: "username",
    email: "email@email.com",
    password: "examplepass123",
    hp-num : "08xxxxxxx",
    address: "xxxxxx"
  }
  ```  
- Response:  
  ```
  status: true,
  code: 201,
  message: "REGISTER_SUCCESS",
  ```  
- Error Response:
    - `400` : NAME_REQUIRED, EMAIL_REQUIRED, PASSWORD_REQUIRED,  
    - `409` : EMAIL_ALREADY_EXIST,
    - `500` : USER_REGISTER_FAILED
  
### [2] - Login  
- URL:
    - http://wwww.rooturl-api.com/v1/auth/login
- Endpoint:
    - `/login` 
- Method:
    - `POST`  
- Request Body: 
    - `email` : string, email need to be valid
    - `password`: string, email and password need to be match  
```
{
    email : "example@email.com",
    password: "exmaplepassword123"
}
```  
- Response:
```
{
status: true,
code: 200,
message: "LOGIN_SUCCESS",
accessToken,
refreshToken
}
```  
- Err Response:
    - `400` : INVALID_INPUT, EMAIL_REQUIRED, PASS_REQUIRED
    - `401` : USER_NOT_FOUND, EMAIL_NOT_REGISTERED, PASSWORD_INVALID  

### [3] - resreshToken [**DO NOT USE refreshToken**]
- URL:
    - http://wwww.rooturl-api.com/v1/auth/refreshToken
- Endpoint:
    - `/refreshToken`
- Method: 
    - `POST`
- Headers:  
    - `Authorization` : Bearer Access-Token
- Request Body:
    - refresh-token
```
{
refreshToken: <token>
}
```  
- Response:
```
{
status: "success",
message: "REFRESH_TOKEN_SUCCES",
newAccessToken,
newRefreshToken
}
```  
-----------  
## Group: User  
### [1] - editProfile
- URL: 
    - http://wwww.root-api.com/v1/user/:id
- Endpoint: 
    - `/user/:id`
- Method: 
    - `PUT` or `PATCH`
- Headers:  
    - `Authorization` : Bearer < Access-Token >
- Request Body:
    - `Name`, string and NULL able
    - `Username`, string and NULL able
    - `hp-num`, string and NULL able
    - `address`, string and NULL able  

```
{
Name: "example",
Username: "exampleuser",
hp-num: "08xxxxxxx",
address: "exmaple address"
}
```  
- Response:
```
{
status: true,
code: 200,
message: "USER_UPDATED",
updatedAt
}
```  
### [2] - change password
- url :
    - http://wwww.root-api.com/v1/user/:id 
- Endpoint:
    - `/user/:id`
- Method: 
    - `PUT` or `PATCH`
- Headers:  
    - `Authorization` : Bearer < Access-Token >  
- Request Body:  
    - `old-password`, string
    - `new-password`, string  
```
{
old-password: "example",
new-password: "exmaple123"
}
```  
- Response: 
```
{
status: true,
code: 201,
message: "PASSWORD_UPDATED",
updatedAt
}
```  
- Err Response:
    - `400` : PASSWORD_INVALID, PASSWORD_NOT_MATCH, PASSWORD_REQUIRED  
