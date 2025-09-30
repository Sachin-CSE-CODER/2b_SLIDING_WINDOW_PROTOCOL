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

CLIENT 
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

 SERVER
 ```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True: 
 print(s.recv(1024).decode())
 s.send("acknowledgement recived from the server".encode())
```


## OUPUT
<img width="530" height="227" alt="Screenshot 2025-09-30 085442" src="https://github.com/user-attachments/assets/9628986c-e637-4de1-9f5c-bd7963762dee" />
<img width="529" height="225" alt="Screenshot 2025-09-30 085435" src="https://github.com/user-attachments/assets/eff1cbae-e067-4840-9924-b87e371e61c9" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
