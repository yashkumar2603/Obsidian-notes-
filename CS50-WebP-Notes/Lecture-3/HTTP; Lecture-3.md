HTTP, or HyperText Transfer Protocol, is a widely-accepted protocol for how messages are transfered back and forth across the internet. Typically, information online is passed between a client (user) and a server. ![Client and Server](https://cs50.harvard.edu/web/2020/notes/3/images/client_server.png)

In this protocol, the client will send a **request** to the server, that might look something like the one below. In the example below, `GET` is simply a type of request, one of three we’ll discuss in this course. The `/` typically indicates that we’re looking for the website’s home page, and the three dots indicate that we could be passing in more information as well. ![Request](https://cs50.harvard.edu/web/2020/notes/3/images/request.png)

After receiving a request, a server will then send back an HTTP response, which might look something like the one below. Such a response will include the HTTP version, a status code (200 means OK), a description of the content, and then some additional information. ![Response](https://cs50.harvard.edu/web/2020/notes/3/images/response.png)

200 is just one of many status codes, some of which you may have seen in the past: ![Codes](https://cs50.harvard.edu/web/2020/notes/3/images/codes.png)

