# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM


Server:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
c, addr = s.accept()
print("Connected to sender")

expected = 1

while True:
    data = c.recv(1024).decode()

    if not data:
        break

    print("Received:", data)

    print("Sending ACK", expected)
    c.send(("ACK " + str(expected)).encode())

    expected += 1

c.close()
s.close()
```
Client:
```

import socket

s = socket.socket()
s.connect(('localhost', 8000))

frames = ["Frame 1", "Frame 2", "Frame 3"]

for frame in frames:
    print("Sending:", frame)
    s.send(frame.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()

```
## OUTPUT

<img width="966" height="292" alt="image" src="https://github.com/user-attachments/assets/1ef1c433-1648-440f-afeb-d05528abdb89" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
