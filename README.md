## Ex.No:2b Sliding window protocol

## AIM:
To write a python program to perform sliding window protocol.

## ALGORITHM:
1. Start the program.
   
2. Get the frame size from the user.
   
3. To create the frame based on the user request.
   
4. To send frames to server from the client side.
   
5. If your frames reach the server it will send ACK signal to client.
   
6. Stop the Program.
   
## PROGRAM:
# Client
~~~
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
~~~

# Server
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
~~~

## OUTPUT:
# Client
![image](https://github.com/NaliniG007/2b_SLIDING_WINDOW_PROTOCOL/assets/139334830/40c38d61-70e7-44e9-a8a2-8c38e2c48d8f)

# Server
![image](https://github.com/NaliniG007/2b_SLIDING_WINDOW_PROTOCOL/assets/139334830/6155a5c1-1e64-4494-90a9-4e6ffd6e539e)

## RESULT:
Thus, python program to perform sliding window protocol was successfully executed.
