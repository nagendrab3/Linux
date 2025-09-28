What is Package Management?

Package management is the method of installing, updating, configuring, and removing software packages on Linux systems. Ubuntu uses the Advanced Package Tool (apt) which handles dependencies, security updates, and software repositories automatically.

Why Package Management Matters?

- Security: Automated security updates and vulnerability patches

- Dependency handling: Automatically resolves software dependencies

- System integrity: Prevents conflicts between software packages

- Efficiency: Centralized software installation and removal

- Updates: Easy system-wide software updates

- Repositories: Access to thousands of tested software packages

APT Package Manager

- apt: Modern, user-friendly interface

- apt-get: Traditional interface with more options

- apt-cache: Search and query package information

- dpkg: Low-level package management tool

- aptitude: Advanced package management with dependency resolution

Essential APT Commands

- apt update: Refresh package lists from repositories

- apt upgrade: Upgrade installed packages

- apt install: Install new packages

- apt remove: Remove packages (keep configuration)

- apt purge: Remove packages and configuration files

- apt search: Search for packages

- apt show: Display package information

Package Repositories

- Main: Canonical-supported open source software

- Universe: Community-maintained open source software

- Restricted: Proprietary drivers and codecs

- Multiverse: Software with copyright restrictions

- PPA: Personal Package Archives for additional software

Package States

- Installed: Package is installed and configured

- Not installed: Package is available but not installed

- Upgradeable: Newer version available

- Held: Package version is locked

- Broken: Package has unmet dependencies

**PRACTICE**

==> update package database

sudo apt update

==> show upgradeable packages

apt list --upgradable

==> Search for packages related to the "network"

apt search network

==> install the tree command utility

sudo apt install tree -y

==> show detailed information about the tree package

apt show tree

==> List all installed packages

apt list --installed

==> install multiple packages

apt install htop ncdu tmux -y

==> check which files are installed by the tree package

dpkg -L tree

==> find which package provides the /bin/ls command

dpkg -S /bin/ls

==> remove the ncdu package but keep its configuration

sudo apt remove ncdu

==> show packages that can be automatically removed

apt autoremove --dry-run

==> clean the package cache

sudo apt clean

==> check for broken packages

sudo apt check

==> hold the tmux package to prevent updates

sudo apt-mark hold tmux

==> show held packages

apt-mark showhold

