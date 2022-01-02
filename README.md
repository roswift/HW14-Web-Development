# HW14-Web-Development
Homework assignment for week 14 of the UCSD Cybersecurity Bootcamp

### Questions 

#### HTTP Requests and Responses

Answer the following questions about the HTTP request and response process.

1. What type of architecture does the HTTP request and response process occur in?
 * **_Client-Server Architecture, on the Application Layer of the OSI Model._**
   
2. What are the different parts of an HTTP request? 
 * **_The Request Line:_**
   * **_The first line of the HTTP request which includes the following:_**
    * HTTP method:
       * `GET`
       * `HEAD`
       * `POST`
       * `PUT`
       * `DELETE`
       * `CONNECT`
       * `OPTIONS`
     * The request URI
     * The HTTP protocol version
   
  * **_The Request Header:_**
     * **_The Request Header provides information about the nature of the request for the servers response._**
      * Sample Header Variations:
         * `Connection`
         * `Host`
         * `Upgrade`
         * `Accept`
         * `User-Agent`
         * `Authorization`
         * `Referrer`
         * `Cookie`
       
  * **_The Request Body:_**
      * Is the data sent by the client to your API. A response body is the data your API sends to the client. 

3. Which part of an HTTP request is optional?
  * **_The optional part of the HTTP Request is the Body._**
  
4. What are the three parts of an HTTP response?
  * **_The Three parts of an HTTP response are:_**
    * Status Line - Unencrypted protocol in use & status code
      * Status Codes: `100's`, `200's`, `300's`, `400's`, and `500's`
    * Header 
    * Body - Optional

5. Which number class of status codes represents errors?
  * **_`400` codes indicate client errors._**
  * **_`500` codes inidicate server errors._**

6. What are the two most common request methods that a security professional will encounter?
 * **_The two most common request methods are:_**
   * `GET`and `POST`

7. Which type of HTTP request method is used for sending data?
  * **_The HTTP Request method that is used for sending data is:_**
     * `POST`

8. Which part of an HTTP request contains the data being sent to the server?
  * **_The part of an HTTP request that contains the data being sent to the server is:_**
    * The Request Body contains the actual data being sent, which is sent using the HTTP Method `POST`
9. In which part of an HTTP response does the browser receive the web code to generate and style a web page?
  * **_The part of an HTTP response which gives the web code is:_**
    * The Response body

#### Using curl

Answer the following questions about `curl`:

10. What are the advantages of using `curl` over the browser?
* **_A few advantages of using `curl` are:_**
  * Test web server security configurations
  * Authenticating
  * Using HTTP Post
  * Ensure web servers don't leak sensitive data through their HTTP responses
  * Verify that servers only respond to certain request types
  * SSL Connections
  * Look for vulnerabilities on a web server
  * Downloading  

11. Which `curl` option is used to change the request method?
* **_`-X` or `--request` are both options to change the request method._**

12. Which `curl` option is used to set request headers?
* **_`-H` or `--header` are both options to set request headers._**

13. Which `curl` option is used to view the response header?
* **_`-i` or `--include` are both options to view the response header_**

14. Which request method might an attacker use to figure out which HTTP requests an HTTP server will accept?
* **_`GET` or `OPTIONS` are both viable options._**
  * `GET`: would allow the attacker to request information from the server and see which requests can and cannot be accepted.
  * `OPTIONS`: is best because it allows the attacker to see which communication options are availble for use.

#### Sessions and Cookies

15. Which response header sends a cookie to the client?

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```
* **_`Set-Cookie` is responsible for sending the `cookie` to `cart=Bob`._**

16. Which request header will continue the client's session?

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```
* **_`Cookie` will continue the clients session, in particular `cart=Bob`._**

#### Example HTTP Requests and Responses
**HTTP Request**

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What is the request method?
* **_`POST`_**

18. Which header expresses the client's preference for an encrypted response?
* **_`Upgrade-Insecure-Requests: 1`_**

19. Does the request have a user session associated with it?
* **_The request `DOES NOT` have a user session associated with it_**

20. What kind of data is being sent from this request body?
* **_Log in credentials were being sent in the body of this request:_**
  * `username=Barbara&password=password`

**HTTP Response**

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```

21. What is the response status code?
* **_`200`_**

22. What web server is handling this HTTP response?
* **_`Server: Apache`_**

23. Does this response have a user session associated to it?
* **_Yes - `Set-Cookie: SessionID=5`_**

24. What kind of content is likely to be in the [page content] response body?
* **_The content of the page given in the header `Content-Type: text/html; charset=UTF-8`._**

25. If your class covered security headers, what security request headers have been included?
* **_The Security Request Headers in this example are listed below:_**
  * `Strict-Transport-Security: max-age=31536000; includeSubDomains`
  * `X-Content-Type: NoSniff`
  * `X-Frame-Options: DENY`
  * `X-XSS-Protection: 1; mode=block`

#### Monoliths and Microservices

26. What are the individual components of microservices called?
* **_The individual components of a microservice are:_**
  * Front-end
  * Back-end
  * Database

27. What is a service that writes to a database and communicates to other services?
* **_Application Programming Interface (API)._**

28. What type of underlying technology allows for microservices to become scalable and have redundancy?
* **_Containers are the underlying technology that allows for microservices to become scalable, while loadbalancers allow them to have redunddancy._**

#### Deploying and Testing a Container Set

29. What tool can be used to deploy multiple containers at once?
* **_`docker-compose up` is a tool to spin up multiple containers._**
* **_`docker-compose down` is a tool to tear down multiple containers._**

30. What kind of file format is required for us to deploy a container set?
* **_`YAML`files are required to deploy a container set_**

#### Databases

31. Which type of SQL query would we use to see all of the information within a table called `customers`?
* **_SELECT statements_**
  * `SELECT * FROM customers WHERE Last_Name"insertnamehere"`

32. Which type of SQL query would we use to enter new data into a table? (You don't need a full query, just the first part of the statement.)
* **_INSERT INTO_**
  * `INSERT INTO customers (field1, field2, field3, ...) VALUES ('a', 'b', 'c', ...)`

33. Why would we never run `DELETE FROM <table-name>;` by itself?
* **_It would delete the entire table as it doesn't have the `WHERE` clause._**

---
