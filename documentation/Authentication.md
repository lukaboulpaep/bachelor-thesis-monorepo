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

#### References

¹ [OAuth vs JWT and how to use them together](https://frontegg.com/blog/oauth-vs-jwt)
