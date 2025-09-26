What is Linux Multi-User System?
Linux is designed as a multi-user operating system where multiple users can work simultaneously. Each user has their own account, home directory, and permissions. The system uses users and groups to control access to resources.

Why User Management Matters?

- Security: Control who can access what resources

- Organization: Separate different users' data and configs

- Resource Control: Limit what users can do on system

- Auditing: Track who performed what actions

- Collaboration: Enable multiple users to work securely

- Service Accounts: Run services under dedicated accounts

User Account Types

- Root User: System administrator with unlimited privileges (UID 0)

- System Users: Service accounts for daemons (UID 1-999)

- Regular Users: Normal user accounts for people (UID 1000+)

- Service Users: Accounts for specific applications

User Account Information

User data stored in several files:

- /etc/passwd: User account information

- /etc/shadow: Encrypted passwords and policies

- /etc/group: Group definitions and memberships

- /etc/gshadow: Group passwords and administrators

- /home/username: User's home directory

Essential User Commands

- useradd: Create new user accounts

- userdel: Delete user accounts

- usermod: Modify existing user accounts

- passwd: Change user passwords

- su: Switch user identity

- sudo: Execute commands as another user

- whoami: Display current username

- id: Show user and group IDs

Group Management

Groups are collections of users sharing permissions:

- Primary Group: User's main group (set at creation)

- Secondary Groups: Additional groups user belongs to

- Group permissions apply to all group members

- Files created inherit the user's primary group

Group Commands

- groupadd: Create new groups

- groupdel: Delete groups

- groupmod: Modify group settings

- gpasswd: Manage group memberships

- newgrp: Switch to different primary group temporarily

- groups: Show which groups a user belongs to

sudo Configuration

sudo allows users to run commands with elevated privileges:

- Configured in /etc/sudoers file

- Use visudo to edit safely

- Can grant specific commands or full access

- Logs all sudo usage for security auditing

- Timeout settings control privilege duration

Password Policies

Linux supports various password policies:

- Password aging: Force regular password changes

- Complexity requirements: Minimum length, character types

- Account locking: Lock accounts after failed attempts

- Password history: Prevent reusing recent passwords

- Expiration warnings: Notify before password expires


Best Practices

- Use sudo instead of logging in as root

- Create service accounts for applications

- Use strong passwords and enable policies

- Regularly audit and remove unused accounts

- Use groups to manage permissions efficiently

- Monitor user activity through logs

- Implement proper password aging policies


PRACTICE

==> Display information of the current user

id 

==> show which groups the current user belongs to

groups

==> display the contents of /etc/passwd for your use

grep $USER /etc/passwd

==> create a new group called "developers"

sudo groupadd developers

==> create a testuser with bash shell

sudo useradd -m -s /bin/bash testuser

==>set password for testuser account

sudo passwd testuser

==> add testuser to the developers group

usermod -aG developers testuser

==> verify testusers is in the developers group

groups testuser

==> create a directory owned by the developers group

sudo mkdir /tmp/dev-project && sudo chgrp developers /tmp/dev-project

==> set group write permissions on dev-project directory

sudo chmod g+w /tmp/dev-project

==> switch to test user account and test access

sudo su - testuser

==> list all user on the system from /etc/passwd

cut -d: -f1 /etc/passwd

==> find all files owned by testuser

sudo find /home -user testuser -type f 2>/dev/null

==> Lock the test user account

usermod -L testuser

==> delete testuser account

sudo userdel -r testuser 
