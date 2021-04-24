# Social Media System
---

### Introduction
- Social Media System with Client-Server architecture to let user make friends and post messages on their Walls
---

### Components of the system
- **Friends**: users who can exchange messages
- **Wall*: contains messages posted by friends
- **Server**: Stores information about the different users, their walls and who they are friends with

---
### How to?
Below are the basic commands to be sent to the Server:
- **wall**: containing message posted by friends to the user’s wall. Each line contains one message and has the following structure: friend id : message
- **friends**:  containing the id of the user’s friends, one id per line. Only friends can post to a user’s wall. Note that the friend relationship is not symmetric in our system: A can be a friend of B (A can write to B’s wall) while B is not a friend of A (B can not write to A’s wall)

---
- **The server is capable of the following operations:**
Create new user - Create a new folder and files to store a user’s information.

$ ./create.sh
Error: parameters problem
$ ./create.sh anthony
Error: user already exists
$ ./create.sh paul
OK: user created


Add new friend - Add a user to another user’s friend list.

$ ./add.sh paul
Error: parameters problem
$ ./add.sh tony anthony
Error: user does not exist
$ ./add.sh anthony tony
Error: friend does not exist
$ ./add.sh anthony thomas
Error: user already friends with this user
$ ./add.sh anthony paul
OK: friend added


Post a message - Add a message from one user to another user’s wall.

$ ./post.sh anthony
Error: parameters problem
$ ./post.sh tony anthony "Hey there"
Error: Receiver does not exist
$ ./post.sh anthony tony "Hey there"
Error: Sender does not exist
$ ./post.sh anthony aUserThatExistsButIsNotAFriendOfAnthony "Hey there"
Error: Sender is not a friend of receiver
$ ./post.sh thomas anthony "Hey there"
Ok: Message posted to wall


Show wall - Display the contents of a wall.

$ ./show.sh
Error: parameters problem
$ ./show.sh tony
Error: user does not exist
$ ./show.sh anthony
wallStart
thomas: hey, how are you?
aisling: so bored from lockdown, I wanna go out!
wallEnd
