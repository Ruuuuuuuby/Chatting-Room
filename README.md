# Multi-Client Chatroom Using TCP Protocol

This project is a command-line multi-client chatroom application implemented using Java TCP Sockets. It includes functionalities for user login, registration, and group chatting. The server processes client connections in multi-threaded mode, ensuring real-time communication between multiple users.
Features

1. Login and Registration:
• Users can log in with a valid username and password.
• New users can register, ensuring unique usernames and proper password format.
2. Group Chat:
• Messages sent by a client are broadcast to all connected clients.
• Real-time message delivery using a server that handles multiple clients concurrently.
3. Data Storage:
• User credentials are stored in a text file (userinfo.txt) on the server.
Technologies Used

• Java SE: Core programming language.
• TCP Sockets: For server-client communication.
• Multi-threading: To handle multiple clients simultaneously.
• File I/O: For storing and retrieving user credentials.
• Collections API: To manage connected client sockets.

Project Structure

bash
￼Copy code
sockethomework/
├── servicedir/
│   └── userinfo.txt           # Stores valid usernames and passwords
├── src/
│   └── com/
│       └── ruuuuuuuby/
│           ├── server/
│           │   ├── Server.java        # Main server code
│           │   ├── MyRunnable.java    # Thread for handling individual clients
│           └── client/
│               ├── Client.java        # Main client code
│               └── ClientMyRunnable.java # Client-side thread for receiving messages
└── out/                        # Compiled .class files
Prerequisites

Before running the project, ensure the following:
1. Java JDK (version 8 or higher) is installed.
2. The userinfo.txt file exists under the servicedir directory with user credentials.
Example userinfo.txt content:
makefile
￼Copy code
zhangsan=123
lisi=1234
wangwu=12345
How to Compile and Run

1. Compile the Project
Run the following command in the project root directory:
bash
￼Copy code
javac -d out src/com/ruuuuuuuby/server/*.java src/com/ruuuuuuuby/client/*.java
2. Start the Server
Run the server to listen on port 10001:
bash
￼Copy code
java -cp out com.ruuuuuuuby.server.Server
Server Output:
arduino
￼Copy code
Server started, listening on port 10001...
3. Start the Client
Open a new terminal window and run the client:
bash
￼Copy code
java -cp out com.ruuuuuuuby.client.Client
Client Output:
arduino
￼Copy code
Server connected successfully
==============Welcome to the Chatroom================
1 Login
2 Register
Enter your choice:
Usage

1. Login:
• Choose option 1 and enter your username and password.
• Successful login starts the group chat.
2. Registration:
• Choose option 2 to register a new user with unique credentials.
3. Group Chat:
• After logging in, type messages, and they will be broadcast to all connected clients.
• The server will display messages sent by clients in the console.
Testing the Project

1. Start the server.
2. Open multiple client instances to simulate multiple users.
3. Test the following scenarios:
• Successful login with valid credentials.
• Login failure with incorrect username or password.
• Registration of new users.
• Group chat where all messages are broadcast to all clients.
Example Interaction

Server Console:
arduino
￼Copy code
Server started, listening on port 10001...
Client connected: /127.0.0.1
User zhangsan logged in successfully
zhangsan sent: Hello everyone!
Client 1:
mathematica
￼Copy code
Server connected successfully
==============Welcome to the Chatroom================
1 Login
2 Register
Enter your choice:
1
Enter Username:
zhangsan
Enter Password:
123
Login successful, start chatting
Enter your message:
Hello everyone!
Client 2:
yaml
￼Copy code
Server connected successfully
==============Welcome to the Chatroom================
1 Login
2 Register
Enter your choice:
1
Enter Username:
lisi
Enter Password:
1234
Login successful, start chatting
zhangsan sent: Hello everyone!
Error Handling

• Incorrect Password: Displays "Incorrect password".
• Username Not Found: Displays "Username does not exist".
• Disconnected Clients: Server detects disconnections and removes invalid sockets.
Known Issues

1. Broken Pipe: Occurs when a client disconnects unexpectedly.
• Solution: Check for valid sockets before broadcasting messages.
2. Port Conflicts: Ensure port 10001 is free before starting the server.
Future Enhancements

1. Add private chat functionality between users.
2. Improve user registration validation with advanced checks.
3. Implement a GUI interface for a better user experience.
Author

• ruuuuuuuby
• Contact: jru6055@gmail.com
License

This project is licensed under the MIT License.
