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
server.py:
```
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)
print("Waiting for client connection...")
c, addr = s.accept()
print("Connected to:", addr)
while True:
    msg = c.recv(1024).decode()
    if msg.lower() == "exit":
        print("Client disconnected.")
        break
    print("Client :", msg)
    reply = input("Server : ")
    c.send(reply.encode())
    if reply.lower() == "exit":
        break
c.close()
s.close()
```
client.py:
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))
print("Connected to the server.")
while True:
    msg = input("Client : ")
    s.send(msg.encode())
    if msg.lower() == "exit":
        break
    reply = s.recv(1024).decode()
    if reply.lower() == "exit":
        print("Server ended the chat.")
        break
    print("Server :", reply)
s.close()
```
## OUTPUT:

[Screenshot 2026-08-05 095250.pdf](https://github.com/user-attachments/files/31166997/Screenshot.2026-08-05.095250.pdf)
<img width="1353" height="936" alt="Screenshot 2026-08-05 095250" src="https://github.com/user-attachments/assets/2f30b2f0-568c-44db-9615-0ff7cc0f88a7" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
