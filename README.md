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
client 
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
        print(f'data={data}')
        if not data:
            break
        f.write(data)
print('Successfully received the file')
s.close()
print('Connection closed')

```
server
```
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)
print(f"Server listening on {host}:{port}...")
while True:
    conn, addr = s.accept()
    print(f'Got connection from {addr}')

    data = conn.recv(1024)
    print('Server received:', repr(data))

    filename = 'mytext.txt'
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    print('Done sending')
    conn.send('Thank you for connecting'.encode())  
    conn.close()

```
## OUPUT




client 



![3cclient](https://github.com/user-attachments/assets/bc3da616-06a6-4a70-8c7d-44b8b8667783)




server



![3cserver](https://github.com/user-attachments/assets/93b22f0d-2dd1-4ac7-9e22-9a36fcade675)




## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
