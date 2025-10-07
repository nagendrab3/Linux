==> What is a package manager, and why is it used in Linux?

A package manager is a tool used in Linux to install, update, remove, and manage software packages on the system. It handles dependencies, downloads packages from repositories, and ensures the correct versions are installed.

==> What is the difference between apt and apt-get?

apt-get: Older tool, still widely used and fully supported. Used in scripting and automation.

apt: Introduced to be more human-readable and better for interactive use.

==> What command would you use to update the package index on an Ubuntu system?

sudo apt update — updates the package list (repository metadata), but does not install or upgrade any packages.

sudo apt upgrade — upgrades all installed packages to their latest available versions based on the updated package list.

==> How would you install a specific package, for example, nginx, using both apt and yum?

sudo apt update
sudo apt install nginx

REdhat
sudo yum install nginx

==> How do you remove a package using apt and yum? Also, what’s the difference between remove and purge in apt?

sudo apt remove <package> — removes the package but keeps the configuration files intact.

sudo apt purge <package> — removes the package along with its configuration files.


==> How can you list all installed packages using apt and yum?

sudo apt list --installed — for Debian-based systems

sudo yum list installed — note: the correct syntax for yum is without the double dashes for installed packages

==> How do you find out which package provides a specific file, say /usr/bin/python?

The command apt-file might not be installed by default, so you may need to install it first:

sudo apt update
sudo apt install apt-file
sudo apt-file update

Then you can search for the file:

apt-file search /usr/bin/python

==> What command would you use to clean the local repository of retrieved package files in both apt and yum? Why is this useful?

sudo apt clean: Removes all cached package files from /var/cache/apt/archives/.

sudo apt autoclean: Removes only cached package files that can no longer be downloaded (obsolete).

sudo yum clean all: Cleans all cached files from any enabled repository, including metadata and package files.

Why is this useful?

Frees up disk space by removing downloaded package files after installation.

Helps resolve issues with corrupted or outdated cache when repositories have changed.

Keeps the system tidy and reduces storage bloat.

==> How can you downgrade a package using apt or yum?

sudo apt install <package>=<version>

sudo yum downgrade <package>-<version>

==> Explain how you would add a new repository and install a package from it using apt and yum.

For apt (Debian/Ubuntu):

Add the repository:
You can add a repository by adding its URL to a file in /etc/apt/sources.list or better, by creating a new file under /etc/apt/sources.list.d/.

sudo add-apt-repository ppa:some/ppa-name

echo "deb http://repository.url/ubuntu bionic main" | sudo tee /etc/apt/sources.list.d/custom.list

Update package list:

sudo apt update

Install the package:

sudo apt install package-name

For yum (CentOS/RHEL):

Add the repo file:
Create a .repo file inside /etc/yum.repos.d/. For example:

sudo vi /etc/yum.repos.d/custom.repo

Add repo details like:

[custom-repo]
name=Custom Repository
baseurl=http://repository.url/path/
enabled=1
gpgcheck=1
gpgkey=http://repository.url/path/RPM-GPG-KEY-custom


Clean and update repo metadata:

sudo yum clean all
sudo yum makecache

Install package:

sudo yum install package-name

==> In a yum repo file, what directive specifies the URL where the repository’s packages are located?

baseurl=http://repository.url/path/

==> On a Debian-based system, how would you manually install a .deb package, and how would you fix dependency issues if any occur?

To manually install a .deb package on a Debian-based system (like Ubuntu), you use:

sudo dpkg -i package_name.deb

However, dpkg does not resolve dependencies automatically, so if there are missing dependencies, you might see errors.

To fix those dependency issues, run:

sudo apt-get install -f

This command tells APT to fix broken dependencies by installing what's missing.

wget http://example.com/some-package.deb
sudo dpkg -i some-package.deb
sudo apt-get install -f   # Fix any broken/missing dependencies

==> How do you manually install an .rpm package on a CentOS/RHEL system, and how do you check or fix any dependency issues?

To install an .rpm package:

sudo rpm -ivh package-name.rpm


-i: install

-v: verbose output

-h: show hash progress

To check for missing dependencies:

After installation, if there are missing dependencies, you’ll get error messages.

To install the .rpm package with dependencies resolved, use yum (or dnf on newer systems):

