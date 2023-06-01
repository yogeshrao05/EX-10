# EX-10 APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM

## DATE : 08/05/2023

## AIM :
To write a python program for creating File Transfer using TCP Sockets Links.

## ALGORITHM :

1.Import the necessary python modules.

2.Create a socket connection using socket module.

3.Send the message to write into the file to the client file.

4.Open the file and then send it to the client in byte format.

5.In the client side receive the file from server and then write the content into it

## PROGRAM :
## Client
Developed by : Yogesh rao S D
Register no : 212222110055
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
 while True:
 print('receiving data...')
 data = s.recv(1024)
 print('data=%s', (data))
 if not data:
 break
 f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
## Server
Developed by : yogesh rao S D
Register no : 212222110055
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
 conn, addr = s.accept()
 data = conn.recv(1024)
 print('Server received', repr(data))
 filename='mytext.txt'
 f = open(filename,'rb')
 l = f.read(1024)
 while (l):
 conn.send(l)
 print('Sent ',repr(l))
 l = f.read(1024)
 f.close()
 print('Done sending')
 conn.send('Thank you for connecting'.encode())
 conn.close()
 ```
## OUTPUT :

## clientoutput :

![7 client](https://github.com/yogeshrao05/EX-10/assets/122008288/5a0900bd-3e9e-4480-a873-b418d4851d8a)

## serveroutput :

![7 server](https://github.com/yogeshrao05/EX-10/assets/122008288/ae502228-9209-4be1-86c4-1d57b1364445)


## RESULT :
Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
