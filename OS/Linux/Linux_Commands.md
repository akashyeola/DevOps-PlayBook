_________________________________________

# Linux
### 1. Linux Fundamentals
- **Overview of Linux    -  Distributions**:
    - Linux Kernel: The core of the operating system, managing hardware resources and enabling communication between software and hardware.   
    - GNU Tools: Essential system software like compilers, libraries, and shell programs, which form the backbone of most distributions.    
    - Package Management: Each distribution comes with a package management system to install, update, and remove software (e.g., APT for Debian-based distros, YUM for Red Hat-based distros).   
    - Desktop Environments: Distributions often include desktop environments like GNOME, KDE, or XFCE, providing a graphical interface for users.   
    - Customization: Distros are highly customizable, allowing users to select the software and tools they want during installation.

- **Linux Installation and Setup**: Installing Linux on different environments (bare metal, virtual machines, cloud instances).  
Bare metal refers to a physical machine that is not virtualized. Installing Linux on bare metal means installing it directly on the physical hardware, making full use of the system's resources.   
    - A virtual machine is a software-based emulation of a physical computer. It runs on top of a hypervisor, which manages the resources of the physical hardware and allocates them to multiple VMs.   
         - A Type 2 hypervisor, also known as a hosted hypervisor, runs on top of an existing operating system (OS) on the host machine. It relies on the host OS for resource management and interacts with the hardware through the host OS.
    - A cloud instance is a virtual server provided by a cloud service provider like AWS, Google Cloud, or Azure. These instances run in a data center and can be accessed remotely.
         - A Type 1 hypervisor, also known as a bare-metal hypervisor, runs directly on the physical hardware of the host machine. It has direct access to the hardware and manages the hardware resources for all the virtual machines running on it.
    
- **File System Hierarchy**: Familiarizing yourself with the Linux directory structure (e.g., /bin, /etc, /home) and the purpose of each directory.
    - Linux File System Hierarchy: Overview
The Linux file system hierarchy is organized in a tree-like structure, with the root directory / at the top. Understanding this structure is essential for navigating, managing, and administering Linux systems. Here's a breakdown of the most important directories in the Linux file system hierarchy:

        1. / (Root Directory)
The root directory is the base of the Linux file system. All other directories and files are under this directory. It's the starting point for the entire directory structure.
        2. /bin (Binary Executables)
Contains essential user command binaries (programs) needed in single-user mode and for basic system functionality. Examples include basic commands like ls, cp, mv, rm, bash, etc.
        3. /sbin (System Binaries)
Holds essential system binaries, typically used by the system administrator. These include commands required for system administration, such as fsck, reboot, shutdown, and fdisk.
        4. /etc (Configuration Files)
This directory contains all the system-wide configuration files and shell scripts used to boot and initialize the system. Examples include /etc/fstab, /etc/passwd, and /etc/hosts.
        5. /dev (Device Files)
Contains device files that represent hardware devices. For example, /dev/sda represents the first hard drive, /dev/null is a special file that discards all data written to it, and /dev/tty is the terminal device.
        6. /lib (Shared Libraries)
Stores essential shared libraries and kernel modules needed to boot the system and run the binaries in /bin and /sbin. This includes the dynamic linker/loader ld-linux.so.
        7. /lib64 (64-bit Shared Libraries)
Contains libraries for 64-bit systems, specifically for 64-bit binaries. It exists on 64-bit systems alongside /lib.
        8. /usr (User Binaries and Program Data)
The /usr directory is where user applications and files are stored. It has several important subdirectories:
/usr/bin: Non-essential user command binaries (applications like gcc, python, etc.).
/usr/sbin: Non-essential system binaries.
/usr/lib: Libraries for binaries in /usr/bin and /usr/sbin.
/usr/local: Locally compiled programs.
        9. /var (Variable Files)
Contains files that are expected to change frequently, such as logs, spool files, and temporary email files. Notable subdirectories include:
/var/log: Log files.
/var/tmp: Temporary files that need to persist between reboots.
/var/spool: Spool directories, such as print queues and mail queues.
        10. /tmp (Temporary Files)
A space for temporary files. Files here are typically deleted upon reboot. It's used by applications to store transient data.
        11. /home (Home Directories)
Contains the home directories for all the user accounts. Each user has a subdirectory within /home, like /home/username, where personal files and user-specific configurations are stored.
        12. /root (Root Home Directory)
The home directory for the root user. Unlike regular users, the root user's home directory is not under /home but directly under /.
        13. /boot (Boot Loader Files)
Contains the files needed to boot the system, including the Linux kernel, bootloader configuration files, and initial RAM disk images (e.g., vmlinuz, grub.cfg).
        14. /opt (Optional Software)
