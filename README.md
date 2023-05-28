# EX-3 IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
# DATE : 22-03-2023
# AIM :
To write a python program to perform sliding window protocol.

# ALGORITHM :
1.Start the program.

2.Get the frame size from the user

3.To create the frame based on the user request.

4.To send frames to server from the client side.

5.If your frames reach the server it will send ACK signal to client otherwise it will send NACKsignal to client.

6.Stop the program

# PROGRAM :
## CLIENT:
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
## SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode()
 ```
# OUTPUT :
## CLIENT:
![image](https://github.com/yuvabharathib/EX-3/assets/113497404/3f16d9b8-16d2-41cb-956b-4cc93d60817f)


## SERVER:
![image](https://github.com/yuvabharathib/EX-3/assets/113497404/ebca141b-2ba4-435e-ba0f-6d1ce2c56561)


# RESULT:
Thus, python program to perform stop and wait protocol was successfully executed.
