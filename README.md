# DHIRAVIYA S
# 212223040041
# 2c.SIMULATING ARP /RARP PROTOCOLS
# AIM
To write a python program for simulating ARP protocols using TCP.
# ALGORITHM:
# Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
# Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
# PROGRAM - ARP
## CLIENT PROGRAM:
```
 import socket
 s=socket.socket()
 s.bind(('localhost',8000))
 s.listen(5)
 c,addr=s.accept()
 address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
 while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
## SERVER PROGRAM:
```
 import socket
 s=socket.socket()
 s.connect(('localhost',8000))
 while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
# OUTPUT - ARP
## CLIENT OUTPUT:
![Screenshot 2024-03-11 211114](https://github.com/DHIRAVIYASUNDARAM/2c.ARP_RARP_PROTOCOLS/assets/165143880/0f3cae82-611b-4d12-944e-5e4975eb3b6c)

## SERVER OUTPUT:
![Screenshot 2024-03-11 211137](https://github.com/DHIRAVIYASUNDARAM/2c.ARP_RARP_PROTOCOLS/assets/165143880/235ed5dd-af76-473d-88a2-3e2f72a18e05)

# PROGRAM - RARP
## CLIENT PROGRAM:
```
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
```
## SERVER PROGRAM:
```
 import socket
 s=socket.socket()
 s.connect(('localhost',9000))
 while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
# OUTPUT -RARP
## CLIENT OUTPUT:
![Screenshot 2024-03-11 211215](https://github.com/DHIRAVIYASUNDARAM/2c.ARP_RARP_PROTOCOLS/assets/165143880/47cdf801-f8b6-4ebd-baa0-40e4c4aa733b)

## SERVER OUTPUT:
![Screenshot 2024-03-11 211244](https://github.com/DHIRAVIYASUNDARAM/2c.ARP_RARP_PROTOCOLS/assets/165143880/139458d5-4b85-4007-82d4-4b464134f6ac)

# RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