Used for the installation of additional software packages. Programs installed here are not part of the standard system installation and can include add-on applications.
        15.  
/mnt: Used as a temporary mount point for filesystems. This is often used by system administrators to manually mount filesystems.
/media: Automatically mounts removable media like CDs, DVDs, and USB drives.
        16. /proc (Process Information)
A virtual filesystem that provides a mechanism to access kernel information. Files in /proc contain information about system processes and hardware. For example, /proc/cpuinfo contains information about the CPU, and /proc/meminfo contains memory information.
        17. /sys (System Information)
Another virtual filesystem that provides information about the hardware and system. It offers more detailed information about the devices and drivers than /proc.
        18. /srv (Service Data)
Contains data for services provided by the system, such as web servers and FTP servers. For example, /srv/www might contain web server files.
        19. /run (Runtime Variable Data)
A temporary filesystem (usually mounted as tmpfs) that stores runtime data for processes since the last boot. This includes process IDs, sockets, and other transient information.
        20. /lost+found (Recovered Files)
Used by the fsck tool to store recovered files that were lost during system crashes or improper shutdowns. Each filesystem mounted on Linux will have its own lost+found directory. 
- **Basic Commands**: Mastering essential commands like `ls` (list directory contents), `cp` (copy files), `mv` (move/rename files), `rm` (remove files), `cat` (concatenate and display files).

### 2. Command-Line Proficiency

- **File System Navigation**: Using commands like `cd` (change directory), `pwd` (print working directory), and `ls`.
- **Text Editors**: Proficiency in text editors like `vi`, `vim`, and `nano` for editing configuration files and scripts.
- **Standard I/O**: Understanding how to use `stdin`, `stdout`, and `stderr`, and how to redirect output using `>`, `>>`, and `2>`.
- **Piping and Redirection**: Combining commands with `|` to pass output from one command as input to another.
- **Process Management**: Using `ps` (process status), `top` (real-time process monitoring), `kill` (terminate processes).   

clear                    Clear the terminal screen.       
man *command*            help command   
open *~/path*            opens the specified folder in the GUI  
cat **filename**         opens the specified file in the terminal    
cat > **filename**       creats a file and the editor is activated   
'>'                      redirection   
|                        translate        
^c                       to save the file and exit the editor   

pwd	                     Shows the current working directory’s path   
whoami                   Shows who are you logged in as   
sudo                     Runs a command as a superuser   

ls	                     lists a directory’s content   
ls -a                    list all files including hidden    
ls -l                    list long all the files  
ls -R                    recursively lists all the files & directories in the current folder
            
cd	                     changes the working directory to home directory    
cd ..                    previous folder   
cd ../folder./path       to change the folders, we can use the path   

mkdir	                 Creates a new directory   
rmdir                    Deletes a directory   
touch	                 Creates a new empty file   
rm	                     Deletes a file   
rm -r                    Removes directory and its content    
                    
cp *source_file destination_file*	               Copies files and directories, including their content    
cp -r *source_directory destination_directory*     Copy directories even if error occures    

mv old_name new_name                               Renames files and directories    
mv file.txt /path/to/destination/                  Moves files and directories     

df	Displays the system’s overall disk space usage   (disk - free space)     
du	Checks a file or directory’s storage consumption (disk - used space)    

head	                Displays a file’s first ten lines (default)     
head -n 4               Displays a file’s first four lines     
tail	                Prints a file’s last ten lines (default)        
tail -n 3               Prints a file’s last three lines     


diff *File1 file2*   	                        Compares two files’ content and their differences     
locate  "*.txt"                                 recursively outputs a file or folder’s location      
find *directoryName*                            recursively finds directories/files in a system’s database   
find *directoryName* -type d                    recursively finds directories in a system’s database     
find *directoryName* -type f                    recursively finds files in a system’s database    
find *directoryName* -type f -maxdepth 1        finds files in a system’s database only in specified directory   
find *directoryName* -type f -iname "*name*"    recursively finds files in a system’s database with specified name   
find *directoryName* -mmin -15                  Finds files which were modified Less that 15 mins ago    
find *directoryName* -mtime +20                 Finds files which were modified More that 15 days ago    
find *directoryName* -size +100M                Finds files which are of size More that 100 MB     
find *directoryName* -perm 777                  Finds the f/d whcih has the specified permissions    
find *directoryName* -type f -iname "*name*" -exec rm -rf {} +      
                                             -exec *command* placeholder itterative     
-i                                            non case sensitive    '-name' is Case Sensitive    
-n                                            line number     
-B *LineNumber*                               Before specified line number     
-c                                            count     

chmod u=rwx,g=rw,o=r *directoryName*         	Modifies a file’s read, write, and execute permissions
chmod 777 OR chmod 421 *FileName*               4=read(r) 2=right(w) 1=execute(x) 


