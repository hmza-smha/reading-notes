# HTTP cookies

[reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)

### An HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to a user's web browser. The browser may store the cookie and send it back to the same server with later requests. Typically, an HTTP cookie is used to tell if two requests come from the same browser—keeping a user logged in,

## Cookies are mainly used for three purposes:

### Session management
Logins, shopping carts, game scores, or anything else the server should remember

### Personalization
User preferences, themes, and other settings

### Tracking
Recording and analyzing user behavior


Cookies were once used for general client-side storage. While this made sense when they were the only way to store data on the client, modern storage APIs are now recommended. Cookies are sent with every request, so they can worsen performance (especially for mobile data connections). Modern APIs for client storage are the Web Storage API (localStorage and sessionStorage) and IndexedDB.

## Creating cookies
After receiving an HTTP request, a server can send one or more Set-Cookie headers with the response. The browser usually stores the cookie and sends it with requests made to the same server inside a Cookie HTTP header. You can specify an expiration date or time period after which the cookie shouldn't be sent. You can also set additional restrictions to a specific domain and path to limit where the cookie is sent. 

### The ```Set-Cookie``` and ```Cookie``` headers
The Set-Cookie HTTP response header sends cookies from the server to the user agent. A simple cookie is set like this:

The Set-Cookie HTTP response header sends cookies from the server to the user agent. A simple cookie is set like this:

```Set-Cookie: <cookie-name>=<cookie-value>```

This instructs the server sending headers to tell the client to store a pair of cookies:

```
HTTP/2.0 200 OK
Content-Type: text/html
Set-Cookie: yummy_cookie=choco
Set-Cookie: tasty_cookie=strawberry

[page content]
```

Then, with every subsequent request to the server, the browser sends all previously stored cookies back to the server using the Cookie header.

```
GET /sample_page.html HTTP/2.0
Host: www.example.org
Cookie: yummy_cookie=choco; tasty_cookie=strawberry
```

