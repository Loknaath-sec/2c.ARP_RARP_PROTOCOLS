# Exp No-2c.SIMULATING ARP /RARP PROTOCOLS
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
### CLIENT
```python
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
### SERVER
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter Logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```



## OUPUT - ARP
### CLIENT
![image](https://github.com/Loknaath-sec/2c.ARP_RARP_PROTOCOLS/assets/145742558/cd947ea7-a012-4057-8ef4-b462dbc7a41a)
### SERVER
![image](https://github.com/Loknaath-sec/2c.ARP_RARP_PROTOCOLS/assets/145742558/1a437c7a-929b-4232-af3b-eb51dd9e9a91)



## PROGRAM - RARP
### CLIENT
```python
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
```
### SERVER
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
### CLIENT
![image](https://github.com/Loknaath-sec/2c.ARP_RARP_PROTOCOLS/assets/145742558/240d1ca8-188a-4826-b6eb-97a27cefaf9d)

### SERVER
![image](https://github.com/Loknaath-sec/2c.ARP_RARP_PROTOCOLS/assets/145742558/0399c1f0-f6ce-4d37-a2d7-a5b631fcd4a5)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