chown [OPTIONS] USER[:GROUP] *FileName*	            Changes a file, directory, or symbolic link’s ownership
chown *username* *FileName*                         To change the owner of a file or directory to a specified user
chown *:groupname* *FileName*                       To change the group of a file or directory to a specified group
chown *username:groupname* *FileName*               To change both the user and group ownership
chown -R *username:groupname* *directoryName*       To change the ownership of a directory and all its contents recursively,
chown --reference=*reference_file* *target_file*    To change the owner of a f/d to match the owner of another f/d

grep *SPECIFY Phrase* *FileName*                    Searches a string within a file
grep -r *SPECIFY Phrase* *FileName*                 Searches a string within a directory

history             shows previous used commands in list with serial number
!*historyNumber*      use command from history referance number

sort *FileName* 	Reorders a file’s content
sort -r       reverse order
sort -f       case insensitive
sort -n       numerical order

jobs        	Displays a shell’s running processes with their statuses
wget *url*   	Downloads files from a URL
wget -o *NameYouWant* *url*    downloads the file and r
kill *PID*	Terminates a running process

top	         Displays running processes and the system’s resource usage and PID

file	Checks a file’s type
lsof    list open files
lsof -u *username*    list open files by User
zip *NameYouWant*.zip *FileName*	    Creates ZIP archive
unzip *FileName*.zip                    extracts a ZIP archive

nslookup *domainName*	Queries a domain’s IP address and vice versa
nslookup *IPAddress*	Queries a domain’s IP address and vice versa

netstat                	Shows the system’s network information, like routing and sockets
ifconfig
sed	                    Finds, replaces, or deletes patterns in a file

tar	Archives files without compression in a TAR format
nano, vi, and jed	Edits a file with a text editor
cat	Lists, combines, and writes a file’s content as a standard output
awk	Finds and manipulates patterns in a file

cut	Sections and prints lines from a file
tee	Prints command outputs in Terminal and a file

su	Runs programs in the current shell as another user
useradd and userdel	Creates and removes a user account
htop	Works like top but with an interactive user interface
ps	Creates a snapshot of all running processes
uname	Prints information about your machine’s kernel, name, and hardware
hostname	Shows your system’s hostname
time	Calculates commands’ execution time
systemctl	Manages system services
watch	Runs another command continuously


shutdown	Turns off or restarts the system
ping	Checks the system’s network connectivity

curl	Transmits data between servers using URLs
scp	Securely copies files or directories to another system
rsync	Synchronizes content between directories or machines
lfconfig	Displays the system’s network interfaces and their configurations
traceroute	Tracks a packet’s hops to its destination
dig	Displays DNS information, including record types
history	Lists previously run commands
man	Shows a command’s manual
echo	Prints a message as a standard output
ln	Links files or directories
alias and unalias	Sets and removes an alias for a file or command
cal	Displays a calendar in Terminal
apt-get	Manages Debian-based distros package libraries



### 3. Shell Scripting

- **Basics of Bash Scripting**: Writing and executing simple scripts, understanding shell syntax.
- **Variables and Arrays**: Using variables to store data, and arrays for lists of values.
- **Control Structures**: Implementing conditional statements (`if`, `else`) and loops (`for`, `while`).
- **Functions**: Writing reusable code blocks with functions.
- **Task Automation**: Automating routine tasks with scripts, such as backups and system monitoring.

### 4. Package Management

- **APT (Debian-based)**: Using `apt-get`, `apt-cache`, and `dpkg` for package management.
- **YUM/DNF (Red Hat-based)**: Managing packages with `yum` or `dnf`.
- **Installing, Updating, and Removing Software**: Performing software installation, updates, and removals.
- **Repository Management**: Adding, removing, and managing software repositories.

### 5. Networking Basics

- **Configuring Network Interfaces**: Setting up and managing network interfaces using `ifconfig` or `ip`.
- **IP Addressing and Subnetting**: Understanding IP addressing schemes and subnetting.
- **Network Tools**: Using tools like `ping` (check connectivity), `netstat` (network statistics), `traceroute` (trace network path).
- **DNS and Host Files**: Configuring DNS settings and managing `/etc/hosts` for local hostname resolution.
- **SSH**: Securely accessing remote machines with SSH, setting up key-based authentication, and using `scp` for secure file transfers.

### 6. Security and Permissions

- **User and Group Management**: Creating and managing users and groups with `useradd`, `groupadd`, `usermod`, and `groupmod`.
- **Permissions and Ownership**: Using `chmod` to change file permissions, `chown` to change file ownership, and understanding permission symbols (r, w, x).
- **Sudo**: Configuring and using `sudo` for elevated privileges.
- **SELinux/AppArmor**: Implementing advanced security policies with SELinux (Security-Enhanced Linux) or AppArmor.

