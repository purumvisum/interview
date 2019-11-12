# How the Internet works

Resources: 
* [How_the_Web_works(Video mdn)](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works)
* [How_does_the_Internet_work (Video mdn)](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work)
* [Url and DNS](
https://medium.com/@nickteixeira/anatomy-of-a-url-and-the-dns-process-1c200d306fdf)

1. The browser goes to the [DNS server](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/README.md#dns), and finds the real address of the server using IP address.
2. The browser sends an HTTP request message to the server, asking it to send a copy of the website to the client.
    This message, and all other data sent between the client and the server, 
    is sent across your internet connection using TCP/IP. [More detailed video](https://www.youtube.com/watch?v=F27PLin3TV0&feature=emb_logo)
3. If the server approves the client's request, the [server sends the client](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/README.md#Server-send-data) a "200 OK" message and then starts sending the      website's files to the browser as a series of small chunks called data packets
4. The browser assembles the small chunks into a complete website and [displays](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/README.md#Browser-render-page)  it to you


## DNS

### Resources: 
* [DNS Explanation (video)](https://www.youtube.com/watch?v=72snZctFFtA)

![Network](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/network.gif)


![Url](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/url.png )

https://mail.google.com/gmail
* The browser, Operating System and the router check their memory cache for the requested URL.
* Root Name Server
* Top Level Domain (TLD) servers (COM TLD name servers)
* Google name servers
* Authoritative name servers
* The authoritative name servers give the IP address associated with the resolver query (https://mail.google.com/gmail).
* The resolver then gives the IP address to the Operating System. 

## Server send data

![client-server](https://github.com/purumvisum/interview/blob/master/theoretical-basis/how-internet-works/web-site.jpg )

## Browser render page

Resources: 
* [how the browser renders html css](https://medium.com/@mustafa.abdelmogoud/how-the-browser-renders-html-css-27920d8ccaa6)

1. *DOM Tree*: The browser creates the Document Object Model. It is a tree of objects. Each node represents an HTML tag.
2. *CSSOM Tree*: Stands for CSS Object Model. It is basically a “map” of the CSS style which you can find on a web page. It is like the DOM but for CSS rules.
3. *Render Tree*:It is a tree that contains just the visible elements on the screen. The CSSOM and the DOM trees are combined into a render tree.
4. *Layout*: Once the browser finds out which rules apply to which elements, it will start calculating how much space it takes up and where is it on the screen.
5. *Paint*: Painting is the process of filling pixel by pixel on the screen. The drawing is typically done onto multiple surfaces called layers.
6. *Composite*: In this step, the browser combines all the layers together.

#### Examples
Change the width of an element:  layout -> paint -> compose
Changed the color of the element: paint -> compose
Change the transform of an element: compose

