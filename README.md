# ECHOSERVER 
Echo server and client using python socket

## AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

1) Design of echo server and client using python socket
2) Implementation using Python code
3) Testing the server and client
4) Run the server side first that listening (or) waiting the client side.
5) After that run the client side.
6) finally we got the output as "HELLO! WORLD" 

## PROGRAM:

### CLIENT SIDE
python
```
import socket
HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello, world")
    data = s.recv(1024)
print(f"Received {data!r}")
```


### SERVER SIDE 
python
```
import socket
HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    try:
        s.bind((HOST, PORT))
    except Exception as e:
        print(f"Error binding to {HOST}:{PORT}: {e}")
        exit()
    s.listen()
    print(f"Listening on {HOST}:{PORT}...")
    try:
        conn, addr = s.accept()
    except Exception as e:
        print(f"Error accepting connection: {e}")
        exit()
    with conn:
        print(f"Connected by {addr}")
        while True:
            try:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)
            except Exception as e:
                print(f"Error receiving/sending data: {e}")
                exit()
```

## OUTPUT:

### SERVER SIDE 

<img width="460" alt="image" src="https://github.com/Monisha-11/Echoserver/assets/93427240/8b032737-da85-4378-9440-f20c7636cc9d">

### CLIENT SIDE 
<img width="865" alt="image" src="https://github.com/Monisha-11/Echoserver/assets/93427240/55175569-07ae-40ce-b338-44ed99cb8da3">

## RESULT:
The program is executed successfully
