# 2c.SIMULATING ARP /RARP PROTOCOLS

# NAME: BLESSING S
# REG NO:212224230039

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
P
## PROGRAM - ARP
```
CLIENT.PY
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"192.168.56.1":"14:F6:D8:DA:C9:24","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
 SERVER.PY
 import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
<img width="968" height="243" alt="Screenshot 2025-09-12 125037" src="https://github.com/user-attachments/assets/8b663284-9d64-45b1-bbcf-3bca2ae21379" />

## PROGRAM - RARP
```
CLIENT.PY
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
SERVER.PY
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
<img width="917" height="321" alt="Screenshot 2025-09-12 125046" src="https://github.com/user-attachments/assets/af47d8cb-c258-467e-b02f-e35b342e3664" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
