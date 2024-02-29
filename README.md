# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM [ARP]:
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
## PROGRAM - ARP:
### CLIENT:
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
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
### CLIENT:
<img width="563" alt="image" src="https://github.com/Ganesh23013987/2c.ARP_RARP_PROTOCOLS/assets/147473768/18cc8a53-5d42-4747-939e-95f3e8409ac7">

### SERVER:
<img width="559" alt="image" src="https://github.com/Ganesh23013987/2c.ARP_RARP_PROTOCOLS/assets/147473768/0e41a4e9-5af8-4162-9451-ab7b88d1cabe">

## ALGORITHM [RARP]:
### Client:
1. Start the program
2. Using datagram sockets UDP function is established.
3. Get the MAC address to be converted into IP address.
4. Send this MAC address to server.
5. Server returns the IP address to client.
### Server:
1. Start the program.
2. Server maintains the table in which IP and corresponding MAC addresses are stored.
3. Read the MAC address which is send by the client.
4. Map the IP address with its MAC address and return the IP address to client.
## PROGRAM - RARP:
### CLIENT:
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
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP:
### CLIENT:
<img width="562" alt="image" src="https://github.com/Ganesh23013987/2c.ARP_RARP_PROTOCOLS/assets/147473768/d84ecae9-3b49-43d1-aedd-99ec69b3aae6">

### SERVER:
<img width="559" alt="image" src="https://github.com/Ganesh23013987/2c.ARP_RARP_PROTOCOLS/assets/147473768/ae56103e-efd9-4ed4-a3ac-a3c521bd97b8">

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
