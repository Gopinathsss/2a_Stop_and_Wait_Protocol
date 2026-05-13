# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
import socket

# Create TCP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind IP address and port number
host = "127.0.0.1"
port = 8000

server_socket.bind((host, port))

# Start listening
server_socket.listen(1)

print("Waiting for client connection...")

# Accept client connection
client_socket, address = server_socket.accept()

print("Client connected from:", address)

while True:

    # Send message to client
    server_msg = input("Server: ")
    client_socket.send(server_msg.encode())

    # Check exit condition
    if server_msg.lower() == "exit":
        print("Server closed the chat.")
        break

    # Receive message from client
    client_msg = client_socket.recv(1024).decode()

    print("Client:", client_msg)

    # Check client exit
    if client_msg.lower() == "exit":
        print("Client closed the chat.")
        break

# Close sockets
client_socket.close()
server_socket.close()

```
## PROGRAM
```
import socket

# Create client socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
host = "127.0.0.1"
port = 8000

client_socket.connect((host, port))

# Number of frames to send
frames = int(input("Enter number of frames: "))

for i in range(frames):

    # Read frame data
    data = input(f"Enter frame {i+1}: ")

    # Send frame to server
    client_socket.send(data.encode())

    # Receive acknowledgement
    ack = client_socket.recv(1024).decode()

    print("Acknowledgement from server:", ack)

# Close connection
client_socket.close()
```
## OUTPUT
<img width="1358" height="767" alt="image" src="https://github.com/user-attachments/assets/d25df232-1d9e-48d5-b510-26a9d97a2604" />
<img width="1365" height="767" alt="image" src="https://github.com/user-attachments/assets/7a5f60ed-7829-4668-a7aa-86716fcf5427" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
