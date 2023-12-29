![](https://github.com/OverclockedD2/easier_sockets/blob/main/notice.png)

![#f03c15](https://place-hold.it/1024x64/0a0c10/adff2f/00000.png&text=EASIER_SOCKETS&bold&italic&fontsize=32)

**Introduction**
=

| The easier_sockets library makes Python sockets even easier to use and is great for beginners to understand the basics of networking, It’s mostly a wrapper around the Python standard library `socket`, but also includes functionality for encrypted communication using the `rsa` library. |
| :- |

<br/><br/>

> [!important]
> This library is intented for quick testing and experimenting, so it shouldn't be used as the core of any professional or critical project, because it may contain security vulnerabilities or bugs. Users are advised to exercise caution and thoroughly inspect the code for potential flaws before implementing it for any product available to the public. By using this software, individuals accept full responsibility for assessing its suitability and ensuring its safety for their intended use.

<br/><br/>

**Installation**
=
#### PYPI
```css
pip install easier_sockets
```
#### GITHUB
> Download the [***source code***](https://github.com/OverclockedD2/easier_sockets) from GitHub

<br/><br/>

**Usage**
=
#### IMPORTING
```python
import easier_sockets
```
#### CLIENT
```python
client = easier_sockets.client(9999)  # Set target port to 9999 (the default target name is 127.0.0.1)
client.connect()  # Connect to server
print(client.receive_packet())  # Print the received packet
client.send_packet("Make sure to check OverclockedD2's other cool project's as well!")  # Send a packet
client.disconnect()  # Disconnect from the server
client.terminate()  # Close the client
```
#### SERVER
```python
server = easier_sockets.server(9999)  # Starting the server on port 9999
server.accept()  # Accept a client
server.send_packet("Make sure to ★STAR★ easier_sockets on GitHub!")  # Send a packet
print(server.receive_packet())  # Print the received packet
server.kick()  # Kick the connected client
server.terminate()  # Close the server
```
#### ENCRYPTION (RSA)
```python
client = easier_sockets.client(9999, encrypted=True)
server = easier_sockets.client(9999, encrypted=True)

# You can also change the size of the keys used for encrypted by changing the value of the rsa_key_size parameter(default is 2048)
```
#### SHORTCUTS *(for all the lazy people)*
```python
client = easier_sockets.client(9999)
client.c()  # Connect to server
client.s()  # Send a packet
client.r()  # Recieve a packet
client.d()  # Disconnect from server
client.t()  # Terminate the client

server = easier_sockets.server(9999)
server.c()  # Accept a client
server.s()  # Send a packet
server.r()  # Recieve a packet
server.d()  # Kick the client
server.t()  # Terminate the server
```
#### FURTHER CUSTOMIZATION
```python
client = easier_sockets.client(server_port: int, server_name: str = "127.0.0.1", name: str = None, port: int = None, encrypted: bool = False, rsa_key_size: int = 2048, packet_size: int = 8192, timeout: float = 600)
# server port, server name, name to use, port to use, is the connection encrypted, the size of rsa keys, size of packets, timeout (if the server doesn't respond in time. Measured in seconds).

server = easier_sockets.server(port: int = 0, name: str = "0.0.0.0", client_name: str = None, client_port: int = None, encrypted: bool = False, rsa_key_size: int = 2048, packet_size: int = 8192, queue_size: int = 8, timeout: float = 600)
# port to use, name to use, specify the client name (if client name is different, then it gets kicked), specify the client port (if the client port is different, then it gets kicked), is the connection encrypted, the size of rsa keys, the size of packets, the queue size (you are cycling through the queue using server.accept()), timeout (if the client doesn't respond int time. Measured in seconds)
```
#### CLASS VARIABLES
```python
# The following class variables CAN be changed, but once the object is created, they shouldn't be messed with, as that could cause some errors. But reading them is perfectly fine. It should be pretty obvious what they all contain from their names so I wont add a comment behind each one. 

# Class variables of the client
client.name
client.port
client.server_name
client.server_port
client.encrypted
client.rsa_key_size
client.packet_size
client.timeout
client.client
client.server_public_key
client.own_public_key
client.own_private_key

# Class variables of the server
server.name
server.port
server.client_name
server.client_port
server.encrypted
server.rsa_key_size
server.packet_size
server.queue_size
server.timeout
server.server
server.client_info
server.socket
server.client_public_key
server.own_public_key
server.own_private_key
```
