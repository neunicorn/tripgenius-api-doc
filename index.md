# TripGenius API Planning & Documentation
URL: http://trigpen-api.com/{version}/{Group}/{endpoint}

==   
GROUP: Auth

## [1] - Register
- URL: http://tripgen-api.com/v1/auth/register
- Endpoint: `register`  
- Method: POST
- Request Body:
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
  - `name` : string, `NOT NULL`,
  - `username`: string, `NOT NULL`, Must Unique,
  - `email` : string, `Unique`
  - `hp-num`: string, Tidak harus di isi
- Response:
  ```
  message: "REGISTER_SUCCESS",
  ```
- Error Response:
  
