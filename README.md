# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## 
server:
```
import socket

# Server details
host = '127.0.0.1'  # Localhost
port = 5001         # Port (make sure it's free)

# Create TCP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((host, port))
server_socket.listen(1)
print(f"Server listening on {host}:{port}...")

# Accept connection from client
conn, addr = server_socket.accept()
print(f"Connected by {addr}")

# File to send
filename = 'sample.txt'

try:
    with open(filename, 'rb') as file:
        data = file.read()
        conn.sendall(data)  # Send file in bytes
    print(f"File '{filename}' sent successfully.")
except FileNotFoundError:
    print(f"File '{filename}' not found!")

conn.close()
server_socket.close()
```

client:
```
import socket

# Server details
host = '127.0.0.1'
port = 5001

# Create TCP socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((host, port))

# File to save
filename = 'received_file.txt'

# Receive file data from server
with open(filename, 'wb') as file:
    while True:
        data = client_socket.recv(1024)  # Receive 1KB at a time
        if not data:
            break
        file.write(data)

print(f"File received and saved as '{filename}'.")

client_socket.close()
```
## OUPUT
<img width="1919" height="1195" alt="image" src="https://github.com/user-attachments/assets/513d0663-5d64-4f03-9cdd-80bc1ac79987" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
