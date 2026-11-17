# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
1.Server 
```
import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = '127.0.0.1'
port = 5000
server_socket.bind((host, port))
server_socket.listen(1)
print("Waiting for client connection...")
client_socket, addr = server_socket.accept()
print("Connected to:", addr)
while True:
    client_message = client_socket.recv(1024).decode()
    print("Client:", client_message)
    if client_message.lower() == "bye":
        break
    message = input("Server: ")
    client_socket.send(message.encode())
    if message.lower() == "bye":
        break
client_socket.close()
server_socket.close()
```
2.Client
```
import socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = '127.0.0.1'
port = 5000
client_socket.connect((host, port))
print("Connected to server")
while True:
    message = input("Client: ")
    client_socket.send(message.encode())
    if message.lower() == "bye":
        break
    server_message = client_socket.recv(1024).decode()
    print("Server:", server_message)
    if server_message.lower() == "bye":
        break
client_socket.close()
```
## OUTPUT
1.Server
<img width="1312" height="832" alt="image" src="https://github.com/user-attachments/assets/27e7c5d9-51ae-49cc-bf5f-76d27acec074" />

2.Client
<img width="1362" height="803" alt="image" src="https://github.com/user-attachments/assets/72ab150a-31ab-47fc-8826-71040bd0c4fe" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
