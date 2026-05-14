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
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
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
## OUPUT - ARP
<img width="1370" height="930" alt="image" src="https://github.com/user-attachments/assets/d9ba94c0-145f-41fc-aab7-1a109f48defe" />
<img width="1336" height="984" alt="image" src="https://github.com/user-attachments/assets/6e949180-a798-4a20-96fc-d90ffae21180" />


## PROGRAM - RARP
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    mac=input("Enter Physical Address : ")
    s.send(mac.encode())
    print("MAC Address",s.recv(1024).decode())
```
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"FC:6D:77:6D:AA:7E":" 169.254.65.147","10:94:BB:EB:44:34":"169:254:201:22"};
while True:
    mac=c.recv(1024).decode()
    try:
       c.send(address[mac].encode())
    except KeyError:
       c.send("Not Found".encode())
```
## OUPUT -RARP
<img width="1373" height="963" alt="image" src="https://github.com/user-attachments/assets/620433fa-3121-4b77-a9bf-a61473cc8677" />
<img width="1358" height="941" alt="image" src="https://github.com/user-attachments/assets/a1143456-7f15-4253-bc97-48eceaf7c764" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
