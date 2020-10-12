# JWT (Json Web Tokens)

- JWT - Authorization value token

## 3 Parts of JWT

### JWT Header:

- This tells what algorithm used to verify JWT signature
- contains - algorithm and typ

### JWT Payload:

- User identifier (unique to user)

### JWT Signature:

- This does not used to encrypt/decrypt
- it just validates the jwt header + payload for integrity
- secret keys stored at server side

## Flow

-\> \[User - Authenticates Using Creds\]  
-\> \[Server - Generates unique JWT for that authenticated user and signs that JWT with server's private key and sends back to User\]  
-\> \[User - stores this JWT in local storage/cookie\]  
-\> \[User - sends HTTP Header "Authorization: Bearer JWT" with each request\]  
-\> \[Server - verifies if the JWT supplied by user is blacklisted by searching in server cache if not move next step else deny access\]  
-\> \[Server - creates signature of base64 encode of "JWT Header + JWT Payload" using server's private key \]
-\> \[Server - compares newly created signature with signature with JWT\]  
-\> \[Server - If both signatures are matched User is allowed else denied\]

## Keys
- JWT is created and signed by issuer's private key
- JWT signature is validated by anyone using issuer's public key

## Best Practices

- Never store sensitive info in JWT
- JWT should used with oAuth
    - To avoid stealing of JWT
- JWT should sent over https
- include "issued at" timestamp in payload to terminate all other JWTs

## How to log off JWT

- Blacklisting of JWT at server side
