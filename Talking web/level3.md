```python
import ssl
import socket

hostname = "example.com"
context = ssl.create_default_context()

with socket.create_connection((hostname, 443)) as sock:
    with context.wrap_socket(sock, server_hostname=hostname) as ssock:
        print(ssock.version())
```
### AttributeError: module 'ssl' has no attribute 'PROTOCOL_TLSv1_3'

The AttributeError: module 'ssl' has no attribute 'PROTOCOL_TLSv1_3' error occurs when the version of the Python ssl module that you are using does not support the PROTOCOL_TLSv1_3 constant.

The PROTOCOL_TLSv1_3 constant was added in Python 3.7, so if you are using an earlier version of Python, you will not be able to use it.

To check if your version of Python supports TLSv1.3, you can run the following code:
```python
import ssl
print(ssl.OPENSSL_VERSION)
```
This will print the version of OpenSSL that is being used by your Python installation. If the version is lower than 1.1.1, then your Python installation does not support TLSv1.3.

If you are using an older version of Python, you can try upgrading to a newer version that supports TLSv1.3, or you can try using a different SSL/TLS library that supports TLSv1.3, such as pyOpenSSL or cryptography. These libraries provide their own TLSv1.3 constants, which you can use instead of ssl.PROTOCOL_TLSv1_3.

## Using Python to Consume APIs 

he Python requests API enables developers to write code to interact with REST APIs. It allows them to send HTTP requests using Python without having to worry about the complexities that typically come with carrying out such tasks (i.e., manually adding query strings to URLs, form-encoding PUT and POST data, etc.). 

Despite being considered the de facto standard for making HTTP requests in Python, the requests module is not part of Python’s standard library – it must be installed. 

The most straightforward way to install the requests module is with pip: 
```bash
python -m pip install requests
```
```python
import requests
# The API endpoint
url = "http://localhost"
# A GET request to the API
response = requests.get(url)
print(response.text)
```
https://www.datacamp.com/tutorial/making-http-requests-in-python
