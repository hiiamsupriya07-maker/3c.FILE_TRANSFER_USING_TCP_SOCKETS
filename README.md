# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
```
#Server
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
while True:
    conn, addr = s.accept() 
    data =conn.recv(1024)
    print('Server received', repr(data))
    filename="D:\\Study Material\\CN EXP files\\mytext3c.txt"
    f = open(filename,'rb')## 'rb' read the file in binary format
    l = f.read(1024)
    while (l):
        conn.send(l)
        print('Sent',repr(l))
        l =f.read(1024)
    f.close()
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()
#Client
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
## OUPUT

<img width="1920" height="1080" alt="Screenshot 2026-05-19 211045" src="https://github.com/user-attachments/assets/9dcca164-10f1-4196-879d-b0e2865c6205" />

<img width="1920" height="1080" alt="Screenshot 2026-05-19 215244" src="https://github.com/user-attachments/assets/3384130f-8b7f-42b4-8820-a5d0b207cf58" />


## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
