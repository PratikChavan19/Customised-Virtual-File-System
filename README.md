📌 Overview :

This project implements a Customised Virtual File System (CVFS) in C++, simulating core functionalities of a real file system.

It is based on concepts like:
  Inode structure
  File descriptors
  File tables
  Memory-based storage

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

  🏗️ Architecture Diagram :

                +----------------------+
                |     User Shell       |
                | (Command Interface)  |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |   Command Parser     |
                +----------+-----------+
                           |
                           v
                +----------------------+
                |   File System APIs   |
                | create, open, read   |
                | write, lseek, rm     |
                +----------+-----------+
                           |
          +----------------+----------------+
          |                                 |
          v                                 v
+--------------------+           +----------------------+
|   UFDT (FD Table)  |           |     Inode List       |
| File Descriptors   |           | (DILB Linked List)   |
+--------------------+           +----------------------+
          |                                 |
          +--------------+------------------+
                         |
                         v
                +----------------------+
                |   Super Block        |
                | (Free Inodes Info)   |
                +----------------------+

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

⚙️ Features :

  📁 Create/Delete files
  📖 Read/Write operations
  🔓 File permissions (Read / Write / Read+Write)
  📌 File descriptor management
  🔄 File offset manipulation (lseek)
  📊 File metadata (stat, fstat)
  📋 File listing (ls)
  🧠 In-memory file system (no disk I/O)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🧱 Core Components :

🔹 Super Block
    Stores total and free inodes
🔹 Inode (File Metadata)
    File name, size, type, permissions
    Link count & reference count
    Buffer pointer (actual data)
🔹 UFDT (User File Descriptor Table)
    Maps file descriptors to file tables
🔹 File Table
    Maintains:
      Read/Write offset
      Mode
      Pointer to inode

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🚀 How to Compile & Run :

🔧 Compile :
  g++ CVFS.cpp -o cvfs
▶️ Run :
  ./cvfs

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

💻 Supported Commands :

Command	                      Description
create <name> <perm>	        Create new file
open <name> <mode>	          Open file
read <name> <bytes>	          Read data
write <name>	                Write data
ls	                          List files
stat <name>	                  File info (by name)
fstat <fd>	                  File info (by FD)
truncate <name>	              Clear file data
rm <name>	                    Delete file
close <name>	                Close file
closeall	                    Close all files
lseek <name> <size> <from>	  Change offset
help	                        Show commands
exit	                        Exit system

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

📚 Libraries Used :

Library    	Purpose
stdio.h	    Input/Output
stdlib.h	  Memory allocation
string.h	  String handling
unistd.h	  System calls
iostream	  C++ I/O

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🧠 System Calls & Their Usage :

🔹 read()
  Used to display file content to console
🔹 write()
  Used to output data (stdout)
🔹 malloc()
  Allocates memory for:
  Inodes
  File tables
  Buffers
🔹 free()
  Frees allocated memory (on delete)
🔹 memset()
  Clears file buffer (truncate)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

⚙️ Internal Functions :

File Management :
  CreateFile() → Creates new file
  OpenFile() → Opens existing file
  rm_File() → Deletes file
Read/Write :
  ReadFile() → Reads from buffer
  WriteFile() → Writes into buffer
File Info :
  stat_file() → Info by name
  fstat_file() → Info by FD
Navigation :
  LseekFile() → Offset control
Utilities :
  ls_file() → List files
  GetFDFromName() → Get file descriptor
  Get_Inode() → Get inode

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

📊 Example Usage :

Pratik VFS : > create Demo 3
File is successfully created with file descriptor : 0

Pratik VFS : > write Demo
Enter the data :
Hello CVFS

Pratik VFS : > read Demo 5
Hello

Pratik VFS : > ls
File Name    Inode    Size    LinkCount
Demo         1        10      1

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

⚠️ Limitations :

No persistent storage (RAM only)
Limited file size (1024 bytes)
Limited number of files (50)
No directory hierarchy
No multi-user support

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

🔮 Future Enhancements :

💾 Disk-based persistence
📂 Directory structure support
👥 Multi-user environment
🔐 File security & authentication
🧵 Multi-threading support

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

👨‍💻 Author

Pratik Chavan

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