sudo yum install package-name.rpm

==> What is the purpose of the ifconfig command, and what basic information does it display?

ifconfig (interface configuration) is used to view and configure network interfaces on Linux systems.

It shows:

IP addresses (IPv4 and IPv6)

MAC addresses

Network interface status (UP/DOWN)

RX/TX packet stats


==> Which command is used to test basic network connectivity to a host, and how does it work?

The ping command is used to test network connectivity between your system and a remote host (like an IP address or domain).

It works by:

Sending ICMP Echo Request packets

Receiving Echo Reply packets (if the host is reachable)

It shows:

Round-trip time (latency)

Packet loss (if any)

Whether the host is reachable

==> What is the difference between wget and curl?

wget is a command-line utility used primarily to download files from the web via HTTP, HTTPS, or FTP.

It’s simple and great for downloading directly to disk.

curl is a more versatile tool used to transfer data to or from a server using various protocols (HTTP, HTTPS, FTP, etc.).

It can display response headers, send POST requests, upload files, and more

wget is mainly for downloading.

curl is for sending/receiving data — it's more suitable for API testing, debugging, and scripting.


==> Which command can you use to check which ports are currently open and which services are listening on them?

netstat -tuln

-t: TCP ports

-u: UDP ports

-l: Listening ports only

-n: Show numerical addresses (don’t resolve DNS)

==> How do you use curl to make a GET request and show response headers as well as the body?

To make a GET request and show both the headers and body using curl

curl -i https://example.com

-i stands for include headers in the output.

By default, curl sends a GET request unless you specify otherwise.

curl -i https://api.github.com

Response headers (e.g. HTTP/1.1 200 OK, Content-Type, etc.)

Response body (usually JSON or HTML)

==> What does the following ping output mean?

The output means:

5 packets were sent, and 5 were successfully received.

There was 0% packet loss, which indicates a stable and healthy network connection.

The total time for all pings was 4005 milliseconds (4 seconds).

A stable connection usually has low packet loss (preferably 0%) and consistent round-trip times.


==> How would you use curl to send a POST request with JSON data to a REST API endpoint?

To send a POST request with JSON data using curl, you can use:

curl -X POST https://api.example.com/endpoint \
     -H "Content-Type: application/json" \
     -d '{"key1": "value1", "key2": "value2"}'

-X POST → Specifies the HTTP method (POST).

-H → Adds a header (here, it's saying the data is JSON).

-d → Sends the actual data in the request body.

==> You’re logged into a Linux server. You want to test if port 8080 is open on a remote host (10.0.0.25).
Which command can you use from the terminal?

telnet (if available): telnet 10.0.0.25 8080  If the port is open, you'll get a successful connection message.

nc (netcat): nc -zv 10.0.0.25 8080

-z = scan mode (don’t send data)

-v = verbose

curl (if it's a web service):

curl http://10.0.0.25:8080

nmap (if installed):

nmap -p 8080 10.0.0.25

==> What does the df command do?

df shows disk space usage of mounted file systems.

==> What does the du command do?

du shows disk usage of files and directories.

==> What’s the difference between df and du?

df → shows free/used space on mounted file systems.

du → shows space used by individual directories/files

==> How do you check disk usage of all subdirectories in the current directory?

du -sh *

==> What does fdisk do?

fdisk is used to create, delete, and manage partitions on a disk (like /dev/sda). sudo fdisk /dev/sda

==> How do you view all disks and partitions on a Linux system?

lsblk
or
fdisk -l

==> What does the mount command do?

mount attaches a file system (like a disk or partition) to a directory so it can be used.

==> How do you unmount a mounted file system?

sudo umount /mnt	

sudo umount /dev/sdb1

==> How do you make a mount persistent after reboot?

Edit the /etc/fstab file and add an entry for the mount.

/dev/sdb1  /mnt  ext4  defaults  0  2

==> How do you format a new partition to ext4?

sudo mkfs.ext4 /dev/sdb1

==> You have a new partition /dev/sdb1. How would you format it with the ext4 file system?

To format /dev/sdb1 with the ext4 filesystem:

sudo mkfs.ext4 /dev/sdb1

mkfs stands for make file system. You run this before mounting the partition.

sudo mount /dev/sdb1 /mnt

