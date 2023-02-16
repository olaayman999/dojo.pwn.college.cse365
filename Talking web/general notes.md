internet = network of networks = collection of distributed systems

TCP/IP => layers over layers of abstraction

[HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

[How HTTP Tunneling works, The CONNECT method, Pros & Cons and more](https://www.youtube.com/watch?v=PAJ5kK50qp8)

![image](https://user-images.githubusercontent.com/72671239/219287557-e47c3c2a-bdc3-4238-9154-5f1cfa4bdff8.png)
![image](https://user-images.githubusercontent.com/72671239/219288250-e8e6e5c8-788d-43b8-9c60-5fecca651c54.png)
![image](https://user-images.githubusercontent.com/72671239/219288932-7e9bbe11-4627-442b-8759-e6f9a12999e6.png)

TLS (Transport Layer Security) is a cryptographic protocol that provides secure communication over the internet. It is the successor to SSL (Secure Sockets Layer) and is used to secure connections between web browsers and web servers, as well as other types of client-server connections.

When a client (such as a web browser) connects to a server over TLS, the following happens:

1. The client initiates a connection request to the server.

2. The server responds by sending its SSL/TLS certificate to the client.

3. The client verifies the authenticity of the certificate and negotiates a set of encryption parameters with the server.

4. The client and server exchange encrypted messages using the agreed-upon encryption parameters.

TLS provides several security benefits, including confidentiality, integrity, and authenticity. Confidentiality means that the data being transmitted is encrypted and can only be decrypted by the intended recipient. Integrity means that the data cannot be modified during transmission without detection. Authenticity means that the client can be sure that it is communicating with the intended server, and not with an impostor.

Here's a brief overview of the TLS handshake process:

1. ClientHello: The client sends a message to the server with a list of supported cipher suites, TLS version, and other information.

2. ServerHello: The server responds to the client with a message that contains the chosen cipher suite, TLS version, and other information.

3. Server Certificate: The server sends its digital certificate, which contains the server's public key and other information that allows the client to verify the server's identity.

4. Client Key Exchange: The client sends a message that contains the symmetric key to be used for encrypting and decrypting data.

5. Server Key Exchange (Optional): If the server needs to send the client additional information, such as a Diffie-Hellman public key or a pre-shared secret, it sends a Server Key Exchange message.

6. Certificate Request (Optional): If the server requires the client to authenticate itself, it sends a Certificate Request message.

7. Server Hello Done: The server sends a message indicating that the server has completed its part of the handshake.

8. Client Certificate (Optional): If the server requested a client certificate, the client sends its digital certificate to the server.

9. Client Key Exchange: The client sends another message that contains additional key material, such as a pre-master secret.

10. Certificate Verify (Optional): If the client has sent a digital certificate, it sends a message that contains a cryptographic signature of the handshake messages to prove the authenticity of the certificate.

11. Finished: Both the client and server send a message containing a cryptographic hash of all the handshake messages exchanged so far. This verifies that both parties have successfully completed the handshake and have agreed on a shared secret key.

Once the TLS handshake process is complete, the client and server can securely exchange data using the agreed-upon encryption parameters.

![image](https://user-images.githubusercontent.com/72671239/219291725-acb31832-3a25-450f-bf1c-4290dc9021a1.png)
![image](https://user-images.githubusercontent.com/72671239/219291749-37baa22a-7803-443a-a8dc-4c6eb0ede946.png)

[CONNECT http](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/CONNECT)

[TRACE http](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/TRACE)

## url encoding

![image](https://user-images.githubusercontent.com/72671239/219319986-680cdcac-248f-4ee7-838a-8c8a17d018ee.png)

## state

HTTP/1.0 does support cookies. The first version of cookies was introduced in 1994, which is before the release of HTTP/1.0 in 1996. Cookies are a mechanism for storing information in the form of key-value pairs on the client side and transmitting it between the server and client in subsequent requests. They are commonly used for session management, user authentication, and tracking user behavior.

In HTTP/1.0, the `Set-Cookie` header is used by the server to set a cookie, and the `Cookie` header is used by the client to send the cookie back to the server in subsequent requests. However, HTTP/1.0 cookies have some limitations, such as the inability to specify a path or domain for the cookie, which were later addressed in HTTP/1.1.


