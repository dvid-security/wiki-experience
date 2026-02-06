# Curl

`curl` is a versatile command-line tool that allows you to transfer data across networks using various protocols, such as HTTP, HTTPS, FTP, SFTP, and more. It’s widely used by developers, sysadmins, and network engineers for tasks such as testing APIs, downloading files, and debugging network issues.

## Main usages

1. Transfer Data Over the Network: `curl` can download or upload files, fetch web pages, and perform network-related operations.
2. API Testing: You can use `curl` to interact with RESTful APIs by sending requests (GET, POST, PUT, DELETE, etc.) and receiving raw responses.
3. Automating Requests: It’s commonly used in scripts to automate repetitive tasks like monitoring web services or downloading files.
4. Debugging Network Issues: `curl` provides detailed output about server responses (e.g., HTTP headers, status codes), helping to troubleshoot connectivity or server-side problems.
5. Customizing HTTP Requests: You can send custom headers, manipulate cookies, include authentication, and much more.

## Command line examples

This section will present some basic `curl` usages.

### Retrieve a webpage or download a file

```bash
curl https://example.com
```

This fetches the content of the webpage https://example.com and displays it in the terminal. To save it to a file:

```bash
curl -o page.html https://example.com
```

### Get a webpage from a server using port 8000:

`curl` also permits to specify the port used by the web server:

```bash
curl http://www.example.com:8000/
```

### Perform an HTTP GET request

Fetch data from an API using a GET request:

```bash
curl -X GET https://api.example.com/items
```

### Send two fields with two field names

This permits to specify multipart data in the request body:

```bash
curl -F "docpicture=@dog.gif" -F "catpicture=@cat.gif" https://api.example.com/
```

### Perform an HTTP POST request with JSON Data

This command will send data to an API:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"name":"John","age":30}' https://api.example.com/users
```

### Download a file with authentication

To download a file from a server that requires a username and password:

```bash
curl -u username:password https://example.com/file.zip -O
```

Or, if an API requires a Bearer Token for authentication:

```bash
curl -H "Authorization: Bearer YOUR_TOKEN" https://api.example.com/data
```

### Display HTTP headers only

To view only the HTTP response headers:

```bash
curl -I https://example.com
```

### Upload a file via a POST request

You can upload a file to a server:

```bash
curl -X POST -F "file=@myfile.txt" https://example.com/upload
```

### Verbose Mode for Debugging

Enable verbose output to see details about the request and response:

```bash
curl -v https://example.com
```

## Useful options

This section presents some useful `curl` options:

```
-o <filename>: Save the output to a file with a custom name.
-O: Save the output using the original filename from the server.
-H <header>: Add a custom HTTP header.
-X <method>: Specify the HTTP method (e.g., GET, POST).
-d <data>: Send data in the request body (e.g., JSON for POST requests).
-F: Send data as multipart/form-data (useful for file uploads).
-u <user:pass>: Provide username and password for authentication.
-k: Ignore SSL/TLS certificate errors.
--limit-rate: Limit the transfer speed.
```