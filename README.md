# CMPG-323-Project2-35124776
API Development

## Register to get autherization
### 
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
     
## GET method that retrieves all Device entries
### 
