# 2c.SIMULATING ARP /RARP PROTOCOLS
## Name : Iniyasri.S
## Register number : 212223230081
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
## client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}; while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
## server
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter logical address: ")
s.send(ip.encode())
print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP
## client
![image](https://github.com/iniyasri4464/2c.ARP_RARP_PROTOCOLS/assets/152419072/cd7efcf1-177c-4bec-83ec-d375258483ad)
## server
![image](https://github.com/iniyasri4464/2c.ARP_RARP_PROTOCOLS/assets/152419072/66023255-442d-4942-a124-0505ce66bb50)

## PROGRAM - RARP
## client
```
import socket
s = socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr = s.accept()
address = {"6A:08:AA:C2":"165.165.80.1","8A:BC:E3:FA":"165.165.79.1"}
while True:
ip = c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())
```
## server
```
import socket
s = socket.socket()
s.connect(('localhost',8000))
while True:
ip = input("Enter MAC address: ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
## client
![image](https://github.com/iniyasri4464/2c.ARP_RARP_PROTOCOLS/assets/152419072/64f90484-c30b-4859-a4ba-7e248092a86e)
## server
![image](https://github.com/iniyasri4464/2c.ARP_RARP_PROTOCOLS/assets/152419072/90dac413-2726-48b9-a917-fdec318319e6)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
