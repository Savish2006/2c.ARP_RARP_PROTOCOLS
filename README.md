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
#CLIENT:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()

address = {"165.165.80.80": "6A:08:AA:C2", "165.165.79.1": "8A:BC:E3:FA"}

while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

#SERVER:

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter logical Address: ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
```

## OUPUT - ARP

#CLIENT:


<img width="495" height="296" alt="image" src="https://github.com/user-attachments/assets/02a5840f-204d-4363-8541-ec8234edcec0" />


#SERVER:


<img width="537" height="305" alt="image" src="https://github.com/user-attachments/assets/20b2d835-fb47-467c-af82-42f2d2eacf46" />

## PROGRAM - RARP

#CLIENT:

```
import socket

s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)
c, addr = s.accept()

address = {"6A:08:AA:C2": "192.168.1.100", "8A:BC:E3:FA": "192.168.1.99"}

while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```

#SERVER:

```
import socket

s = socket.socket()
s.connect(('localhost', 9000))

while True:
    ip = input("Enter MAC Address: ")
    s.send(ip.encode())
    print("Logical Address:", s.recv(1024).decode())
```
## OUPUT -RARP


#CLIENT:




<img width="491" height="250" alt="image" src="https://github.com/user-attachments/assets/743e5be6-4843-42c9-b75c-10fe4066e565" />



#SERVER:



<img width="526" height="292" alt="image" src="https://github.com/user-attachments/assets/c55314ee-ce48-4afc-acb3-3b09e70eb210" />



## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
