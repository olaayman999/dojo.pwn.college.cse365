curl is a command-line tool to transfer data to or from a server, using any of the supported protocols (HTTP, FTP, IMAP, POP3, SCP, SFTP, SMTP, TFTP, TELNET, LDAP, or FILE). 
 This tool is preferred for automation since it is designed to work without user interaction. curl can transfer multiple files at once. 
 
 ## wget vs curl
 
 Both `wget` and `curl` are command-line tools that allow you to download files from the internet. Here are some of the key differences between the two:

wget is designed primarily for downloading files from the web, It can follow links on a web page and download entire websites recursively. By contrast, curl is a more general-purpose tool that supports a wider range of protocols, including HTTP, FTP, SMTP, and more.

wget is a non-interactive tool, meaning it can be used in scripts or automated processes. It can run in the background without requiring user input. curl is more interactive and can display progress indicators and other information while it is running.

curl has more advanced features for sending and receiving data over a network. It can send custom HTTP headers, handle cookies, and perform more advanced authentication schemes. wget is more limited in these areas.

Overall, if you just need to download a file from the web, either tool can work, but wget is often the more straightforward option. If you need to perform more complex operations, such as interacting with a web API, curl may be the better choice.

[Linux Essentials: Curl Fundamentals](https://www.youtube.com/watch?v=Xy7fDxz39FM)

fetch the HTML content only and print it in terminal

```bash
curl https://hsploit.com
```
fetch entire HTML and include the http response header

```bash
curl -i https://example.com
```
if you want to specify a different name for the downloaded file, you should use the `-o` or `--output` option instead.

fetch HTML of a webpage and save it in a .html file, note that it is very important to specify the protocol that you are using "https"

```bash
 curl -o ./example.html https://example.com 
```
The `-O` option is a shortcut for `--remote-name`, and it is used with curl to download a file from a URL and save it with the same name as the remote file.

You should use the `-O` option when you want to download a file from the internet and save it with the same name as the remote file.

```bash
curl -O https://example.com/file.zip
```

used the `-L` to follow the redirection and `-i` to view the http response headers

```bash
curl -Li https://hsploit.com
```

![image](https://user-images.githubusercontent.com/72671239/219545613-b6d39bc6-a6ec-42ea-9b6a-ff9e8372304f.png)


the `-I` option return only the http response headers while `-i ` return both http headers and body
```bash
curl -LI https://hsploit.com
```

the `-v` option is for verbose output, it provide details about the TLS handshake and TCP handshake and more connection data

```bash
 curl -LIv https://hsploit.com
```
![image](https://user-images.githubusercontent.com/72671239/219552653-a8ea07bd-d60b-4754-b98f-0e9eb9ff2b11.png)

---------------------------------------

## does curl use all http versions

Yes, curl supports all versions of the HTTP protocol, including HTTP/1.0, HTTP/1.1, and HTTP/2.

By default, curl uses the latest version of the HTTP protocol that is supported by both the server and the client. However, you can also specify the version of the HTTP protocol to use with the `--http1.0`,` --http1.1`, or `--http2` options.

For example, to use HTTP/1.0, you can use the following command:
```bash
curl --http1.0 https://example.com
```

To use HTTP/1.1, you can use the following command:
```bash
curl --http1.1 https://example.com
```

To use HTTP/2, you can use the following command:
```bash
curl --http2 https://example.com
```

If you don't specify a version of the HTTP protocol, curl will use the latest version that is supported by the server and the client.

## does curl support http 3

Yes, curl supports HTTP/3, the latest version of the HTTP protocol that is designed to improve the speed and efficiency of web communication. HTTP/3 uses the QUIC transport protocol, which is built on top of the User Datagram Protocol (UDP) instead of the Transmission Control Protocol (TCP) used by HTTP/1 and HTTP/2.

To use curl with HTTP/3, you need to make sure that you have a version of curl that is compiled with support for the nghttp3 library, which provides the implementation of the HTTP/3 protocol. You can check whether your curl installation supports HTTP/3 by running the following command:
```bash
curl --http3 -I https://example.com
```
If your curl installation supports HTTP/3, you should see a response that includes the HTTP/3 protocol version in the Server header:

```bash
HTTP/3 200 OK
...
Server: cloudflare
```
Note that HTTP/3 is still an experimental protocol and not yet widely supported by all web servers and clients. You may need to enable experimental features or use specific servers or configurations to test HTTP/3 with curl.

## how does curl know the version of http of the remote server if i didn't specify

When you use curl to make an HTTP request, it sends an initial request line to the remote server that includes the HTTP version that it supports. For example, if curl is configured to use HTTP/1.1, the initial request line might look like this:

```bash
GET /index.html HTTP/1.1
```
This request line specifies that curl is using HTTP/1.1 to make the request.

The remote server then responds to the request with its own HTTP version in the status line of the response. For example, the status line for an HTTP/1.1 response might look like this:

```bash
HTTP/1.1 200 OK
```
This status line indicates that the remote server is using `HTTP/1.1` to send the response.

Based on the HTTP version that it receives in the response status line, curl will continue to use that version for any subsequent requests or responses to that server. If the server supports multiple versions of HTTP, curl will negotiate with the server to use the highest version that both the client and server support.

Therefore, if you don't explicitly specify an HTTP version with curl, it will determine the appropriate version to use based on the response it receives from the remote server.

## can a server block the use of curl

It is possible for a server to block the use of curl or any other user agent that it does not recognize. Some websites or web applications may be configured to only allow requests from certain user agents, such as web browsers, and block requests from other user agents like curl.

A server can determine the user agent of the client making the request by inspecting the `User-Agent`  request header that is sent with the request. curl sends a default `User-Agent` header with its requests, which identifies itself as `curl/{version}`. Some servers may choose to block requests from this user agent or other non-standard user agents as a security measure to prevent automated attacks or scraping of their content.

However, in most cases, it is possible to modify the `User-Agent` header sent by curl using the `-H` or `--header option`. For example, you can use the following command to set a custom `User-Agent` header:

```bash
curl -H 'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36' https://example.com
```
In this example, curl sets the `User-Agent`header to a string that mimics the user agent of the Google Chrome web browser.
