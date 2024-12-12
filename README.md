# EX01 Developing a Simple Webserver

# Date:04/10/2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
~~~
from http.server import HTTPServer, BaseHTTPRequestHandler
content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laptop Configuration Details</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 20px;
        }
        h1 {
            color: #4CAF50;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            border: 1px solid #ddd;
        }
        th, td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>

<h1>Laptop Configuration Details</h1>

<table>
    <tr>
        <th>Attribute</th>
        <th>Value</th>
    </tr>
    <tr>
        <td>Operating System</td>
        <td>Windows 10</td>
    </tr>
    <tr>
        <td>Processor</td>
        <td>Intel(R) Core(TM) i7-8550U</td>
    </tr>
    <tr>
        <td>CPU Cores</td>
        <td>4</td>
    </tr>
    <tr>
        <td>Logical CPUs</td>
        <td>8</td>
    </tr>
    <tr>
        <td>Memory</td>
        <td>16 GB</td>
    </tr>
    <tr>
        <td>Used Memory</td>
        <td>8 GB</td>
    </tr>
    <tr>
        <td>Free Memory</td>
        <td>8 GB</td>
    </tr>
    <tr>
        <td>Disk Usage</td>
        <td>70%</td>
    </tr>
    <tr>
        <td>Battery</td>
        <td>85%</td>
    </tr>
    <tr>
        <td>System Uptime</td>
        <td>2 Days, 3 Hours</td>
    </tr>
</table>

</body>
</html>

"""
class myhandler(BaseHTTPRequestHandler):
   def do_GET(self):
       print("request received")
       self.send_response(200)
       self.send_header('content-type', 'text/html; charset=utf-8')
       self.end_headers()
       self.wfile.write(content.encode())
server_address = ('',8000)
httpd = HTTPServer(server_address,myhandler)
print("my webserver is running...")
httpd.serve_forever()
~~~
# OUTPUT:
![Screenshot (45)](https://github.com/user-attachments/assets/738f3824-55c9-4c8f-a7d0-88739e380b57)
![Screenshot (46)](https://github.com/user-attachments/assets/542323ef-8839-4922-9fb8-bea2c9a77822)

# RESULT:
The program for implementing simple webserver is executed successfully.
