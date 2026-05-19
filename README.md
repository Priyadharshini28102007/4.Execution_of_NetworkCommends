# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Program
# server
```
import socket

# Create socket
server_socket = socket.socket()

# Reuse address
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# Host and port
host = "localhost"
port = 12345

# Bind socket
server_socket.bind((host, port))

# Listen for client
server_socket.listen(1)

print("Server waiting for connection...")

# Accept connection
conn, addr = server_socket.accept()

print("Connected from:", addr)

# Receive message
message = conn.recv(1024).decode()

print("Client Message:", message)

# File to send
filename = "test.txt"

try:
    with open(filename, "rb") as f:

        data = f.read(1024)

        while data:
            conn.send(data)
            data = f.read(1024)

    print("File sent successfully")

except FileNotFoundError:
    print("test.txt file not found")

# Close connection
conn.close()
server_socket.close()

print("Connection closed")
```
# client
```
client.py

import socket

# Create socket
client_socket = socket.socket()

# Host and port
host = "localhost"
port = 12345

# Connect to server
client_socket.connect((host, port))

# Send message
client_socket.send("Hello Server!".encode())

# Receive file
with open("received_file.txt", "wb") as f:

    while True:

        data = client_socket.recv(1024)

        if not data:
            break

        f.write(data)

print("File received successfully")

# Close socket
client_socket.close()

print("Connection closed")
```
## Output
<img width="1175" height="240" alt="Screenshot 2026-05-19 153100" src="https://github.com/user-attachments/assets/b730bc14-ad45-4824-bef9-9b8d79d1526a" />
<img width="1219" height="195" alt="Screenshot 2026-05-19 153132" src="https://github.com/user-attachments/assets/60df853e-e976-488e-a468-d97375e6d9ec" />

## Result
Thus Execution of Network commands Performed 
