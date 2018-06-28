## Part 2: Microservices security with OAuth2

Detailed description can be found here: [Microservices security with Oauth2](https://piotrminkowski.wordpress.com/2017/12/01/part-2-microservices-security-with-oauth2/) 

1, To test without gateway£º

1.1 get access token by password grant type:

$  curl account-service:secret@localhost:9999/oauth/token -d grant_type=password -d username=piomin -d password=piot123            % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
																100   871    0   819  100    52    819     52  
1427{"access_token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1MzAxNzMyNTIsInVzZXJfbmFtZSI6InBpb21pbiIsImF1dGhvcml0aWVzIjpbIlJPTEVfQURNSU4iLCJST0xFX1VTRVIiXSwianRpIjoiY2MxYzc3N2ItYTI0ZS00ZThjLTgzZTAtMzE0NWY2ZWY2YjM2IiwiY2xpZW50X2lkIjoiYWNjb3VudC1zZXJ2aWNlIiwic2NvcGUiOlsicmVhZCJdfQ.XF4jPGYWHgFtfsd8SGnxCPJe6sNcYQVKC6PYKFRO8NY","token_type":"bearer","refresh_token":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX25hbWUiOiJwaW9taW4iLCJzY29wZSI6WyJyZWFkIl0sImF0aSI6ImNjMWM3NzdiLWEyNGUtNGU4Yy04M2UwLTMxNDVmNmVmNmIzNiIsImV4cCI6MTUzMjc0NDk0MywiYXV0aG9yaXRpZXMiOlsiUk9MRV9BRE1JTiIsIlJPTEVfVVNFUiJdLCJqdGkiOiI2NWVkZmI3Mi1hZjcyLTQ0NjYtYTlmMC03YmEyM2E3YTlhMGMiLCJjbGllbnRfaWQiOiJhY2NvdW50LXNlcnZpY2UifQ.UQfoOkbb4kMSNFON2lVj-4mAINv5qYlaMCAiw6eF11Y","expires_in":899,"scope":"read","jti":"cc1c777b-a24e-4e8c-83e0-3145f6ef6b36"}

1.2 visit account service:

$ curl http://localhost:8082/1?access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1MzAxNzMyNTIsInVzZXJfbmFtZSI6InBpb21pbiIsImF1dGhvcml0aWVzIjpbIlJPTEVfQURNSU4iLCJST0xFX1VTRVIiXSwianRpIjoiY2MxYzc3N2ItYTI0ZS00ZThjLTgzZTAtMzE0NWY2ZWY2YjM2IiwiY2xpZW50X2lkIjoiYWNjb3VudC1zZXJ2aWNlIiwic2NvcGUiOlsicmVhZCJdfQ.XF4jPGYWHgFtfsd8SGnxCPJe6sNcYQVKC6PYKFRO8NY
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
Dload  Upload   Total   Spent    Left  Speed
100    58    0    58    0     0     58      0 --:--:-- --:--:-- --:--:--   123{"id":1,"customerId":1,"number":"123456789","amount":1234}

1.3 visit customer service:

$ curl http://localhost:8083/1?access_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE1MzAxNzMyNTIsInVzZXJfbmFtZSI6InBpb21pbiIsImF1dGhvcml0aWVzIjpbIlJPTEVfQURNSU4iLCJST0xFX1VTRVIiXSwianRpIjoiY2MxYzc3N2ItYTI0ZS00ZThjLTgzZTAtMzE0NWY2ZWY2YjM2IiwiY2xpZW50X2lkIjoiYWNjb3VudC1zZXJ2aWNlIiwic2NvcGUiOlsicmVhZCJdfQ.XF4jPGYWHgFtfsd8SGnxCPJe6sNcYQVKC6PYKFRO8NY
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current Dload  Upload   Total   Spent    Left  Speed
                                 
100   228    0   228    0     0    228      0 --:--:-- --:--:-- --:--:--   860{"id":1,"name":"John Smith","age":33,"accounts":[{"id":1,"customerId":1,"number":"123456789","amount":1234},{"id":2,"customerId":1,"number":"123456780","amount":2500},{"id":3,"customerId":1,"number":"123456781","amount":10000}]}

