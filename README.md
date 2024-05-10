# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
Name : SANTHIYA S

Register Number : 212223220098
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
### Client Side
```python
import socket
s=socket.socket()
s.bind(('localhost',80))
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
### Server Side
```python
import socket
s=socket.socket()
s.connect(('localhost',80))
while True:
   ip=input("Enter logical Address : ")
   s.send(ip.encode())
   print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
![Screenshot (52)](https://github.com/ADARSH778/2c.ARP_RARP_PROTOCOLS/assets/149347361/a70d70d9-f596-4f54-8f1a-0b741630e509)

## PROGRAM - RARP
### Client Side
```python
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
### Server Side
```python
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
![Screenshot (53)](https://github.com/ADARSH778/2c.ARP_RARP_PROTOCOLS/assets/149347361/1cc3d213-3fde-4055-9a82-87ca9e5a061c)

## RESULT
Thus, the python program for simulating ARP RARP protocols using TCP was successfully 
executed.
