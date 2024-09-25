# EX01 Developing a Simple Webserver
## Date: 11-09-2024

## AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
```
import platform
from http.server import HTTPServer,BaseHTTPRequestHandler

system_name = platform.system()
node_name = platform.node()
release = platform.release()
version = platform.version()
machine = platform.machine()
processor = platform.processor()

content='''
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My System Configuration</title>
</head>
<body>
    <h1>My System Configuration</h1>
    <ul>
        <li>'''+system_name+'''</li>
        <li>'''+node_name+'''</li>
        <li>'''+release+'''</li>  
        <li>'''+version+'''</li>  
        <li>'''+machine+'''</li>  
        <li>'''+processor+'''</li>  
    </ul>
</body>
</html>
'''

class MyServer(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200) 
        self.send_header("content-type", "text/html")       
        self.end_headers()
        self.wfile.write(content.encode())

print("This is my webserver") 
server_address =('',8000)
httpd = HTTPServer(server_address,MyServer)
httpd.serve_forever()
```
## OUTPUT:

![Screenshot 2024-09-25 085744](https://github.com/user-attachments/assets/c2e93673-5839-431f-abc6-7ef553f67546)
![Screenshot 2024-09-25 085800](https://github.com/user-attachments/assets/c84cd610-2815-4266-9958-965b6211f47e)


## RESULT:
The program for implementing simple webserver is executed successfully.
