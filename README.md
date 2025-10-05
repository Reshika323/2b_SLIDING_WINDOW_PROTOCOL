# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s

```
## Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT
## Client:
<img width="845" height="458" alt="442472193-ef87302f-4e11-4ec9-b0dd-61c9d73f74ef" src="https://github.com/user-attachments/assets/74fa393a-b181-4c82-ae57-824458a9c62d" />

## Server:

<img width="848" height="388" alt="442472196-010519a2-0ee7-40e9-b0c5-3f2a58a374a3" src="https://github.com/user-attachments/assets/bd01e20b-0743-4f18-a2a8-7290592dce24" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
