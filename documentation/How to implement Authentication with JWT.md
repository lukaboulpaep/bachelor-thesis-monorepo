# How to implement Authentication with JWT

There's a package in Golang named golang-jwt which enables us to generate JWT's. The package has a `New` method which and takes the cryptographic algorithm for the JWT and returns a JWT token.

```go
token := jwt.New(jwt.SigningMethodEdDSA)
```

When you want to modify the JWT, you can use the `Claims` method. This enables us to add personal information of the user.

```go
claims := token.Claims.(jwt.MapClaims)
claims["exp"] = time.Now().Add(10 * time.Minute)
claims["authorized"] = true
claims["user"] = "username"
```

In this case, you’re setting an expiry time for the JWT, which is ten minutes, using the time module and the username and authorization status. You’ll be able to retrieve the claims when attempting to verify the JWT.

The final part of generating a JWT is to sign the string using your secret key. You can sign your token string using the `SignedString` method of the token. The `SignedString` method takes the secret key and returns a signed token string.

```go
tokenString, err := token.SignedString(sampleSecretKey)
if err != nil {
    return "", err
}

return tokenString, nil
```

**How to implement this logic on the API Gateway?**

By having a `POST` route to `/register` you can register yourself for the first time. This will generate the JWT and send it back to the user.

**Verifying JWT tokens**

#### References

¹ [A guide to JWT authentication in Go](https://blog.logrocket.com/jwt-authentication-go/)
