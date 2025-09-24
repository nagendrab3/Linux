What is the Linux Command Line?
The Linux command line, accessed through a terminal or shell is a text-based interface for interacting with the operating system. 
It provides direct access to system functions and is often more powerful and efficient than graphical interfaces.

Why Master Command Line Basics?

- Many tasks are faster via command line than GUI

- Commands can be scripted and automated

- Essential for managing remote servers via SSH

- Access to advanced system functions not available in GUI

- Same commands work across different Linux distributions

- Command line often works when GUI fails

Linux File System Hierarchy

- / (root): Top-level directory containing all others

- /home: User home directories

- /etc: System configuration files

- /var: Variable data like logs and databases

- /usr: User programs and applications

- /tmp: Temporary files cleared on reboot

- /bin: Essential system binaries

- /opt: Optional/third-party software

Basic Command Structure

Commands follow this pattern: command [options] [arguments]

- ls -l /home (command, option, argument)

- mkdir -p test/nested (nested directory creation)

- cp file1.txt backup/ (copy source to destination)

Essential Navigation Commands
- pwd: Print current working directory

- ls: List directory contents (ls -la for detailed view)

- cd: Change directory (cd .. for parent, cd ~ for home)

- find: Search for files and directories

- locate: Fast file search using database

- which: Find location of commands

File Operations
- touch: Create empty files or update timestamps

- cp: Copy files and directories (cp -r for recursive)

- mv: Move/rename files and directories

- rm: Remove files (rm -r for directories)

- mkdir: Create directories (mkdir -p for nested)

- rmdir: Remove empty directories

Text Viewing Commands
- cat: Display entire file content

- less/more: View file content page by page

- head: Show first lines of file

- tail: Show last lines of file (tail -f for real-time)

- grep: Search text patterns in files

Getting Help
- man: Manual pages for detailed command help

- --help: Quick command help option

- info: Detailed information pages

- apropos: Search manual pages by keyword

Command Line Tips
- Tab completion for commands and paths

- Up/down arrows to navigate command history

- Wildcards: * for multiple, ? for single character

- Pipes: | to chain commands together

- Background: & to run commands in background

**PRACTICE**

==> Display your current directory

PWD

==> list all files in the current directory, including hidden files

ls -a

==> Navigate to home directory

cd ~

==> create a directory called lab-practice

mkdir lab-practice

==> navigate in to the lab-practice directory

cd lab-practice

==> create nested directories docs/projects/web

mkdir -p docs/projects/web

==> create three empty files file1.txt, file2.txt, file3.txt

touch file1.txt file2.txt file3.txt

==> copy file1.txt to the docs directory

cp file1.txt docs

==> move file2.txt to the docs directory and rename it to backup.txt

mv file2.txt docs/backup.txt

==> copy the entire docs directory to create a backup called docs-backup

cp -r docs docs-backup

==> find all .txt files in the current directory and sub directories

find . -name *.txt*

==> Display the contents of file1.txt

cat file1.txt

==> get help information for the ls command

man ls

==> go back to the parent directory 

cd ..

==> remove file3.txt

rm lab-practice/file3.txt

