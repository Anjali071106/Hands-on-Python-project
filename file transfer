import socket
import os

def send_file(filename, host='localhost', port=5001):
    s = socket.socket()
    s.connect((host, port))
    s.send(filename.encode())
    s.recv(1024)
    with open(filename, "rb") as f:
        data = f.read()
        s.sendall(data)
    s.close()

def receive_file(save_as, host='localhost', port=5001):
    s = socket.socket()
    s.bind((host, port))
    s.listen(1)
    conn, addr = s.accept()
    filename = conn.recv(1024).decode()
    conn.send(b"OK")
    data = conn.recv(9999999)
    with open(save_as, "wb") as f:
        f.write(data)
    conn.close()
    s.close()
