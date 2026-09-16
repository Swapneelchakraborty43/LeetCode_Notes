**JWT**
![img_27.png](images/img_27.png)

JWT was made for secure data transfer, but over the years it is used for many other purposes:


![img_28.png](images/img_28.png)

Authentication flow of JWT:
![img_29.png](images/img_29.png)

Auth server - 3rd party lib to genrrare and validate token 

- client provide username / password
- Auth server generated token and return to client
- client will call the resource server and pass JWT in the authorization  header.
- resource server will call the auth server and pass the token
- resource will grant permission and return the data.

Before JWT there was session id:
![img_30.png](images/img_30.png)

Disadvantages:
![img_31.png](images/img_31.png)

JWT Structure:

![img_32.png](images/img_32.png)

- Header
![img_33.png](images/img_33.png)

-Payload: holds claims:
Types of claims:
Registered Claims: names are reserved
![img_34.png](images/img_34.png)

Public claims: email, country. Never put 

![img_36.png](images/img_36.png)

Private claim: auth server understands. ex: IAM
![img_35.png](images/img_35.png)

Signature (JWS) Json Web Signature:

![img_37.png](images/img_37.png)

How is signature created: 
- Encode Base64 Encodinfg for header and payload and concatenate these two using . period
- create signature by using RSA or HMAC encryption
- encode signature and append to header and payload

![img_38.png](images/img_38.png)

![img_39.png](images/img_39.png)

Challenges of JWT:
![img_40.png](images/img_40.png)

 
**JWT IMPLEMENTATION**

- User Creation
- Token Generation
- Token Validation
- Refresh token

![img_41.png](images/img_41.png)








