# 3b_CHAT_USING_TCP_SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
## server
```
import socket
import threading

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('localhost', 8001))
s.listen(1)

print("Server waiting for connection...")
conn, addr = s.accept()
print("Client connected")

def receive():
    while True:
        try:
            msg = conn.recv(1024).decode()
            if not msg or msg.lower() == "exit":
                print("Client disconnected")
                break
            print("\nClient:", msg)
        except:
            break

threading.Thread(target=receive, daemon=True).start()

while True:
    msg = input("Server: ")
    conn.send(msg.encode())
    if msg.lower() == "exit":
        break

conn.close()
s.close()
```
## client
```

import socket
import threading

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('localhost', 8001))

print("Connected to server")

def receive():
    while True:
        try:
            msg = s.recv(1024).decode()
            if not msg or msg.lower() == "exit":
                print("\nServer disconnected")
                break
            print("\nServer:", msg)
        except:
            break

threading.Thread(target=receive, daemon=True).start()

while True:
    msg = input("Client: ")
    s.send(msg.encode())
    if msg.lower() == "exit":
        break

s.close()
```
## OUPUT
# server

<img width="373" height="245" alt="image" src="https://github.com/user-attachments/assets/2a40e6a8-d1dc-441e-9ad7-5b11f8aa44ea" />

# client

<img width="355" height="137" alt="image" src="https://github.com/user-attachments/assets/14bb3697-6664-4f81-8fdc-327a9c9cf60b" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
