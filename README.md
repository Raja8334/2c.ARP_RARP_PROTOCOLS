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
### CLIENT:
```import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
 ip=c.recv(1024).decode()
 if not ip:
     break
 try:
   c.send(address[ip].encode())
 except KeyError:
   c.send("Not Found".encode())
 c.close()
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
### CLIENT :
![Screenshot 2024-03-08 143400](https://github.com/Raja8334/2c.ARP_RARP_PROTOCOLS/assets/120719634/db3419fe-e6a3-484d-ba39-a1b28cbe30d7)
### SERVER :
![Screenshot 2024-03-08 143422](https://github.com/Raja8334/2c.ARP_RARP_PROTOCOLS/assets/120719634/7a6900f6-7578-497e-9e9e-11cf990a48e5)

## PROGRAM - RARP
### CLIENT :
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
### SERVER :
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
### CLIENT :
![Screenshot 2024-03-08 144558](https://github.com/Raja8334/2c.ARP_RARP_PROTOCOLS/assets/120719634/b60c6a49-3936-4e28-a032-a9dcc3992ec4)
### SERVER :
![Screenshot 2024-03-08 144604](https://github.com/Raja8334/2c.ARP_RARP_PROTOCOLS/assets/120719634/2be5aee8-924b-4543-a793-8284ccc040b2)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
