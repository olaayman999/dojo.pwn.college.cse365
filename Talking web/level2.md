![image](https://user-images.githubusercontent.com/72671239/219560619-aabd2ceb-4d27-45ae-9fbf-14e058e53afb.png)
![image](https://user-images.githubusercontent.com/72671239/219560844-2815615f-2484-48c4-9eb9-98eb0882bc1e.png)

To send an HTTP request using the nc (netcat) utility, you can use the following command:

```bash
echo -e "GET / HTTP/1.1\r\nHost: example.com\r\n\r\n" | nc example.com 80
```
In this command, we're using the `echo` command to send an HTTP `GET` request for the root path (`/`) to `example.com` on port `80`. The `-e` flag is used to enable interpretation of backslash escapes in the string, and we're using `\r\n` to separate the lines of the request.

The Host header is included to indicate the hostname of the server we're making the request to. This is required for HTTP/1.1 requests.

The output of the command will be the HTTP response received from the server.

`\r\n ` is a sequence of two characters that represents a line break or newline in various protocols, including HTTP.

In this sequence, the `\r` represents a "carriage return", which moves the cursor to the beginning of the line, and the `\n` represents a "line feed", which moves the cursor to the next line. **Together, they create a new line,** and are used to separate lines of text in HTTP requests and responses.




