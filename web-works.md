# Web Dev Fundamentals


High-level overview of the internet, or at least the parts related to software development.




## What happens when


* I type https://developer.chrome.com/home/devtools-pillar into the URL bar of a browser?


    The browser breaks down the URL into components to send a GET request to the server by:

    1. Breaking down the URL into components:
        1. https    -   protocol, make sure the request is wrapped
        2. developer.chrome.com     -     hostname, human-friendly address to the host server
        3. port     -  port not given here, use default
        4. /home/devtools-pillar      -   resource, requested from the server
        5. query string - not given here


    2. Protocols included in the address will be used to format the GET request in the ways that the server expects. 

        In our example, requests sent with HTTPS protocols will included HTTPS headers wrapped around the data to be transfered.


    3. The hostname must be resolved into the computer-friendly IP address. 

        1. This IP address will be used to find the server on the Internet. 
        2. The client device will check its own domain name services (DNS) cache to see if it can trust the latest cached mapping between hostname and IP address. If it does not have a record or has an expired record, it checks for a current record to DNS servers in the network router, ISP, then Authoritative DNS server. 
        3. Once the browser has a current IP address, it sends a GET request to the IP address for **developer.chrome.com**.


    3. Ports are sometimes included in an address. 
    
        Servers can have multiple hostnames and serve different processes through different ports. For example, an e-commerce site may serve their book store through one port, and their video services through another. 

        When a port is not explicitly given, the default per the protocol is used. For HTTPS, is default port is 443. In our example, the client will connect to **developer.chrome.com** at **port 443**.


    4. Once the browser has a current IP address, it sends a GET request to that server for the resource. 

        If the request satisfies server requirements, the server responds with headers (metadata, including things like a success status code) and HTML for the page, which may include resources (style sheets, scripts, images, etc.) that the browser must request to render the page. 
        
        The browser automatically requests those other resources as well as any additional resources that they need to fully render. Requests are sent asynchronously and reassembled as responses are received. 

        Sometimes the server responds with a redirect status code and location. At this point the browser automatically sends a GET request to that new location.

    5. If a query string is included in the URL, the client would pass that as additional information in the GET request. 
    
        These parameters can be used by the server to change what is displayed or accessed, depending oon how the server is designed. 


------


* I send a POST request instead of a GET request to a HTTP server?

    POST requests to a server create a side effect, whereas GET requests are side effect free (and tend to just return data). Side effects can include changing data on server, sending mail, charge credit card, etc.

    Arguments sent with POST requests typically sent in the body of the request. Arguments sent with GET requests are typically sent in a query string.


------


* I send a request to an API with AJAX?

    Many APIs can be used with AJAX. 
    
    Some APIs will only serve data if the request is made with a JS app from the **"same origin"** as the API. For example, a bank's API could only serve data when it is called by a site and script rendered by the bank's servers.

    Some APIs can opt-in to requests made from different origins (domain, protocol, port) using **Cross-Origin Resource Sharing (CORS)**.

    Requests to an API can contain arguments as a query string or in the body of the request as well as cookies and tokens used to  authenticate the user. APIs respond with data in a text-based format, like JSON or XML. 