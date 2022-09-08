# CMPG-323-Project2-35124776
## API Development

### Project Documentation
In this project I will be creating a CRUD RESTful API that will connect to a database storing IoT device data. 
The API will contain at least one get, post, patch and delete method per resource.

### List all endpoints and how the user would use them.

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
### Request
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
### Response
  ![Authorization_Response](https://user-images.githubusercontent.com/90704811/189106951-42e3a336-f70e-454b-981f-cecfc9e4c770.png)


## GET all Device entries
### Request Body
        curl -X 'POST' \
      'https://cmpg323appservice.azurewebsites.net/api/Devices' \
      -H 'accept: text/plain' \
      -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U' \
      -H 'Content-Type: application/json' \
      -d '{
      "deviceId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "deviceName": "Laptop",
      "categoryId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "zoneId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "status": "string",
      "isActvie": true,
      "dateCreated": "2022-09-08T11:08:40.758Z"
    }'
    
  ## Response  
    HTTP/1.1 200 OK
    content-length: 248 
    content-type: application/json; charset=utf-8 
    date: Thu,08 Sep 2022 11:09:13 GMT 
    location: https://cmpg323appservice.azurewebsites.net/api/Devices/3fa85f64-5717-4562-b3fc-2c963f66afa6 
    server: Microsoft-IIS/10.0 
    x-powered-by: ASP.NET 

## Retrieve one Device from the database based on the ID parsed through
### Request       
       curl -X 'GET' \
      'https://cmpg323appservice.azurewebsites.net/api/Devices/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
      -H 'accept: text/plain' \
      -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U'

## Response
     HTTP/1.1 200 OK
     content-encoding: gzip 
     content-length: 261 
     content-type: application/json; charset=utf-8 
     date: Thu,08 Sep 2022 11:27:47 GMT 
     server: Microsoft-IIS/10.0 
     vary: Accept-Encoding 
     x-powered-by: ASP.NET
     
## Create a new Device entry

## update an existing Device entry
### Request 
    curl -X 'PUT' \
      'https://cmpg323appservice.azurewebsites.net/api/Devices/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
      -H 'accept: */*' \
      -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U' \
      -H 'Content-Type: application/json' \
      -d '{
      "deviceId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "deviceName": "string",
      "categoryId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "zoneId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "status": "string",
      "isActvie": true,
      "dateCreated": "2022-09-08T11:49:28.223Z"
    }'
## Response 
       HTTP/1.1 204 OK
       date: Thu,08 Sep 2022 11:49:36 GMT 
       server: Microsoft-IIS/10.0 
       x-powered-by: ASP.NET 
       
## Delete an existing Device entry

### Request
        curl -X 'DELETE' \
          'https://cmpg323appservice.azurewebsites.net/api/Devices/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
          -H 'accept: text/plain' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U'
          
## Response
         HTTP/1.1 200 OK
         content-encoding: gzip 
         content-length: 256 
         content-type: application/json; charset=utf-8 
         date: Thu,08 Sep 2022 11:53:50 GMT 
         server: Microsoft-IIS/10.0 
         vary: Accept-Encoding 
         x-powered-by: ASP.NET 
         
 ## Create a new Zone entry
 ### Request
        curl -X 'POST' \
          'https://cmpg323appservice.azurewebsites.net/api/Zones' \
          -H 'accept: text/plain' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U' \
          -H 'Content-Type: application/json' \
          -d '{
          "zoneId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
          "zoneName": "Zone",
          "zoneDescription": "string",
          "dateCreated": "2022-09-08T12:19:52.935Z"
        }
 ### Response
         HTTP/1.1 201 OK
         content-length: 135 
         content-type: application/json; charset=utf-8 
         date: Thu,08 Sep 2022 12:35:03 GMT 
         location: https://cmpg323appservice.azurewebsites.net/api/Zones/3fa85f64-5717-4562-b3fc-2c963f66afa6 
         server: Microsoft-IIS/10.0 
         x-powered-by: ASP.NET 
 
## Retrieve all Zone entries 
#### Request
        curl -X 'GET' \
          'https://cmpg323appservice.azurewebsites.net/api/Zones' \
          -H 'accept: text/plain' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U'

### Response
         HTTP/1.1 200 OK
         content-encoding: gzip 
         content-length: 239 
         content-type: application/json; charset=utf-8 
         date: Thu,08 Sep 2022 12:38:47 GMT 
         server: Microsoft-IIS/10.0 
         vary: Accept-Encoding 
         x-powered-by: ASP.NET
 

## Retrieve one Zone from the database based on the ID parsed through
### Request 
        curl -X 'GET' \
          'https://cmpg323appservice.azurewebsites.net/api/Zones/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
          -H 'accept: text/plain' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U'
          
 ### Response
         HTTP/1.1 200 OK
         content-encoding: gzip 
         content-length: 236 
         content-type: application/json; charset=utf-8 
         date: Thu,08 Sep 2022 12:41:59 GMT 
         server: Microsoft-IIS/10.0 
         vary: Accept-Encoding 
         x-powered-by: ASP.NET 
         
## Delete an existing Zone entry on the database
### Request
        curl -X 'DELETE' \
          'https://cmpg323appservice.azurewebsites.net/api/Zones/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
          -H 'accept: text/plain' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U'
          
### Response
         HTTP/1.1 200 OK
         content-encoding: gzip 
         content-length: 236 
         content-type: application/json; charset=utf-8 
         date: Thu,08 Sep 2022 12:44:25 GMT 
         server: Microsoft-IIS/10.0 
         vary: Accept-Encoding 
         x-powered-by: ASP.NET 
 
## Update an existing Zone entry

### Request
        curl -X 'PUT' \
          'https://cmpg323appservice.azurewebsites.net/api/Zones/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
          -H 'accept: */*' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNDU2NzgiLCJqdGkiOiJlYWM0YWZhNS05MzQ2LTQ5ZTctODA0MC1kZjVlOTYxNmIyOGEiLCJleHAiOjE2NjI2NDUwODAsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.NYABV1eF-hKCI2759VTD4kUpQdYf81m4arfCaD__k9U' \
          -H 'Content-Type: application/json' \
          -d '{
          "zoneId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
          "zoneName": "Zone1",
          "zoneDescription": "string",
          "dateCreated": "2022-09-08T12:47:56.270Z"
        }'
        
 ### Response
         HTTP/1.1 404 Not Found
         content-length: 133 
         content-type: application/problem+json; charset=utf-8 
         date: Thu,08 Sep 2022 12:48:20 GMT 
         server: Microsoft-IIS/10.0 
         x-powered-by: ASP.NET
         
         {
          "type": "https://tools.ietf.org/html/rfc7231#section-6.5.4",
          "title": "Not Found",
          "status": 404,
          "traceId": "|6c453d9b-468c03403118269e."
        }

## Create a new Category entry

## Retrieves all Category entries
### Request
        curl -X 'GET' \
          'https://cmpg323appservice.azurewebsites.net/api/Categories' \
          -H 'accept: text/plain' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNTY3ODkiLCJqdGkiOiI3NTA1NzI1OC0wZjg2LTQwNjAtYmUwMi03ZjgxMGY0NGY0ZDYiLCJleHAiOjE2NjI2NTQwOTcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.2hQApxBBAa1JcK35FVHTtNuiH_WADFlDgqwatG_ltEw'

 ### Response
         HTTP/1.1 200 OK
         content-encoding: gzip 
         content-length: 241 
         content-type: application/json; charset=utf-8 
         date: Thu,08 Sep 2022 13:26:04 GMT 
         server: Microsoft-IIS/10.0 
         vary: Accept-Encoding 
         x-powered-by: ASP.NET 
  
  
## Retrieve one Category from the database based on the ID parsed through
### Request
        curl -X 'GET' \
          'https://cmpg323appservice.azurewebsites.net/api/Categories/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
          -H 'accept: text/plain' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNTY3ODkiLCJqdGkiOiI3NTA1NzI1OC0wZjg2LTQwNjAtYmUwMi03ZjgxMGY0NGY0ZDYiLCJleHAiOjE2NjI2NTQwOTcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.2hQApxBBAa1JcK35FVHTtNuiH_WADFlDgqwatG_ltEw'
          
 ### Response
         HTTP/1.1 200 OK
         content-encoding: gzip 
         content-length: 238 
         content-type: application/json; charset=utf-8 
         date: Thu,08 Sep 2022 13:28:28 GMT 
         server: Microsoft-IIS/10.0 
         vary: Accept-Encoding 
         x-powered-by: ASP.NET 
         
## Update an existing Category
### Request
        curl -X 'PUT' \
          'https://cmpg323appservice.azurewebsites.net/api/Categories/3fa85f64-5717-4562-b3fc-2c963f66afa6' \
          -H 'accept: */*' \
          -H 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJodHRwOi8vc2NoZW1hcy54bWxzb2FwLm9yZy93cy8yMDA1LzA1L2lkZW50aXR5L2NsYWltcy9uYW1lIjoiMTIzNTY3ODkiLCJqdGkiOiI3NTA1NzI1OC0wZjg2LTQwNjAtYmUwMi03ZjgxMGY0NGY0ZDYiLCJleHAiOjE2NjI2NTQwOTcsImlzcyI6Imh0dHA6Ly9sb2NhbGhvc3Q6NjE5NTUiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjQyMDAifQ.2hQApxBBAa1JcK35FVHTtNuiH_WADFlDgqwatG_ltEw' \
          -H 'Content-Type: application/json' \
          -d '{
          "categoryId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
          "categoryName": "Tv",
          "categoryDescription": "telecommunication medium for transmitting moving images and sound",
          "dateCreated": "2022-09-08T13:31:33.384Z"
        }'
   
### Response
         HTTP/1.1 204
         date: Thu,08 Sep 2022 13:32:57 GMT 
         server: Microsoft-IIS/10.0 
         x-powered-by: ASP.NET 
