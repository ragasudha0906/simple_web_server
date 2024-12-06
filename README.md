# EX01 Developing a Simple Webserver

# Date:
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
```
from http.server import HTTPServer,BaseHTTPRequestHandler
content="""
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laptop Configuration Details</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            background-color: #1e1e2f;
            color: #fff;
            padding: 20px;
        }

        h1 {
            text-align: center;
            margin-bottom: 40px;
            font-size: 3em;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .config-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .config-card {
            background: #2c2c3d;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .config-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 6px 30px rgba(0, 0, 0, 0.15);
        }

        .config-card h2 {
            font-size: 1.6em;
            margin-bottom: 15px;
            color: #4CAF50;
        }

        .config-card p {
            font-size: 1.2em;
            color: #ddd;
        }

        .icon {
            font-size: 3em;
            color: #4CAF50;
            margin-bottom: 20px;
            text-align: center;
        }

        /* Animations for icons */
        .icon-animated {
            animation: rotateIcon 2s infinite;
        }

        @keyframes rotateIcon {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        /* Responsive Styles */
        @media (max-width: 768px) {
            body {
                padding: 10px;
            }

            h1 {
                font-size: 2em;
            }

            .config-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>

    <h1>Laptop Configuration Details</h1>

    <div class="config-container">
        <div class="config-card">
            <div class="icon icon-animated">🖥️</div>
            <h2>Operating System</h2>
            <p>{{ config['OS'] }} {{ config['OS Version'] }}</p>
        </div>

        <div class="config-card">
            <div class="icon">⚙️</div>
            <h2>Machine</h2>
            <p>{{ config['Machine'] }}</p>
        </div>

        <div class="config-card">
            <div class="icon">💻</div>
            <h2>Processor</h2>
            <p>{{ config['Processor'] }}</p>
        </div>

        <div class="config-card">
            <div class="icon">🧠</div>
            <h2>CPU Cores</h2>
            <p>{{ config['CPU Cores'] }}</p>
        </div>

        <div class="config-card">
            <div class="icon">🧑‍💻</div>
            <h2>RAM</h2>
            <p>{{ config['RAM (GB)'] }} GB</p>
        </div>

        <div class="config-card">
            <div class="icon">💾</div>
            <h2>Disk Usage</h2>
            <p>{{ config['Disk Usage'] }}</p>
        </div>

        <div class="config-card">
            <div class="icon">🔋</div>
            <h2>Battery Status</h2>
            <p>{{ config['Battery Status'] }}</p>
        </div>
    </div>

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
print("my webserver id running....")
httpd.serve_forever()
```
# OUTPUT:
![Screenshot (25)](https://github.com/user-attachments/assets/5a1d6e0d-c039-4743-a7bd-9078f85b2031)
![Screenshot (20)](https://github.com/user-attachments/assets/ae7e0df5-36ca-4af5-a8b6-2e8840a5ec3a)

# RESULT:
The program for implementing simple webserver is executed successfully.