### 7. File Systems and Storage

- **Understanding File Systems**: Familiarity with ext4, xfs, btrfs, and others.
- **Mounting and Unmounting**: Using `mount` and `umount` commands to attach and detach file systems.
- **Disk Partitions**: Managing partitions with `fdisk` or `parted`.
- **LVM (Logical Volume Manager)**: Setting up and managing LVM for flexible disk management.

### 8. System Monitoring and Performance Tuning

- **System Performance Monitoring**: Using `top`, `htop`, `iostat`, and `sar` for monitoring system performance.
- **Log Management**: Managing system logs with `journald` and `syslog`.
- **Performance Tuning**: Tweaking system parameters for optimal performance.

### 9. Automated Task Scheduling

- **Cron Jobs**: Creating and managing scheduled tasks with `cron`.
- **Crontab**: Using `crontab -e` to edit the crontab file, understanding cron syntax.
- **Anacron**: Setting up tasks with `anacron` for systems that are not continuously running.

### 10. Backup and Recovery

- **Creating Backups**: Using tools like `rsync` for incremental backups, `tar` for archiving files, and `dd` for disk cloning.
- **Disaster Recovery**: Implementing disaster recovery plans and testing backups.

### 11. Virtualization and Containers

- **Basics of Virtualization**: Understanding virtualization concepts with KVM, VirtualBox.
- **Docker Fundamentals**: Installing Docker, creating and managing Docker containers and images.
- **Dockerfile**: Writing Dockerfiles for automated builds.
- **Container Management**: Using `docker-compose` for managing multi-container applications.

### 12. Advanced Command-Line Tools

- **Text Processing**: Using `grep` for searching, `sed` for stream editing, and `awk` for pattern scanning and processing.
- **File Management**: Managing files and directories with `find`, `locate`, and `xargs`.
- **Network Configuration and Troubleshooting**: Advanced usage of `ifconfig`, `ip`, `netstat`, and `traceroute`.

### 13. Networking and Security Tools

- **SSH Configuration**: Setting up and configuring SSH, managing keys and known hosts.
- **Firewalls**: Configuring firewalls with `iptables` or `firewalld`.
- **Network Monitoring**: Using `tcpdump` and Wireshark for network analysis.
- **VPNs**: Setting up VPNs with OpenVPN or similar tools.

### 14. System Services and Daemons

- **Systemd**: Managing system services with `systemctl`, creating and managing service units.
- **Init Systems**: Understanding different init systems (systemd, SysVinit).

### 15. Kernel and System Tuning

- **Kernel Modules**: Managing kernel modules with `modprobe`, `lsmod`, and `rmmod`.
- **Kernel Parameters**: Tuning kernel parameters with `sysctl`.
- **Resource Limits**: Setting resource limits with `ulimit`.

### 16. Advanced User and Group Management

- **Advanced User Management**: Creating and managing user accounts, setting password policies.
- **Sudo Configuration**: Configuring `sudo` and managing the sudoers file with `visudo`.
- **PAM (Pluggable Authentication Modules)**: Understanding and configuring PAM for authentication.

_____________________________________________
Viewing and editing files (cat, less, more, head, tail, nano, vi/vim)


Process Management:
Viewing processes (ps, top, htop)
Managing processes (kill, pkill, killall, nice, renice)

File and Disk Management:
Disk usage and partition management (df, du, fdisk, lsblk)
File compression and archiving (tar, gzip, gunzip, zip, unzip)

System Monitoring and Performance:
Monitoring system performance (vmstat, iostat, free)
Analyzing logs (/var/log, journalctl)

Security:
Understanding and using iptables/firewalld
Managing user permissions and sudo access

Terminal Shortcuts

Basic Navigation
Ctrl + U:                   Clear the line 
Ctrl + K:                   Clear the line after the cursor (delete everything to the right of the cursor).
Ctrl + W:                   Delete the word before the cursor.
Ctrl + Y:                   Paste the last cut text that was removed by Ctrl + U, Ctrl + K, or Ctrl + W.

Process Management
Ctrl + C:                   Kill the current process.
Ctrl + Z:                   Suspend the current process (you can resume it with the fg command).

History Navigation
Ctrl + R:                   Search through your command history as you type.
↑ (Up Arrow):               Scroll through previous commands in your history.
↓ (Down Arrow):             Scroll through more recent commands in your history.

Editing
Option + ←:                 Move the cursor backward by one word.
Option + →:                 Move the cursor forward by one word.
Ctrl + T:                   Swap the last two characters before the cursor (useful for correcting mistyped characters).


