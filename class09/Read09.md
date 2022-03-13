# The HTTP Request Lifecycle

1. Local Processing

 the browser need optional port number, resource path, and query strings<b>localhost:3000/client?query=param<b>


2. Resolve an IP

>The Domain Name System (DNS) is the phonebook of the Internet. When users type domain names such as ‘google.com’ or ‘nytimes.com’ into web browsers, DNS is responsible for finding the correct IP address for those sites

> the User Datagram Protocol is one of the core members of the Internet protocol suite. With UDP, computer applications can send messages, in this case referred to as datagrams, to other hosts on an Internet Protocol network.

* Your request of IP will reach many network devices to reach its target DNS server then device uses a routing table to determine which other device it is connected to that is most likely situated along the shortest path
*  Once the request arrives at server it will look for the address with the requested hostname then it will sends a response

3.  Establish a TCP Connection

>The Transmission Control Protocol (TCP) is one of the main protocols of the Internet protocol suite. TCP is connection-oriented, and a connection between client and server is established before data can be sent

* so now we have IP but we need open the TCP which is like transport layer protocol

   4. Send an HTTP Request
   1. initialize request line 
   * request header :made up of pairs in the form `name:value <CR><LF>`
   * HOST mandatory field in an HTTP request which contains the domain and port that the request is being sent to `(domain.com:8080)`
   2. Once the server receives the request, processes it, and finds the resource being requested, it generates an HTTP response. An HTTP response has a similar structure to an HTTP request, containing a "status line", response header fields, and an optional body


   # Do a Simple HTTP Request in Java

   using the built-in Java class <b>HttpUrlConnection<b> which  allows us to perform basic HTTP requests without the use of any additional libraries ,it's part of <b>java.net package.<b>
 
    1. creating request
   ```
   URL url = new URL("http://example.com");
   HttpURLConnection con = (HttpURLConnection) url.openConnection();
   con.setRequestMethod("GET");
   ```
    2. Adding Request Parameter

   ```
   Map<String, String> parameters = new HashMap<>();
   parameters.put("param1", "val");
   
   con.setDoOutput(true);
   DataOutputStream out = new DataOutputStream(con.      getOutputStream());
   out.writeBytes(ParameterStringBuilder.getParamsString      (parameters));
   out.flush();
   out.close();
   ```

   3. Setting Request Headers
       
    * by using the setRequestProperty() method
   > con.setRequestProperty("Content-Type", "application/json");
   To read the value of a header from a connection, we can use the getHeaderField() method:

   > String contentType = con.getHeaderField("Content-Type");

   4. Configuring Timeouts
    
    * it's values define the interval of time to wait for the connection to the server to be established or data to be available for reading.

   >con.setConnectTimeout(5000);
     con.setReadTimeout(5000);

   5. Handling Cookies
   >The java.net package contains classes such as CookieManager and HttpCookie

   ```
   what is cookies?
   HTTP cookies are used to identify specific users and improve your web browsing experience.

   Data stored in a cookie is created by the server upon your    connection. This data is labeled with an ID unique to you    and your computer.
   ```

   ```
   String cookiesHeader = con.getHeaderField("Set-Cookie");
   List<HttpCookie> cookies = HttpCookie.parse(cookiesHeader);
   ```

   check if cookie called username
   ```
    Optional<HttpCookie> usernameCookie = cookies.stream()
    .findAny().filter(cookie -> cookie.getName().equals("username"));
    if (usernameCookie == null) {
    cookieManager.getCookieStore().add(null, new HttpCookie("username", "john"));
     }
    ```
     add the cookies to the request
    ```
    con.disconnect();
    con = (HttpURLConnection) url.openConnection();

    con.setRequestProperty("Cookie", 
    StringUtils.join(cookieManager.getCookieStore().getCookies(), ";"));
    ``

    hen handle the redirects,reading the responseand building the full response

    link of steps](https://www.baeldung.com/java-http-request)
    