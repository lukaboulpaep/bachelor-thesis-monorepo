# What is an API Gateway?

An API Gateway is an API management tool that sits between the client and a collection of microservices, it's primary function is to serve as a single point of entry. It acts as a very fancy reverse proxy, because it also handles authentication and authorization, rate limiting, monitoring and tracing, service discovery. [¹], [²]

> In computer networks, a reverse proxy is an application that sits in front of back-end applications and forwards client (e.g. browser) requests to those applications. [³]

### What are the advantages of using an API Gateway?

It serves as a protection layer against overuse and abuse and that's where the authentication and rate limiting comes in to place.
Most of the times an API gateway is also used to understand how people use your API's and it's used for analytics and that's where the monitoring comes in to place.
The microservice architectures forces us to send out multiple calls to multiple services, with an API gateway you've got to send out one single request.

An API Gateway is an easy way to manage all of your microservices and it makes it easier for the client to use your API. You also don't have to re-authenticate users for each service as a client will be authenticated when it goes through the gateway, your services can just accept that, by example, John Doe is a user that can access certain data.

**Some popular implementations of API Gateways**

Kong Enterprise is considerd the fastest, most feature-advanced, and secure API management solution built on Kong Gateway. [Kong API Gateway](https://konghq.com/products/kong-gateway)

Envoy Gateway is an open source project for managing Envoy Proxy as a standalone or Kubernetes-based application gateway. [Envoy Gateway](https://github.com/envoyproxy/gateway)

Envoy might be an intersting one to look at as it is open-source and written in Golang which is going to be my programming language of choice.

### Scope of my project

As building a fully featured API Gateway such as Kong or Envoy is too big for a little project like this I will be focussing on small but essential parts of an API Gateway.

Authentication will be very import to enable rate limiting also, this helps me prevent cyber attacks which would also prevent the single point of failure that comes with an API Gateway.

Service discovery also seems like an essential feature for an API Gateway to work really nice.

Lastly the basic functionality to redirect an api call to the right microservices.

### Why won't I use the API Gateway from certain cloud providers?

- **Cost**: Using a cloud provider's fully-featured API Gateway can be expensive, especially if you have a high volume of API traffic. By building your own API Gateway, you can save on costs and optimize your infrastructure for your specific needs.

- **Learning**: Building your own API Gateway is a great way to learn how API Gateway technology works and gain a deeper understanding of microservices architecture. By building it yourself, you can gain hands-on experience and a deeper appreciation for the complexity of building a scalable, secure, and reliable API Gateway.

- **Customization**: Building your own API Gateway allows you to customize the functionality and features to meet the specific needs of your application or organization.

#### References

¹ [What are API Gateways?](https://www.redhat.com/en/topics/api/what-does-an-api-gateway-do#:~:text=An%20API%20gateway%20is,return%20the%20appropriate%20result.)
² [API Gateway functionalities](https://www.solo.io/topics/api-gateway/api-gateway-security/#:~:text=The%20primary%20function%20of%20an%20API%20gateway%20is%20to%20serve%20as%20the%20single%20entry%20point%20for%20all%20data%2C%20applications%2C%20and%20services)
³ [What's a reverse proxy](<https://en.wikipedia.org/wiki/Reverse_proxy#:~:text=In%20computer%20networks%2C%20a%20reverse%20proxy%20is%20an%20application%20that%20sits%20in%20front%20of%20back%2Dend%20applications%20and%20forwards%20client%20(e.g.%20browser)%20requests%20to%20those%20applications.>)
