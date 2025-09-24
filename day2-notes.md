What is the Linux File System?

The Linux file system is a hierarchical structure organizing all files and directories. Unlike Windows with drive letters, Linux uses a single tree structure starting from root (/). 
Everything in Linux is treated as a file, including directories, devices, and processes.

Linux File System Hierarchy Standard (FHS)

- /bin: Essential system binaries (ls, cp, mv)

- /sbin: System administration binaries

- /etc: System configuration files

- /home: User home directories

- /var: Variable data (logs, databases, mail)

- /usr: User programs and data

- /tmp: Temporary files

- /proc: Virtual file system with process information

- /dev: Device files

- /mnt: Mount points for temporary file systems


Understanding File Permissions
Linux permission system based on three user types:

- Owner (u): The user who owns the file

- Group (g): Users in the file's group

- Others (o): All other users

Three permission types:

- Read (r): View file contents or list directory

- Write (w): Modify file contents or create/delete in directory

- Execute (x): Run file as program or enter directory

Permission Representation
Two formats for showing permissions:

- Symbolic: rwxrwxrwx (owner, group, others)

- Numeric: 755 (4=read, 2=write, 1=execute)

Common examples:

- rwxr-xr-x (755): Owner full, others read/execute

- rw-r--r-- (644): Owner read/write, others read only

- rwx


(700): Owner full access, no others access
File Ownership
Every file has owner and group:

- Owner: Individual user who owns the file

- Group: Group of users sharing access

- chown: Change ownership

- chgrp: Change group ownership

- chmod: Change permissions


Special Permissions

- Sticky Bit: Prevents deletion by non-owners

- SUID: Execute with owner's permissions

- SGID: Execute with group's permissions

- umask: Default permissions for new files

File Types in Linux

- Regular files (-): Standard files containing data

- Directories (d): Containers for other files

- Symbolic links (l): Pointers to other files

- Device files (b/c): Hardware device interfaces

- Named pipes (p): Inter-process communication

- Sockets (s): Network communication endpoints

**PRACTICE:**

==> Create a directory called permission-lab and navigate to it

mkdir permission-lab && cd permission-lab

==> create a file called test.txt with some content 

echo "Hello Linux!" > test.txt

==> check the current permissions of test.txt

ls -l test.txt

==> change permissions of test.txt to read only for all users

chmod 444 test.txt


==> restore write permission for the owner

chmod u+w test.txt


==> create script file called hello.sh with a simple command

echo "#!/bin/bash
echo "Hello from script!"" > hello.sh

==> make the script executable and run it

chmod +x hello.sh && ./hello.sh

==> check the owner and group of your files

ls -l

==> create a symbolic link to test.txt called link-to-test

ln -s test.txt link-to-test

==> display the file type info for all files

files *

==> show disk usage of current directory 

du -sh

==> find all executable files in the current directory

find . -type f -executable

==> Display inode number test.txt

ls -i test.txt


