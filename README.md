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
P
## PROGRAM - ARP
## server.py

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())

## client.py

import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"165.165.79.1"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

## OUPUT - ARP
## server.py
<img width="570" height="190" alt="image" src="https://github.com/user-attachments/assets/759f0997-e784-4591-9190-bbe76fbd614a" />

## client.py
<img width="591" height="71" alt="image" src="https://github.com/user-attachments/assets/379476ae-8b24-449d-a7d4-3883596e5c74" />


## PROGRAM - RARP
## server.py

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())


## client.py

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("not found".encode())



## OUPUT -RARP

## server.py
<img width="577" height="147" alt="image" src="https://github.com/user-attachments/assets/1bb5f698-657b-4162-b477-d9257144352b" />


## client.py
<img width="621" height="57" alt="image" src="https://github.com/user-attachments/assets/df6bf098-74b7-4a36-8ada-2cc9bb3c61b7" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
