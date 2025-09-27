What are Linux Processes?

A process is a running instance of a program in Linux. Every command you execute, every application you run, and every system service creates one or more processes. Understanding process management is crucial for system administration and troubleshooting.

Why Process Management Matters?

- System monitoring: Track resource usage and system health

- Troubleshooting: Identify and resolve performance issues

- Security: Monitor for suspicious processes and activities

- Resource control: Manage CPU and memory usage

- Service management: Start, stop, and restart system services

- Automation: Create scripts that manage long-running processes

Process States

- Running: Currently executing on CPU

- Sleeping: Waiting for event or resource

- Stopped: Suspended by signal

- Zombie: Finished but parent hasn't collected exit status

- Daemon: Background system processes

Essential Process Commands

- ps: Display running processes

- top: Real-time process monitor

- htop: Enhanced interactive process viewer

- kill: Terminate processes by PID

- killall: Terminate processes by name

- jobs: Show background jobs

- nohup: Run commands immune to hangups

Process Control

- Ctrl+C: Interrupt (SIGINT) running process

- Ctrl+Z: Suspend (SIGTSTP) process to background

- & : Run command in background

- fg: Bring background job to foreground

- bg: Resume suspended job in background

System Monitoring

- uptime: System load averages

- free: Memory usage statistics

- iostat: I/O statistics

- vmstat: Virtual memory statistics

- lsof: List open files and processes

- netstat: Network connections and processes

**PRACTICE**

==> Display all running processes in detailed format

ps aux

==> show processes in a tree format to see parent child relationships

ps auxf

==> start the top command to monitor process in real time

top

==> find the process id of bash shell

ps aux | grep bash


==> display current system uptime and load averages

uptime

==> show memory user information

free -h

==> start a long running sleep command in the background

sleep 300 &

==> list current background jobs

jobs

==> Find the PID of the sleep process

ps aux  | grep sleep

==> kill the sleep process using its pID

kill -9 PID ; kill $(pgrep sleep)

==> start another sleep process and suspend with Ctrl +Z

sleep 100
ctrl +Z

==> resume suspened job in the background

bg

==> Display prcesses owned by current user

ps u
 
==> kill all sleep process at one time

killall sleep

==> show the most CPu-intensive process
ps aux --sort=-%cpu | head

