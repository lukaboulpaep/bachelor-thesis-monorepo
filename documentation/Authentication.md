# Authentication

### Why do you need Authentication in an API Gateway?

With authentication you can identify who's making requests to your API Gateway, because of that you can implement some other features that are handy or even required. When you know who is sending requests you can set a limit to that person so they don't make too much requests which prevents cyber attacks.

When the server automatically blocks the request when the user is over their limit, it won't effect the server's load so you won't be affected by DoS attacks, which prevents your server from craching which prevents the single point of failure.

With authentication also comes authorization, you can easily set up authorization when you have authentication. When you don't want certain users to reach a service or only want them to read instead of write to a database.

### How would I implement this?

**What is OAuth?**

Open Authorization (OAuth) is an open standard for token-based authentication over public networks.
OAuth allows third-party services such as Facebook and Google to use end-user account information without exposing the user’s account credentials to a third party.
It acts as an intermediary on behalf of end users, providing access tokens to third-party services authorized to share certain account information. The process of obtaining a token is called the authorization flow. [¹]

**What is JWT**

JSON Web Tokens (JWT) are an open industry standard for sharing information between two entities, typically a client (the front end of an application) and a server (the back end of an application).
A JWT contains a JSON object with information that needs to be shared. Additionally, each JWT is cryptographically signed, so that clients or malicious parties cannot modify JSON content (also known as JWT claims).[¹]

**My decision between the two**

For the scope of this project I think that OAuth might be a bit too complex to set up as this is just a proof of concept and not a real implementation. I will be using JWT's as it also prevents me querying data to a database. The use of JWT also makes the authentication process a little bit quicker as it eliminates the need for a database.
Also JWT's are more suitable to API's as OAuth is more suitable for the web, and I don't plan to make a web interface (although that might be an extra at the end).

**A JSON Web Token can be broken down into three parts** [²]

- Header
- Payload
- Signature

At the end the token will look like this: `xxxxx.yyyyy.zzzzz`

**Header**
The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

For example:

```JSON
{
  "alg": "HS256",
  "typ": "JWT"
}
```

**Payload**

The second part of the token is the payload, which contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims.

- **Registered claims**: These are a set of predefined claims which are not mandatory but recommended, to provide a set of useful, interoperable claims. Some of them are: **iss** (issuer), **exp** (expiration time), **sub** (subject), **aud** (audience), and others.

  `Notice that the claim names are only three characters long as JWT is meant to be compact.`

- **Public claims**: These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.

- **Private claims**: These are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.

```JSON
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```

**Signature**
To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

For example if you want to use the HMAC SHA256 algorithm, the signature will be created in the following way:

```JS
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

The output is three Base64-URL strings separated by dots that can be easily passed in HTML and HTTP environments, while being more compact when compared to XML-based standards such as SAML.

The following shows a JWT that has the previous header and payload encoded, and it is signed with a secret.

```JS
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

#### References

¹ [OAuth vs JWT and how to use them together](https://frontegg.com/blog/oauth-vs-jwt)
² [JWT Introduction](https://jwt.io/introduction)
