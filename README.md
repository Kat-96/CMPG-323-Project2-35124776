# CMPG-323-Project2-35124776
API Development

## Register to get User autherization
### Request Body
    curl -X 'POST' \
      'https://cmpg323appservice.azurewebsites.net/api/Authenticate/register' \
      -H 'accept: */*' \
      -H 'Content-Type: application/json' \
      -d '{
      "username": "12345678",
      "email": "Kat@gmail.com",
      "password": "Kat@123"
    }'

## Response
### 
    {
      "status": "Success",
      "message": "User created successfully!"
     }
     
## User Login 
### Request Body
      curl -X 'POST' \
      'https://cmpg323appservice.azurewebsites.net/api/Authenticate/login' \
      -H 'accept: */*' \
      -H 'Content-Type: application/json' \
      -d '{
      "username": "12345678",
      "password": "Kat@123"
      }'
      
## Response
    {
    "token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U",
    "expiration": "2022-09-08T13:51:20Z"
    }
    
//COPY TOKEN 
## Authorize
  Authorization_Response.png

## GET method that retrieves all Device entries
### 
