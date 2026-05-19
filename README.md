# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP
## 1.server.py
```import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server waiting for connection...")
c, addr = s.accept()
print("Connected with", addr)
address = {"165.165.80.80": "6A:08:AA:C2","165.165.79.1": "8A:BC:E3:FA"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## 2.client.py
```5
import socket
s = socket.socket()
s.connect(('127.0.0.1', 8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```
## OUPUT - ARP
<img width="1482" height="808" alt="Screenshot 2026-05-19 133025" src="https://github.com/user-attachments/assets/bd85fb0a-da2c-41ad-acb8-25d500b6ed68" />

## PROGRAM - RARP
## 1.rarpserver.py
```
import socket
s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)
print("RARP Server waiting for connection...")
c, addr = s.accept()
print("Connected with", addr)
address = {"6A:08:AA:C2": "192.168.1.100","8A:BC:E3:FA": "192.168.1.101"}
while True:
       ip = c.recv(1024).decode()
       try:
          c.send(address[ip].encode())
       except KeyError:
           c.send("Not Found".encode())
```
## 2.client.py
```
import socket
s = socket.socket()
s.connect(('localhost', 9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address:", s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1511" height="750" alt="image" src="https://github.com/user-attachments/assets/c229273c-e2e2-4057-bfdf-8013ca6eda76" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
