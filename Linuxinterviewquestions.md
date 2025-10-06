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
