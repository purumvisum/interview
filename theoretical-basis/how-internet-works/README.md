https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works
https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work

https://medium.com/@nickteixeira/anatomy-of-a-url-and-the-dns-process-1c200d306fdf

![Network](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/network.gif)

What Happens When You Type in a URL
* You enter a URL into a web browser
* The browser looks up the IP address for the domain name via DNS 
    ( Domain Name Server (DNS) matches “wsvincent.com” to an IP address.)
* The browser sends a HTTP request to the server
* The server sends back a HTTP response
* The browser begins rendering the HTML
* The browser sends requests for additional objects embedded in HTML (images, css, JavaScript) and repeats steps 3-5.
* Once the page is loaded, the browser sends further async requests as needed.


## DNS Steps

### Resources: 
* [DNS Explanation (video)](https://www.youtube.com/watch?v=72snZctFFtA)

![Url](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/url.png )

https://mail.google.com/gmail
* The browser, Operating System and the router check their memory cache for the requested URL.
* Root Name Server
* Top Level Domain (TLD) servers (COM TLD name servers)
* google name servers
* authoritative name servers
*  The authoritative name servers give the IP address associated with the resolver query (https://mail.google.com/gmail).
* The resolver then gives the IP address to the Operating System. 


After establishing TCP connection client can get a data from the server.

It gets Html page first and after loads all that in this html (styles, js, images)

![client-server](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/web-site.jpg )

