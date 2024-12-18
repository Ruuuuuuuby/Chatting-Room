# Chatting-Room

Build a TCP-based, console-controlled, multi-user chat room with login and registration functionality (no graphical interface).
Knowledge Points Used

• Loops, conditionals, collections, IO, multithreading, and network programming.
Preparation

Create a txt file in the current module to store valid usernames and passwords.
File Content:
java
￼Copy code
// Left is the username
// Right is the password
zhangsan=123
lisi=1234
wangwu=12345
Requirements

1. Initial Client Prompt
When the client starts, it connects to the server and displays the following prompt:
java
￼Copy code
Server connected successfully  
============== Welcome to the Chat Room ==============  
1. Login  
2. Register  
Please enter your choice:  
2. Login Option
If the user selects login, the following prompts appear:
java
￼Copy code
Server connected successfully  
============== Welcome to the Chat Room ==============  
1. Login  
2. Register  
Please enter your choice:  
1  
Please enter your username:  
3. Enter Username and Password
The user inputs their username and password. Before pressing Enter, the input appears like this:
java
￼Copy code
Server connected successfully  
============== Welcome to the Chat Room ==============  
1. Login  
2. Register  
Please enter your choice:  
1  
Please enter your username:  
zhangsan  
Please enter your password:  
123  
4. Server Validation
After pressing Enter, the client sends the data to the server for validation. The server checks the txt file for the username and password and responds with one of the following messages:
1. Login Successful:
java
￼Copy code
Login successful
2. Incorrect Password:
java
￼Copy code
Incorrect password
3. Username Not Found:
java
￼Copy code
Username does not exist
5. Client Handling Based on Server Response
• Login Successful:
The client can start chatting with the following prompt:
java
￼Copy code
Login successful, you can now start chatting.  
Please enter your message:  
• Incorrect Password:
The user is prompted to re-enter their login information:
java
￼Copy code
Incorrect password  
============== Welcome to the Chat Room ==============  
1. Login  
2. Register  
Please enter your choice:  
• Username Not Found:
The user is prompted to re-enter their login information:
java
￼Copy code
Username does not exist  
============== Welcome to the Chat Room ==============  
1. Login  
2. Register  
Please enter your choice:  
6. Group Chat Functionality
If login is successful, the user can start group chatting. When a client sends a message to the server:
• The server forwards the message to all connected clients.
Key Notes:
• Do not use broadcast addresses, as this is specific to UDP.
• Store all client Socket objects in a collection (e.g., a Set or List).
• To send a message to all users, iterate through the collection and forward the message to each client.
Message Forwarding Diagram
The server acts as a message relay to all connected clients:
arduino
￼Copy code
Client 1  ----\                   /----> Client 2
               |   Server (Relay) |
Client 3  ----/                   \----> Client 4
Additional Requirements

Username and Password Validation Rules
1. Username Requirements:
• Must be unique.
• Length: 6 to 18 characters.
• Must contain only letters (no numbers or special characters).
2. Password Requirements:
• Length: 3 to 8 characters.
• The first character must be an uppercase or lowercase letter.
• The remaining characters must be numbers only.
Client-Side Functionalities

1. Initial Prompt:
• The user chooses between Login or Register.
• This repeats until they successfully log in or register.
2. Login:
• The client sends the following format to the server:
java
￼Copy code
username=zhangsan&password=123
3. Register:
• The client sends the following format to the server:
java
￼Copy code
username=zhangsan&password=123
4. Chat:
• Upon successful login, the user can send messages, which the server forwards to all connected clients.
Server-Side Functionalities

1. Load User Data:
• The server reads the txt file to load valid usernames and passwords into memory.
2. Client Connection Handling:
• When a client connects, the server starts a new thread to handle the connection.
3. Login and Registration:
• Login: Validate the username and password against the file data.
• Registration:
• Check if the username is unique.
• Validate the username and password formats.
• If valid, save the new credentials to the file.
4. Start Chat:
• If login or registration is successful, the server allows the client to start chatting.
5. Message Forwarding:
• The server acts as a relay, forwarding messages from one client to all other clients.
Example Workflow
1. Client A logs in successfully and sends a message:
java
￼Copy code
Hello, everyone!
2. The server receives the message and forwards it to Client B, Client C, and all other connected clients.
