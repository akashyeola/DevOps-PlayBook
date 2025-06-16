
---

# Linux: A Comprehensive Guide for DevOps

---

## 1. Linux Fundamentals

### 1.1 Overview of Linux - Distributions

* **Linux Kernel:** The fundamental **core** of the operating system. It's the central component that directly interacts with the hardware, managing essential resources like CPU, memory, and I/O devices. It provides the **low-level communication layer** that allows software to run efficiently on the hardware.
* **GNU Tools:** A collection of **free software**, including compilers (**GCC**), libraries (**glibc**), shell programs (**Bash**), and utilities (**ls**, **cp**, **mv**, **grep**). These tools, combined with the Linux kernel, form a complete operating system (often referred to as GNU/Linux). They provide the essential **user-space environment** for interacting with the system.
* **Package Management:** A system to streamline the installation, updating, configuration, and removal of software packages.
    * **Debian-based** (e.g., Ubuntu, Debian, Kali Linux): Primarily uses **APT (Advanced Package Tool)**. Commands like `apt update`, `apt install`, `apt remove` are common.
    * **Red Hat-based** (e.g., CentOS, Fedora, RHEL): Historically used **YUM (Yellowdog Updater, Modified)**. Modern versions have largely transitioned to **DNF (Dandified YUM)**, offering improved performance and dependency resolution. Commands like `dnf install`, `dnf update`, `dnf remove`.
    * **Other Notable Package Managers:**
        * **Pacman:** Used by Arch Linux.
        * **Zypper:** Used by openSUSE.
* **Desktop Environments (DEs):** Provide a **graphical user interface (GUI)** for users, making Linux accessible to non-technical users. They include a window manager, file manager, and a set of utilities and applications.
    * **GNOME:** A popular, modern, and user-friendly desktop environment.
    * **KDE Plasma:** Highly customizable and feature-rich.
    * **XFCE:** Lightweight and resource-efficient, ideal for older hardware or minimal installations.
    * **Others:** LXDE, MATE, Cinnamon.
* **Customization:** Linux distributions are **highly flexible**. Users can choose their kernel, GNU tools, package manager, desktop environment, and even compile software from source, allowing for a **tailored operating system experience** optimized for specific needs.

### 1.2 Linux Installation and Setup

Installing Linux involves deploying the operating system on various computing environments.

* **Bare Metal:** Installing Linux directly onto a **physical computer's hardware**.
    * **Characteristics:** Provides **direct access** to all hardware resources, offering maximum performance. Ideal for servers, workstations, or dedicated systems where virtualization overhead is undesirable.
    * **Process:** Typically involves booting from a USB drive or DVD, partitioning the disk, and following an installer wizard.
* **Virtual Machines (VMs):** **Software-based emulations** of physical computers, running on top of a hypervisor.
    * **Characteristics:** Offer isolation, portability, and efficient resource utilization by allowing multiple operating systems to run concurrently on a single physical machine.
    * **Hypervisors:**
        * **Type 1 (Bare-Metal/Native Hypervisor):** Runs directly on the physical hardware, managing resources and allocating them to VMs. It has direct access to hardware, leading to better performance.
            * **Examples:** VMware ESXi, Microsoft Hyper-V, **KVM (Kernel-based Virtual Machine** - integrated into the Linux kernel).
        * **Type 2 (Hosted Hypervisor):** Runs as an application on top of an existing host operating system. It relies on the host OS for hardware interaction.
            * **Examples:** VirtualBox, VMware Workstation/Fusion.
* **Cloud Instances:** Virtual servers provided by **cloud service providers**.
    * **Characteristics:** Elastic, scalable, and accessible remotely. They are essentially VMs hosted in a provider's data center, managed through web consoles or APIs.
    * **Examples:** **Amazon EC2 (AWS)**, **Google Compute Engine (Google Cloud)**, **Azure Virtual Machines (Microsoft Azure)**.

### 1.3 File System Hierarchy (FHS)

The Linux file system is organized in a strict, logical, **tree-like structure**, starting from the **root directory `/`**. Understanding this hierarchy is critical for navigating, managing, and administering Linux systems effectively.

1.  **`/ (Root Directory):`** The **base** of the entire Linux file system. All other directories and files branch off from here.
2.  **`/bin (Binary Executables):`** Contains essential **user command binaries** (programs) required for basic system functionality and single-user mode.
    * **Examples:** `ls`, `cp`, `mv`, `rm`, `bash`.
3.  **`/sbin (System Binaries):`** Holds essential **system binaries**, primarily used by the system administrator for system administration tasks.
    * **Examples:** `fsck`, `reboot`, `shutdown`, `fdisk`.
4.  **`/etc (Configuration Files):`** Contains **system-wide configuration files** and shell scripts used to boot and initialize the system.
    * **Examples:** `/etc/fstab` (filesystem table), `/etc/passwd` (user accounts), `/etc/hosts` (hostname resolution).
5.  **`/dev (Device Files):`** Contains special **device files** that represent hardware devices. These are not typical files but interfaces to devices.
    * **Examples:** `/dev/sda` (first hard drive), `/dev/null` (null device), `/dev/tty` (current terminal).
6.  **`/lib (Shared Libraries):`** Stores essential shared libraries and kernel modules required to boot the system and run binaries in `/bin` and `/sbin`.
    * **Includes:** The dynamic linker/loader `ld-linux.so`.
7.  **`/lib64 (64-bit Shared Libraries):`** On 64-bit systems, this directory holds libraries specifically for 64-bit binaries.
8.  **`/usr (User Binaries and Program Data):`** Contains read-only user applications, libraries, and documentation. This is often the largest directory on a Linux system.
    * **`/usr/bin:`** Non-essential user command binaries (applications).
        * **Examples:** `gcc`, `python`, `firefox`.
    * **`/usr/sbin:`** Non-essential system binaries.
    * **`/usr/lib:`** Libraries for binaries in `/usr/bin` and `/usr/sbin`.
    * **`/usr/local:`** Used for software compiled and installed locally by the system administrator, outside of the distribution's package management.
        * **Examples:** `/usr/local/bin`, `/usr/local/lib`.
9.  **`/var (Variable Files):`** Contains files that are expected to change frequently during normal operation, such as logs, spool files, and temporary email files.
    * **`/var/log:`** System and application log files.
    * **`/var/tmp:`** Temporary files that are preserved between reboots (unlike `/tmp`).
    * **`/var/spool:`** Spool directories for print queues, mail queues, cron jobs.
10. **`/tmp (Temporary Files):`** A temporary storage space for files. Contents are usually deleted on system reboot. Used by applications to store transient data.
11. **`/home (Home Directories):`** Contains the home directories for all regular user accounts. Each user has a subdirectory (`/home/username`) where personal files, documents, and user-specific configurations are stored.
12. **`/root (Root Home Directory):`** The dedicated home directory for the `root` (superuser) account. It's separate from `/home` for security and administrative convenience.
13. **`/boot (Boot Loader Files):`** Contains files necessary to boot the system, including the Linux kernel, bootloader (e.g., GRUB) configuration files, and initial RAM disk images.
    * **Examples:** `vmlinuz` (kernel), `initrd.img` (initial RAM disk), `grub.cfg`.
14. **`/opt (Optional Software):`** Used for the installation of large, optional software packages that are not part of the standard system installation. Often used by third-party vendors.
15. **`/mnt (Mount Point for Temporary Filesystems):`** A conventional mount point for manually mounting temporary filesystems (e.g., network shares, external hard drives, or temporary ISOs).
    * **Example:** `mount /dev/sdb1 /mnt/data`.
    **`/media (Mount Point for Removable Media):`** Used for automatically mounting removable media devices like CDs, DVDs, USB drives, and external hard drives when they are connected.
16. **`/proc (Process Information File System):`** A **virtual filesystem** (resides in memory, not disk) that provides a mechanism to access kernel information and process status. Files here are dynamically generated.
    * **Examples:** `/proc/cpuinfo` (CPU details), `/proc/meminfo` (memory details), `/proc/PID` (information about specific processes).
17. **`/sys (System Information File System):`** Another **virtual filesystem** that provides more detailed, structured information about hardware devices, kernel modules, and system parameters than `/proc`. It's part of the `sysfs` filesystem.
18. **`/srv (Service Data):`** Contains data for services provided by the system.
    * **Examples:** `/srv/www` (web server files), `/srv/ftp` (FTP server files).
19. **`/run (Runtime Variable Data):`** A temporary filesystem (typically `tmpfs`) that stores volatile runtime data for processes since the last boot. Its contents are recreated on reboot.
    * **Examples:** Process IDs (PIDs), sockets, transient information.
20. **`/lost+found (Recovered Files):`** Each filesystem mounted on Linux has its own `lost+found` directory. It's used by the `fsck` (filesystem check) tool to store recovered files that were lost during system crashes or improper shutdowns.

---

## 2. Command-Line Proficiency

Mastering the Linux command line (CLI) is fundamental for DevOps, enabling efficient interaction with the system, automation, and troubleshooting.

### 2.1 Basic Commands & File System Navigation

* `pwd`: **P**rint **W**orking **D**irectory. Shows the **absolute path** of your current location in the file system.
    * **Example:** `pwd` (Output: `/home/youruser`)
* `ls`: **L**i**s**t directory contents. Displays files and directories in the current or specified directory.
    * `ls`: Lists files and directories in the current directory.
    * `ls -a`: Lists **all** files, including hidden files (those starting with a `.`).
    * `ls -l`: Provides a **long listing format**, showing detailed information (permissions, owner, group, size, modification date).
    * `ls -lh`: Same as `-l` but with **human-readable** sizes (e.g., `1.2K`, `5.6M`).
    * `ls -R`: **Recursively** lists files and directories in the current folder and its subdirectories.
    * **Example:** `ls -la /etc/nginx`
* `cd`: **C**hange **D**irectory. Navigates between directories.
    * `cd`: Changes to the current user's **home directory**.
    * `cd ..`: Moves up one level to the **parent directory**.
    * `cd /path/to/directory`: Changes to an **absolute path**.
    * `cd folder/subfolder`: Changes to a **relative path**.
    * `cd -`: Switches back to the **previous working directory**.
    * **Example:** `cd /var/log` then `cd -`
* `mkdir`: **M**a**k**e **Dir**ectory. Creates a new directory.
    * `mkdir my_new_folder`
    * `mkdir -p project/src/main`: Creates **parent directories** if they don't exist.
* `rmdir`: **R**e**m**ove **Dir**ectory. Deletes an **empty** directory.
    * `rmdir empty_folder`
* `touch`: Creates a new **empty file** or updates the timestamp of an existing file.
    * `touch new_document.txt`
* `cp`: **C**o**p**y files and directories.
    * `cp source_file destination_file`: Copies a file.
    * `cp -r source_directory destination_directory`: **Recursively** copies a directory and its contents.
    * `cp -u source_file destination_file`: Copies only when the source file is newer than the destination or the destination does not exist (`update`).
    * `cp -p source_file destination_file`: Preserves attributes like permissions, ownership, and timestamps.
    * **Example:** `cp /etc/hosts ~/my_hosts_backup`
* `mv`: **M**o**v**e or **R**e**n**ame files and directories.
    * `mv old_name new_name`: Renames a file or directory **within the same location**.
    * `mv file.txt /path/to/destination/`: Moves a file or directory to a different location.
    * **Example:** `mv my_script.sh scripts/`
* `rm`: **R**e**m**ove files or directories. **Use with caution!**
    * `rm my_file.txt`: Deletes a file.
    * `rm -r my_directory`: **Recursively** removes a directory and its contents (dangerous!).
    * `rm -f my_file.txt`: **Force** removal, ignoring nonexistent files and never prompting.
    * `rm -rf dangerous_folder/`: **Force recursive removal** – common but extremely dangerous command.
    * `rm -i file_to_delete`: Prompts for confirmation before each removal (`interactive`).
* `cat`: Concatenate and display files. Used to view file content or create small files.
    * `cat filename.txt`: Displays the content of the file.
    * `cat > newfile.txt`: Creates a new file. Type content, then press **Ctrl+D** to save and exit (**EOF** - End Of File).
    * `cat file1.txt file2.txt > combined.txt`: Concatenates `file1.txt` and `file2.txt` into `combined.txt`.

### 2.2 Text Editors

Essential for editing configuration files, scripts, and code directly in the terminal.

* `nano`: A **simple, user-friendly**, and easy-to-use text editor. Ideal for beginners.
    * `nano filename.txt`: Opens `filename.txt` for editing.
    * **Common Shortcuts (displayed at the bottom):**
        * `Ctrl+O`: Write Out (save).
        * `Ctrl+X`: Exit.
        * `Ctrl+W`: Where Is (search).
* `vi` / `vim`: A **powerful, highly configurable**, and ubiquitous text editor. It has a steep learning curve but is incredibly efficient once mastered. `vim` (Vi IMproved) is the modern version.
    * `vim filename.txt`: Opens `filename.txt` for editing.
    * **Modes:**
        * **Normal Mode (Command Mode):** Default mode for navigation and executing commands (e.g., delete, copy, paste).
        * **Insert Mode:** For typing text. Enter by pressing `i` (insert), `a` (append), `o` (open new line below).
        * **Visual Mode:** For selecting text. Enter by pressing `v`.
        * **Command-Line Mode:** For executing commands like save, quit, search. Enter by pressing `:`.
    * **Basic Commands:**
        * `i`: Enter Insert mode.
        * `Esc`: Return to Normal mode.
        * `:w`: Save the file.
        * `:q`: Quit (only if no changes or changes saved).
        * `:wq` or `ZZ`: Save and quit.
        * `:q!`: Quit without saving (force).
        * `dd`: Delete the current line.
        * `yy`: Yank (copy) the current line.
        * `p`: Paste after the cursor.

### 2.3 Standard I/O, Piping, and Redirection

Linux commands operate using three standard streams:

* **`stdin` (Standard Input - 0):** Where a command reads its input from (default: keyboard).
* **`stdout` (Standard Output - 1):** Where a command writes its normal output (default: terminal screen).
* **`stderr` (Standard Error - 2):** Where a command writes error messages (default: terminal screen).

#### Redirection: Changing where input/output goes

* `>`: **Redirects `stdout` to a file.** **Overwrites** the file if it exists.
    * **Example:** `ls -l > file_list.txt` (sends the `ls` output to `file_list.txt`, overwriting it).
* `>>`: **Appends `stdout` to a file.** Creates the file if it doesn't exist.
    * **Example:** `echo "Another line" >> file_list.txt` (adds "Another line" to the end of `file_list.txt`).
* `<`: **Redirects `stdin` from a file.**
    * **Example:** `sort < unsorted.txt` (takes `unsorted.txt` as input for the `sort` command).
* `2>`: **Redirects `stderr` to a file.** Overwrites.
    * **Example:** `find / -name non_existent_file 2> errors.log` (sends error messages from `find` to `errors.log`).
* `&>` or `>&`: **Redirects both `stdout` and `stderr` to a file.**
    * **Example:** `command_that_might_fail &> output_and_errors.log`

#### Piping (`|`): Connecting command outputs to inputs

* The output (`stdout`) of one command becomes the input (`stdin`) of the next command. This allows building complex operations by chaining simple commands.
    * **Example:** `ls -l /var/log | grep ".log"` (lists all files in `/var/log` and then filters that list to show only lines containing ".log").
    * **Example:** `cat access.log | grep "404" | sort | uniq -c` (views access logs, filters for "404" errors, sorts them, and then counts unique occurrences).

### 2.4 Process Management

Managing processes is crucial for system administrators and DevOps engineers to monitor system health and control running applications.

* `ps`: **P**rocess **S**tatus. Displays a snapshot of currently running processes.
    * `ps aux`: Shows all processes for all users (`a`), including processes not attached to a terminal (`x`), with detailed format (`u`). Common for a comprehensive view.
    * `ps -ef`: Another common option to see all processes in full listing format, including parent PID (`p` for process, `s` for status).
    * `ps -u <username>`: Shows processes owned by a specific user.
    * **Example:** `ps aux | grep nginx` (finds running Nginx processes).
* `top`: Displays processes in **real-time**, showing dynamic updates of CPU, memory, and process usage.
    * **Interactive commands within `top`:**
        * `q`: Quit.
        * `k`: Kill a process (prompts for PID).
        * `M`: Sort by Memory usage.
        * `P`: Sort by CPU usage.
    * **Example:** Simply type `top`
* `htop`: An interactive, more user-friendly process viewer with a colored interface and additional features compared to `top`. (Often needs to be installed: `sudo apt install htop` or `sudo dnf install htop`).
* `kill`: Terminates a process by sending a signal. Requires the Process ID (PID).
    * `kill <PID>`: Sends the default `TERM` (terminate) signal (15), allowing the process to gracefully shut down.
    * `kill -9 <PID>`: Sends the `KILL` signal (9), forcefully terminating the process. Use only when `kill <PID>` doesn't work, as it doesn't allow for graceful shutdown.
    * **Example:** `kill 12345` or `kill -9 12345`
* `pkill`: Kills processes by name or other attributes.
    * `pkill firefox`: Kills all processes whose name matches "firefox".
* `killall`: Kills processes by name.
    * `killall apache2`: Kills all `apache2` processes.
* `jobs`: Displays a shell's running processes that were stopped or are running in the background.
    * `Ctrl+Z`: Suspends the current foreground process (puts it in the background, stopped state).
    * `bg`: Resumes a suspended process in the background.
    * `fg`: Brings a background process to the foreground.

### 2.5 Disk Usage and Information

* `df`: **D**isk **F**ree space. Displays the system's overall disk space usage, showing mounted filesystems, their total size, used space, available space, and percentage used.
    * `df -h`: Shows sizes in **human-readable** format (e.g., `G`, `M`).
    * `df -Th`: Shows filesystem type (`-T`) in addition to human-readable sizes.
    * **Example:** `df -h /home` (checks free space on the `/home` partition).
* `du`: **D**isk **U**sage. Estimates file or directory space usage.
    * `du -h`: Shows sizes in **human-readable** format.
    * `du -sh`: **Summarizes** the total size of a directory (or file) in human-readable format.
    * `du -ah . | sort -rh`: Lists all files and directories in the current location, shows human-readable sizes, then sorts them by size in reverse order (`r`) and human-readable (`h`). Useful for finding large files.
    * **Example:** `du -sh /var/log` (shows the total size of the `/var/log` directory).

### 2.6 File Content Viewing and Manipulation

* `head`: Displays the **first ten lines** (by default) of a file.
    * `head filename.txt`
    * `head -n 4 filename.txt`: Displays the first **four** lines.
* `tail`: Displays the **last ten lines** (by default) of a file.
    * `tail filename.txt`
    * `tail -n 3 filename.txt`: Displays the last **three** lines.
    * `tail -f filename.log`: **"Follows"** the file, continuously displaying new lines as they are added (excellent for monitoring live log files). Use `Ctrl+C` to exit.
* `less`: A powerful pager that allows you to view file content **one screen at a time**, scroll forward/backward, and search. Unlike `cat`, it's suitable for large files as it doesn't load the entire file into memory.
    * `less filename.txt`
    * **Navigation within `less`:**
        * `Spacebar` or `f`: Page down.
        * `b`: Page up.
        * `/pattern`: Search forward for `pattern`.
        * `n`: Go to next match.
        * `N`: Go to previous match.
        * `g`: Go to beginning of file.
        * `G`: Go to end of file.
        * `q`: Quit.
* `more`: Similar to `less` but with fewer features (older, simpler pager).
* `diff`: **Diff**erence. Compares two files line by line and highlights their differences. Useful for tracking changes in configuration files or code.
    * `diff file1.txt file2.txt`
* `sort`: Reorders a file's content line by line.
    * `sort filename.txt`: Sorts alphabetically.
    * `sort -r filename.txt`: Sorts in **reverse** order.
    * `sort -f filename.txt`: Sorts **case-insensitively**.
    * `sort -n filename.txt`: Sorts **numerically**.
    * **Example:** `cat numbers.txt | sort -n`

### 2.7 File Search and Location

* `locate "pattern"`: Recursively outputs a file or folder’s location based on a **pre-built database**. Very fast, but the database might not be up-to-date.
    * **Update database:** `sudo updatedb`
    * `locate "*.txt"`: Finds all `.txt` files.
* `find`: Recursively finds files and directories based on extensive criteria. Slower than `locate` but always up-to-date as it traverses the file system directly.
    * `find . -name "*.log"`: Finds all files ending with `.log` in the current directory (`.`) and its subdirectories. `-name` is case-sensitive.
    * `find /etc -iname "nginx*"`: Finds files/directories starting with "nginx" in `/etc`, **case-insensitively** (`-iname`).
    * `find /var/log -type f`: Finds only **files** (`f`) in `/var/log`.
    * `find . -type d`: Finds only **directories** (`d`).
    * `find /var/tmp -type f -maxdepth 1`: Finds files in `/var/tmp` but only up to **one level deep** (i.e., not in subdirectories).
    * `find /home/user -mmin -15`: Finds files modified **less than 15 minutes ago**.
    * `find /home/user -mtime +20`: Finds files modified **more than 20 days ago**.
    * `find /data -size +100M`: Finds files larger than **100 MB**.
    * `find /app -perm 777`: Finds files/directories with **777 permissions**.
    * `find . -type f -name "*.tmp" -exec rm -rf {} +`: Finds all `.tmp` files and executes `rm -rf` on them. `{}` is a placeholder for the found files, and `+` executes `rm` once for multiple found files (more efficient than `\;` which executes `rm` for each file).
    * `find . -empty`: Finds empty files or directories.

### 2.8 Permissions and Ownership Management

Linux uses a robust permission system to control access to files and directories.

* `chmod`: **Ch**ange **Mod**e. Modifies a file's read, write, and execute permissions.
    * **Symbolic Mode:**
        * `u`: User (owner)
        * `g`: Group
        * `o`: Others
        * `a`: All (u, g, o)
        * `+`: Add permission
        * `-`: Remove permission
        * `=`: Set exact permission
        * `r`: Read (4)
        * `w`: Write (2)
        * `x`: Execute (1)
        * **Example:** `chmod u=rwx,g=rw,o=r filename.txt`: Sets owner to rwx, group to rw, others to r.
        * **Example:** `chmod +x my_script.sh`: Makes `my_script.sh` executable for everyone.
    * **Octal (Numeric) Mode:** Each permission (r, w, x) has a numeric value.
        * `r = 4`
        * `w = 2`
        * `x = 1`
        * Combine values for each category (owner, group, others).
        * **Example:** `chmod 777 filename` (rwx for owner, group, others).
        * **Example:** `chmod 644 filename` (rw- for owner, r-- for group, r-- for others).
        * `chmod 755 directory/`: Standard permissions for directories (rwx for owner, rx for group/others).
    * `chmod -R 755 my_app/`: **Recursively** changes permissions for `my_app` and its contents.
* `chown`: **Ch**ange **Own**er. Changes a file, directory, or symbolic link's **ownership**.
    * `chown username filename`: Changes the **user owner** of a file to `username`.
    * `chown :groupname filename`: Changes the **group owner** of a file to `groupname`. (Note the colon before groupname).
    * `chown username:groupname filename`: Changes **both** user and group ownership.
    * `chown -R username:groupname directory/`: Recursively changes ownership of a directory and its contents.
    * `chown --reference=ref_file target_file`: Changes the owner/group of `target_file` to match `ref_file`.
* `chgrp`: **Ch**ange **Gr**ou**p**. Changes the group ownership of a file/directory. (Functionally similar to `chown :groupname`, but a dedicated command).
    * `chgrp new_group file.txt`

### 2.9 Other Useful Commands

* `clear`: Clears the terminal screen.
* `man <command>`: Displays the **manual page** (documentation) for a command. Essential for understanding command options and usage.
    * **Example:** `man ls`, `man find`. Press `q` to quit.
* `whoami`: Displays the effective username of the current user.
* `sudo`: **S**uper**u**ser **do**. Executes a command with elevated privileges (as root). Requires your password.
    * **Example:** `sudo apt update`, `sudo systemctl restart apache2`.
* `grep`: **G**lobal **R**egular **E**xpression **P**rint. Searches for a specified pattern (string or regular expression) within files.
    * `grep "SPECIFY Phrase" filename.txt`: Searches for "SPECIFY Phrase" in `filename.txt`.
    * `grep -i "phrase" filename.txt`: Searches **case-insensitively**.
    * `grep -v "phrase" filename.txt`: **Inverts** the match, showing lines that *do not* contain the phrase.
    * `grep -r "error" /var/log`: Recursively searches for "error" in all files within `/var/log` and its subdirectories.
    * `grep -l "pattern" *`: Prints only the **names of files** that contain the pattern.
    * `grep -n "pattern" filename.txt`: Shows **line numbers** where matches are found.
    * `grep -c "pattern" filename.txt`: Shows the **count** of matching lines.
    * `grep -B <num> "pattern" filename.txt`: Shows `num` lines **before** the match.
    * `grep -A <num> "pattern" filename.txt`: Shows `num` lines **after** the match.
    * `grep -C <num> "pattern" filename.txt`: Shows `num` lines **context** (before and after) the match.
* `history`: Displays a list of previously used commands with serial numbers.
    * `history`
    * `!N`: Re-executes the command from history with serial number `N`.
    * `!string`: Re-executes the most recent command starting with `string`.
* `wget <url>`: **W**eb **Get**. Downloads files from a URL.
    * `wget https://example.com/file.zip`: Downloads `file.zip`.
    * `wget -O my_download.zip https://example.com/file.zip`: Downloads and saves it as `my_download.zip`.
    * `wget -r -l 2 https://example.com/docs/`: Recursively downloads content up to 2 levels deep.
* `curl <url>`: **C**lient **URL**. A versatile tool for transferring data with URLs, supporting various protocols (HTTP, HTTPS, FTP, etc.). Often used for API interactions, checking website headers, etc.
    * `curl https://example.com`: Displays the HTML content of the URL.
    * `curl -O https://example.com/largefile.tar.gz`: Saves the file with its remote name.
    * `curl -I https://example.com`: Shows only HTTP headers.
    * `curl -X POST -d "key=value" https://api.example.com/data`: Sends a POST request with data.
* `file <filename>`: Checks and displays a file's type.
    * `file my_script.sh` (Output: `my_script.sh: Bourne-again shell script, UTF-8 Unicode text`)
    * `file /bin/bash` (Output: `/bin/bash: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=..., stripped`)
* `lsof`: **L**i**s**t **O**pen **F**iles. Lists all open files and the processes that opened them. Useful for troubleshooting "resource busy" errors.
    * `lsof -i :80`: Lists processes listening on port 80.
    * `lsof -u username`: Lists files opened by a specific user.
* `zip` / `unzip`: For creating and extracting ZIP archives.
    * `zip myarchive.zip file1.txt folder/`: Creates `myarchive.zip` containing `file1.txt` and `folder/`.
    * `unzip myarchive.zip`: Extracts contents of `myarchive.zip`.
* `tar`: **T**ape **Ar**chiver. Used for archiving and compressing files. Extremely common for packaging software and backups.
    * `tar -cvf archive.tar dir/`: **C**reates a `v`erbose `f`ile archive of `dir/`.
    * `tar -xvf archive.tar`: E**x**tracts a `v`erbose `f`ile archive.
    * `tar -czvf archive.tar.gz dir/`: Creates a g**z**ipped tar archive (tarball).
    * `tar -xzvf archive.tar.gz`: Extracts a gzipped tar archive.
    * `tar -cjvf archive.tar.bz2 dir/`: Creates a b**j**ipped2 tar archive.
    * `tar -xJvf archive.tar.xz`: Extracts an **x**z compressed tar archive.
    * `tar -tf archive.tar.gz`: **T**ests/lists the content of an archive without extracting.
* `nslookup <domain>`: Queries a domain's IP address and vice versa (DNS lookup).
    * `nslookup google.com`
    * `nslookup 8.8.8.8`
* `dig`: More advanced DNS lookup utility. Provides more detailed information than `nslookup`.
    * `dig google.com`
    * `dig google.com MX`: Queries MX (Mail Exchange) records.
* `netstat`: Displays network connections, routing tables, interface statistics, etc. (Often deprecated in favor of `ss` for connections, and `ip route` for routing).
    * `netstat -tuln`: Shows **t**cp, **u**dp **l**istening **n**umeric ports.
* `ip`: Modern command to show/manipulate routing, devices, policy routing and tunnels. Replaces `ifconfig`, `route`, `arp`, etc.
    * `ip addr show`: Shows network interface addresses (similar to `ifconfig`).
    * `ip route show`: Shows the routing table.
    * `ip link show`: Shows network device status.
* `hostname`: Displays or sets the system's hostname.
* `uname`: Prints information about your machine’s kernel, name, and hardware.
    * `uname -a`: Shows all system information.
* `time <command>`: Measures the execution time of a command.
    * `time ls -R /`
* `systemctl`: Manages system services and units under Systemd (the most common init system today).
    * `systemctl status apache2`: Checks the status of the Apache web server service.
    * `systemctl start nginx`: Starts the Nginx service.
    * `systemctl stop postgresql`: Stops the PostgreSQL service.
    * `systemctl restart sshd`: Restarts the SSH daemon.
    * `systemctl enable apache2`: Ensures Apache starts on boot.
    * `systemctl disable apache2`: Prevents Apache from starting on boot.
* `shutdown`: Turns off or restarts the system.
    * `shutdown -h now`: Shuts down immediately.
    * `shutdown -r now`: Restarts immediately.
    * `shutdown -h +5 "System will go down for maintenance"`: Shuts down in 5 minutes with a message.
* `ping <host>`: Checks network connectivity to a host by sending ICMP echo requests.
    * `ping google.com`
    * `ping -c 4 192.168.1.1`: Sends only 4 packets.
* `scp`: **S**ecure **C**o**p**y. Securely copies files or directories between hosts on a network using SSH.
    * `scp local_file.txt user@remote_host:/path/to/destination/`: Copies `local_file.txt` to a remote host.
    * `scp user@remote_host:/path/to/remote_file.txt .`: Copies `remote_file.txt` to the current local directory.
    * `scp -r local_dir/ user@remote_host:/path/`: Recursively copies a local directory.
* `rsync`: **R**emote **Sync**hronization. Synchronizes files and directories between locations (local or remote). Efficient as it only transfers changed parts of files.
    * `rsync -avz /source/dir/ /destination/dir/`: **A**rchive mode (preserves permissions, timestamps, etc.), `v`erbose, `z`compress during transfer.
    * `rsync -avz /local/dir/ user@remote_host:/remote/dir/`
    * `rsync -avz --delete /source/dir/ /destination/dir/`: Deletes files in destination that are not in source. **Use with extreme caution!**
* `traceroute <host>`: Traces the path (hops) a packet takes to its destination, showing each router it passes through.
* `echo`: Prints a message or variable's value as standard output.
    * `echo "Hello, Linux!"`
    * `echo $PATH` (shows the value of the PATH environment variable).
* `ln`: **L**i**n**k. Creates links (shortcuts) to files or directories.
    * `ln -s /path/to/original /path/to/symlink`: Creates a **symbolic link** (soft link). The original file/directory must exist. Deleting the original breaks the link. Most common type of link.
    * `ln /path/to/original /path/to/hardlink`: Creates a **hard link**. Only works for files on the same filesystem. Deleting the original doesn't break the link, as it's another name for the same data.
* `alias <name>='command'`: Creates a shortcut (alias) for a command.
    * `alias ll='ls -lh'`
    * `unalias ll`: Removes the alias.
    * Aliases are usually stored in `~/.bashrc` or `~/.bash_profile` for persistence.
* `cal`: Displays a calendar in the terminal.
* `sed`: **S**tream **ED**itor. A powerful command-line text editor for transforming text, typically used for find and replace operations. Works on streams (like piped input) or files.
    * `sed 's/old_text/new_text/' filename.txt`: Replaces the **first** occurrence of `old_text` with `new_text` on each line.
    * `sed 's/old_text/new_text/g' filename.txt`: Replaces **all** occurrences (`g` for global).
    * `sed '/pattern_to_delete/d' filename.txt`: Deletes lines matching `pattern_to_delete`.
    * **Example:** `cat apache.log | sed 's/HTTP\/1\.1" 200/HTTP\/1\.1" OK/'`
* `awk`: A powerful pattern scanning and processing language. Excellent for parsing and manipulating structured text files (like logs or CSVs).
    * `awk '{print $1, $3}' filename.txt`: Prints the first and third fields (columns) of each line.
    * `awk '/pattern/ {print}' filename.txt`: Prints lines containing `pattern`.
    * `awk -F':' '{print $1}' /etc/passwd`: Sets field separator to `:` and prints the first field (usernames).
* `cut`: Sections and prints lines from a file based on delimiters or character positions.
    * `cut -d':' -f1,7 /etc/passwd`: Uses `:` as a delimiter (`-d`), and prints fields 1 and 7 (`-f`).
    * `cut -c 1-5 filename.txt`: Prints characters 1 through 5 of each line.
* `tee`: Reads standard input and writes it to both standard output (terminal) and one or more files. Useful for capturing command output while also seeing it on screen.
    * `ls -l | tee file_list.txt`: Displays `ls -l` output on screen and saves it to `file_list.txt`.
* `su`: **S**ubstitute **U**ser (or **S**witch **U**ser). Runs programs in the current shell as another user (default: root).
    * `su - username`: Switches to `username`'s environment (including their home directory and environment variables).
    * `su`: Switches to root user.
* `useradd` / `userdel`: Creates and removes user accounts.
    * `sudo useradd newuser`: Creates a new user.
    * `sudo passwd newuser`: Sets password for `newuser`.
    * `sudo userdel -r olduser`: Deletes `olduser` and their home directory (`-r`).
* `groupadd` / `groupdel`: Creates and removes groups.
    * `sudo groupadd developers`
    * `sudo groupdel oldgroup`
* `usermod`: Modifies user account properties.
    * `sudo usermod -aG sudo newuser`: Adds `newuser` to the `sudo` group.
    * `sudo usermod -l new_name old_name`: Changes username.
* `watch <command>`: Executes another command repeatedly, displaying its output in full screen.
    * `watch -n 1 'ls -l /var/log/nginx'` (updates the listing every 1 second).

---

## 3. Shell Scripting (Bash)

Shell scripting allows you to automate repetitive tasks, execute sequences of commands, and build complex system operations. Bash (Bourne-Again SHell) is the most common shell for scripting in Linux.

### 3.1 Basics of Bash Scripting

* **Shebang Line:** The first line of a script, `#!/bin/bash` (or `#!/bin/sh`), tells the system which interpreter to use for executing the script.
    * **Example:** `#!/bin/bash`
* **Executing a Script:**
    1.  Make it executable: `chmod +x my_script.sh`
    2.  Run it: `./my_script.sh` (if in current directory) or `/path/to/my_script.sh`
* **Comments:** Lines starting with `#` are comments and are ignored by the interpreter.
    * **Example:** `# This is a comment`
* **Basic Script Structure:**

    ```bash
    #!/bin/bash

    # A simple script to greet the user
    echo "Hello, Linux user!"
    ```

### 3.2 Variables and Arrays

* **Variables:** Used to store data. No specific data types; everything is a string.
    * **Defining:** `VAR_NAME="value"` (no spaces around `=`).
    * **Accessing:** `${VAR_NAME}` or `$VAR_NAME`. Use curly braces for clarity or when concatenating.
    * **Example:**
        ```bash
        #!/bin/bash
        NAME="Alice"
        AGE=30
        echo "My name is $NAME and I am $AGE years old."
        echo "The user is ${USER}." # Accessing an environment variable
        ```
* **Positional Parameters:** Special variables `$0`, `$1`, `$2`, ... `$n` represent script name and arguments passed to it.
    * `$0`: Name of the script itself.
    * `$1`: First argument.
    * `$2`: Second argument, and so on.
    * `$#`: Number of arguments.
    * `$@`: All arguments as separate strings.
    * `$*`: All arguments as a single string.
    * **Example:**
        ```bash
        #!/bin/bash
        echo "Script name: $0"
        echo "First argument: $1"
        echo "Total arguments: $#"
        ```
* **Arrays:** Used to store a list of values.
    * **Defining:** `ARRAY_NAME=(value1 value2 "value with spaces")`
    * **Accessing all elements:** `${ARRAY_NAME[@]}`
    * **Accessing specific element:** `${ARRAY_NAME[index]}` (indices start from 0).
    * **Number of elements:** `${#ARRAY_NAME[@]}`
    * **Example:**
        ```bash
        #!/bin/bash
        FRUITS=("Apple" "Banana" "Cherry")
        echo "All fruits: ${FRUITS[@]}"
        echo "First fruit: ${FRUITS[0]}"
        ```

### 3.3 Control Structures

* **Conditional Statements (`if`, `elif`, `else`):** Execute different blocks of code based on conditions.
    * **Syntax:**
        ```bash
        if [ condition ]; then
            # code if condition is true
        elif [ other_condition ]; then
            # code if other_condition is true
        else
            # code if no condition is true
        fi
        ```
    * **Common Conditions (using `[ ]` or `[[ ]]`):**
        * **File Tests:**
            * `-f file`: True if `file` exists and is a regular file.
            * `-d dir`: True if `dir` exists and is a directory.
            * `-e path`: True if `path` exists.
            * `-r file`: True if `file` is readable.
            * `-w file`: True if `file` is writable.
            * `-x file`: True if `file` is executable.
        * **String Comparisons:**
            * `"string1" == "string2"`: True if strings are equal.
            * `"string1" != "string2"`: True if strings are not equal.
            * `-z "string"`: True if string is empty.
            * `-n "string"`: True if string is not empty.
        * **Numeric Comparisons:**
            * `num1 -eq num2`: Equal to.
            * `num1 -ne num2`: Not equal to.
            * `num1 -gt num2`: Greater than.
            * `num1 -ge num2`: Greater than or equal to.
            * `num1 -lt num2`: Less than.
            * `num1 -le num2`: Less than or equal to.
    * **Example:**
        ```bash
        #!/bin/bash
        FILE="my_file.txt"
        if [ -f "$FILE" ]; then
            echo "$FILE exists."
        else
            echo "$FILE does not exist."
        fi
        ```
* **Loops (`for`, `while`):** Execute a block of code multiple times.
    * **`for` loop (iterating over a list):**
        ```bash
        #!/bin/bash
        for ITEM in "apple" "banana" "cherry"; do
            echo "I like $ITEM."
        done

        # Loop through files
        for FILE in *.txt; do
            echo "Processing $FILE"
        done
        ```
    * **`for` loop (C-style numeric iteration):**
        ```bash
        #!/bin/bash
        for (( i=1; i<=5; i++ )); do
            echo "Number: $i"
        done
        ```
    * **`while` loop (looping while a condition is true):**
        ```bash
        #!/bin/bash
        COUNT=1
        while [ $COUNT -le 5 ]; do
            echo "Count: $COUNT"
            COUNT=$((COUNT + 1)) # Arithmetic expansion
        done
        ```
* **`case` statement:** For multi-way branching based on patterns.
    * **Example:**
        ```bash
        #!/bin/bash
        read -p "Enter your choice (y/n): " CHOICE
        case "$CHOICE" in
            y|Y)
                echo "You chose Yes."
                ;;
            n|N)
                echo "You chose No."
                ;;
            *)
                echo "Invalid choice."
                ;;
        esac
        ```

### 3.4 Functions

* Reusable blocks of code that perform a specific task. Improve script organization and avoid repetition.
    * **Defining:**
        ```bash
        function my_function {
            # code here
        }
        # OR
        my_function () {
            # code here
        }
        ```
    * **Calling:** `my_function`
    * **Arguments to functions:** Accessed like script arguments (`$1`, `$2`, etc.).
    * **Return value:** Use `return <integer>` to return an exit status. `echo` can be used to return strings.
    * **Example:**
        ```bash
        #!/bin/bash
        greet_user() {
            echo "Hello, $1!" # $1 is the first argument passed to the function
        }

        greet_user "World"
        greet_user "DevOps Engineer"
        ```

### 3.5 Task Automation

* Shell scripting is the **backbone of automation** in Linux.
* **Backups:** Scripts can automate `tar`, `rsync`, or `cp` commands to create daily/weekly backups.
* **System Monitoring:** Scripts can periodically check disk space (`df`), process status (`ps`), or log files (`grep`, `tail`) and send alerts.
* **Log Rotation:** Custom scripts can manage log file sizes (though `logrotate` is often used).
* **Deployment Tasks:** Automating software deployments, configuration updates, and service restarts.
* **Error Handling and Exit Status:**
    * `$?`: Contains the **exit status** of the most recently executed command (0 for success, non-zero for failure).
    * `set -e`: **Exits the script immediately if any command fails.** Essential for robust scripts.
    * `trap 'echo "Error: Something went wrong!"' ERR`: Executes a command (or function) if an error occurs.
    * **Example:**
        ```bash
        #!/bin/bash
        set -e # Exit immediately if a command exits with a non-zero status.

        echo "Starting process..."
        mkdir /tmp/test_dir # This will succeed
        ls non_existent_file # This will fail, and script will exit if set -e is active
        echo "This line will not be executed if ls fails."
        ```

---

## 4. Package Management

Linux package managers simplify the process of installing, updating, configuring, and removing software.

### 4.1 APT (Debian-based: Ubuntu, Debian)

* **`apt`:** The modern, user-friendly command that combines functionalities from `apt-get`, `apt-cache`, etc. Recommended for general use.
    * `sudo apt update`: Synchronizes package index files from repositories. **Always run this before `install` or `upgrade`!**
    * `sudo apt upgrade`: Upgrades all installed packages to their latest versions.
    * `sudo apt full-upgrade`: Upgrades packages, also handling dependency changes by potentially removing old packages.
    * `sudo apt install <package_name>`: Installs a new package.
    * `sudo apt remove <package_name>`: Removes a package, but *leaves configuration files*.
    * `sudo apt purge <package_name>`: Removes a package and its **configuration files**.
    * `sudo apt autoremove`: Removes packages that were installed as dependencies and are no longer needed.
    * `apt search <keyword>`: Searches for packages containing the keyword.
    * `apt show <package_name>`: Displays detailed information about a package.
    * `apt list --installed`: Lists all installed packages.
* **`apt-get`:** Older command, still widely used in scripts. Functionally similar to `apt` for many common operations.
    * `sudo apt-get update`
    * `sudo apt-get install <package_name>`
* **`dpkg`:** Low-level package manager for Debian packages (`.deb` files). `apt` is a front-end to `dpkg`.
    * `sudo dpkg -i <package.deb>`: Installs a local `.deb` file.
    * `sudo dpkg -r <package_name>`: Removes an installed package.
    * `dpkg -l`: Lists installed packages.
    * `dpkg -s <package_name>`: Shows status of installed package.
    * `dpkg -L <package_name>`: Lists files installed by a package.

### 4.2 YUM/DNF (Red Hat-based: CentOS, Fedora, RHEL)

* **`dnf`:** The next-generation version of `yum`, providing better performance and dependency resolution. Preferred on modern Red Hat-based systems.
    * `sudo dnf check-update`: Checks for available updates.
    * `sudo dnf update`: Updates all installed packages.
    * `sudo dnf install <package_name>`: Installs a package.
    * `sudo dnf remove <package_name>`: Removes a package.
    * `dnf search <keyword>`: Searches for packages.
    * `dnf info <package_name>`: Displays detailed information about a package.
    * `dnf list installed`: Lists all installed packages.
* **`yum`:** Legacy package manager. Still available on older RHEL/CentOS versions.
    * `sudo yum update`
    * `sudo yum install <package_name>`

### 4.3 Repository Management

* **Adding/Removing Repositories:** Package managers rely on repositories (servers containing software packages).
    * **Debian-based:** Repositories are configured in `/etc/apt/sources.list` and files in `/etc/apt/sources.list.d/`. Adding typically involves:
        1.  Adding a PPA (Personal Package Archive) using `sudo add-apt-repository ppa:<ppa_name>`.
        2.  Manually adding a line to `/etc/apt/sources.list` or a new file in `/etc/apt/sources.list.d/`.
        3.  Importing the repository's GPG key: `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <KEY_ID>` (though `apt-key` is deprecated, `signed-by` in source lists is preferred).
        4.  Running `sudo apt update` after adding.
    * **Red Hat-based:** Repositories are typically defined in `.repo` files located in `/etc/yum.repos.d/`.
        1.  Adding a new `.repo` file.
        2.  Using `sudo dnf config-manager --add-repo <url_to_repo_file>` or `sudo yum-config-manager --add-repo <url_to_repo_file>`.
        3.  Enabling/disabling with `sudo dnf config-manager --set-enabled <repo_id>`.

---

## 5. Networking Basics

Understanding networking concepts and tools is crucial for configuring servers, troubleshooting connectivity, and ensuring services are accessible.

### 5.1 Configuring Network Interfaces

* **`ip` command (Modern & Preferred):** A powerful utility for managing network interfaces, routing tables, and ARP.
    * `ip addr show`: Displays IP addresses and network interfaces (similar to `ifconfig`).
    * `ip link show`: Displays network interface status (up/down, MAC address).
    * `ip route show`: Displays the kernel's IP routing table.
    * `sudo ip addr add 192.168.1.10/24 dev eth0`: Adds an IP address to `eth0` (temporary).
    * `sudo ip link set eth0 up`: Brings the `eth0` interface up.
    * **Persistent Configuration:** Network configurations are usually made persistent by editing specific configuration files (location varies by distribution, e.g., `/etc/network/interfaces` on Debian/Ubuntu, `/etc/sysconfig/network-scripts/ifcfg-eth0` on RHEL/CentOS, or using NetworkManager).
* **`ifconfig` (Legacy):** Displays and configures network interfaces. Still commonly found but deprecated in newer distributions in favor of `ip`.
    * `ifconfig`: Displays all active interfaces.
    * `ifconfig eth0`: Displays specific interface details.
    * `sudo ifconfig eth0 192.168.1.10 netmask 255.255.255.0 up`: Sets IP and brings interface up (temporary).

### 5.2 IP Addressing and Subnetting

* **IP Address:** A numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication.
    * **IPv4:** (e.g., `192.168.1.10`) 32-bit address, typically represented as four octets.
    * **IPv6:** (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`) 128-bit address.
* **Subnet Mask:** Defines the network and host portion of an IP address. Determines which part of the IP address identifies the network and which identifies the specific device on that network.
    * **Example:** `255.255.255.0` or `/24` (CIDR notation).
* **Gateway:** The IP address of the router that connects the local network to other networks (e.g., the Internet).
* **DNS Servers:** IP addresses of servers that translate human-readable domain names (e.g., `google.com`) into machine-readable IP addresses.

### 5.3 Network Tools

* `ping <host>`: Checks basic network **connectivity** to a host. Sends ICMP echo requests.
    * `ping -c 5 google.com`: Sends 5 packets and stops.
    * `ping 127.0.0.1`: Pings localhost (checks local network stack).
* `netstat` (or `ss`): Displays network statistics, open ports, routing tables, and connections. `ss` is faster and more efficient, replacing `netstat` in many modern systems.
    * `netstat -tulnp`: Shows **T**CP, **U**DP **L**istening **N**umeric ports with **P**rocess ID.
    * `ss -tuln`: Modern equivalent to `netstat -tuln`.
    * `ss -s`: Shows summary statistics.
* `traceroute <host>`: Traces the route that IP packets take to a host, showing each hop (router) along the path. Useful for diagnosing network latency or path issues.
* `dig <domain>`: **D**omain **I**nformation **G**roper. Advanced command-line tool for querying DNS name servers.
    * `dig example.com`: Default query (A record).
    * `dig example.com MX`: Query Mail Exchange records.
* `nslookup <domain>`: Simple DNS lookup utility.
* `route`: Displays or manipulates the IP routing table. (Mostly replaced by `ip route`).
* `arp`: Displays or manipulates the ARP cache (maps IP addresses to MAC addresses). (Mostly replaced by `ip neigh`).

### 5.4 DNS and Host Files

* **DNS (Domain Name System):** A hierarchical and decentralized naming system for computers, services, or any resource connected to the Internet or a private network. It translates human-readable domain names into IP addresses.
* `/etc/resolv.conf`: Configuration file that specifies the **DNS servers** the system should use for name resolution.
    * `nameserver 8.8.8.8`
    * `nameserver 8.8.4.4`
* `/etc/hosts`: A static file for **local hostname resolution**. It maps IP addresses to hostnames. Entries here take precedence over DNS queries.
    * **Example:** `127.0.0.1 localhost`
    * **Example for local testing:** `192.168.1.10 myapp.local` (allows you to access `myapp.local` as `192.168.1.10` without a DNS server).

### 5.5 SSH (Secure Shell)

SSH is a cryptographic network protocol for secure data communication, remote command-line login, and other secure network services between two networked computers. It's the cornerstone of remote Linux administration.

* **Securely Accessing Remote Machines:**
    * `ssh user@hostname_or_ip`: Connects to the remote host as `user`.
    * `ssh -p <port> user@hostname_or_ip`: Connects to a custom SSH port (default is 22).
    * **Example:** `ssh devops@192.168.1.100`
* **Key-Based Authentication (Recommended):** More secure and convenient than password authentication.
    1.  **Generate SSH keys:** `ssh-keygen` (creates `id_rsa` (private key) and `id_rsa.pub` (public key) in `~/.ssh/`).
    2.  **Copy public key to remote host:** `ssh-copy-id user@remote_host` (This command copies your public key to the remote host's `~/.ssh/authorized_keys` file).
    3.  Once the public key is on the server, you can `ssh` without a password.
* **`scp` for Secure File Transfers:**
    * `scp /local/path/file.txt user@remote_host:/remote/path/`
    * `scp -r user@remote_host:/remote/dir/ /local/path/`
* **SSH Configuration File (`~/.ssh/config`):** Allows you to define shortcuts and specific settings for different hosts.
    * **Example:**
        ```
        Host myserver
            Hostname 192.168.1.100
            User devops
            Port 2222
            IdentityFile ~/.ssh/id_rsa_myserver
        ```
        Now you can just type `ssh myserver`.

---

## 6. Security and Permissions

Linux's robust security model is built around users, groups, and file permissions.

### 6.1 User and Group Management

* **Users:** Each user has a unique ID (UID).
    * `useradd <username>`: Creates a new user account. (Often just adds the user, no home directory or password).
        * `sudo useradd -m <username>`: Creates user with a home directory (`-m`).
        * `sudo useradd -s /bin/bash <username>`: Sets the default shell.
    * `passwd <username>`: Sets or changes a user's password.
    * `usermod`: Modifies an existing user account.
        * `sudo usermod -aG <groupname> <username>`: **A**dds user to a **G**roup (appends, doesn't overwrite existing groups). This is crucial!
        * `sudo usermod -l <new_username> <old_username>`: Changes username.
        * `sudo usermod -d /new/home/dir -m <username>`: Moves (`-m`) user's home directory.
    * `userdel <username>`: Deletes a user account.
        * `sudo userdel -r <username>`: Deletes user and their **home directory** (`-r`).
* **Groups:** Collections of users. Each group has a unique ID (GID).
    * `groupadd <groupname>`: Creates a new group.
    * `groupdel <groupname>`: Deletes a group.
    * `groups <username>`: Displays the groups a user belongs to.
    * `id <username>`: Displays user and group IDs.
* **`/etc/passwd`:** Stores user account information (username, UID, GID, home directory, shell).
* **`/etc/shadow`:** Stores encrypted user passwords and password expiration information. **Highly sensitive!**
* **`/etc/group`:** Stores group information (group name, GID, members).

### 6.2 Permissions and Ownership

* **File Permissions (r, w, x):**
    * `r` (read): Can view content (for files), can list directory content (for directories). Numeric value: `4`.
    * `w` (write): Can modify content (for files), can create/delete/rename files within (for directories). Numeric value: `2`.
    * `x` (execute): Can run the file (if it's a program/script), can traverse/enter the directory (for directories). Numeric value: `1`.
* **Permission String (e.g., `-rwxr-xr--` from `ls -l`):**
    * First character: File type (`-` for regular file, `d` for directory, `l` for symlink).
    * Next 3 chars: Owner permissions (`rwx`).
    * Next 3 chars: Group permissions (`r-x`).
    * Next 3 chars: Others permissions (`r--`).
* **`chmod`:** (See section 2.8)
    * `chmod 755 script.sh`: `rwxr-xr-x` - Owner can read, write, execute; Group and Others can read and execute. Common for scripts/executables.
    * `chmod 644 index.html`: `rw-r--r--` - Owner can read/write; Group and Others can only read. Common for web content.
    * `chmod -R 770 /data/app_files`: Recursive, gives read/write/execute to owner and group, no access to others.
* **`chown`:** (See section 2.8)
* **`chgrp`:** (See section 2.8)
* **Special Permissions (Sticky Bit, SUID, SGID):**
    * **SUID (Set User ID - `s` in owner's `x` position):** When an executable with SUID is run, it executes with the permissions of the file's owner, not the user running it. (e.g., `passwd` command, allows non-root users to change their password). Octal `4000`.
    * **SGID (Set Group ID - `s` in group's `x` position):** For executables, runs with the permissions of the file's group. For directories, new files/directories created within inherit the group of the parent directory. Octal `2000`.
    * **Sticky Bit (`t` in others' `x` position for directories):** For directories, only the owner of a file (or root) can delete or rename files within that directory, regardless of other permissions. (e.g., `/tmp`). Octal `1000`.
    * **Applying with `chmod`:** Add the octal value to the usual permissions.
        * `chmod 4755 my_program` (sets SUID, and 755 for owner/group/others).
        * `chmod 1777 /tmp` (sets sticky bit, and 777 for tmp directory).

### 6.3 Sudo

* `sudo` allows authorized users to execute commands as the superuser (root) or another user. It provides **granular control** over who can run what commands with elevated privileges, without sharing the root password.
* **`/etc/sudoers` file:** Contains the configuration for `sudo`.
    * **Always edit with `visudo`:** This command checks for syntax errors before saving, preventing you from locking yourself out of `sudo`.
    * **Syntax:** `user ALL=(ALL:ALL) ALL` (user can run ALL commands, from ALL terminals, as ALL users and ALL groups).
    * **Example for specific commands:** `devops ALL=(ALL) /usr/sbin/apachectl, /usr/bin/systemctl restart nginx` (allows `devops` user to run `apachectl` and restart `nginx` via `systemctl`).
    * **No password for specific commands:** `devops ALL=(ALL) NOPASSWD: /usr/sbin/reboot`

### 6.4 SELinux/AppArmor (Advanced Security Policies)

These are **mandatory access control (MAC)** systems that add an extra layer of security beyond traditional discretionary access control (DAC - Linux permissions). They define strict rules on what processes can access what resources.

* **SELinux (Security-Enhanced Linux):** Implemented in Red Hat-based distributions (RHEL, CentOS, Fedora). Highly granular and complex, but very powerful.
    * **Modes:** `Enforcing`, `Permissive`, `Disabled`.
    * **Tools:** `sestatus`, `setenforce`, `semanage`, `restorecon`.
    * **Troubleshooting:** `audit2allow` (to analyze AVC denials from audit logs).
* **AppArmor:** Implemented in Debian-based distributions (Ubuntu, Debian). Simpler to configure and manage than SELinux, using profiles to restrict program capabilities.
    * **Tools:** `aa-status`, `aa-enforce`, `aa-complain`, `aa-logprof`.

---

## 7. File Systems and Storage

Managing storage effectively is critical for server reliability and performance.

### 7.1 Understanding File Systems

* A file system is a method and data structure that an operating system uses to control how data is stored and retrieved.
* **`ext4` (Extended Filesystem 4):** Default and most common Linux filesystem. Successor to ext3, offering larger volume and file size support, and improved performance.
* **`XFS`:** High-performance journaling filesystem. Often used for large file systems and high-throughput applications.
* **`Btrfs` (B-tree File System):** A modern copy-on-write (CoW) filesystem. Offers advanced features like snapshots, checksums, and built-in RAID.
* **`ZFS`:** Another powerful CoW filesystem, known for its data integrity features, snapshots, and volume management capabilities. (Often used as an external module on Linux).
* **Journaling Filesystems:** Record changes to metadata (e.g., file permissions, directory structure) in a log (journal) before committing them to the main filesystem. This prevents data corruption in case of system crashes. (`ext4`, `XFS`, `NTFS` are journaling).

### 7.2 Mounting and Unmounting

* **Mounting:** The process of making a filesystem accessible at a specific point (mount point) in the directory tree.
* **Unmounting:** The process of detaching a filesystem from its mount point, making it inaccessible.
* `mount`: Mounts a filesystem.
    * `sudo mount /dev/sdb1 /mnt/data`: Mounts the partition `/dev/sdb1` to `/mnt/data`.
    * `mount -a`: Mounts all filesystems listed in `/etc/fstab`.
    * `mount`: (without arguments) Shows currently mounted filesystems.
* `umount`: Unmounts a filesystem.
    * `sudo umount /mnt/data`: Unmounts the filesystem mounted at `/mnt/data`.
    * `sudo umount /dev/sdb1`: Unmounts the device `/dev/sdb1`.
    * **Common Error:** "Device is busy" - means files are open or processes are using the mount point. Use `lsof /mnt/data` or `fuser -m /mnt/data` to find processes.
* **`/etc/fstab`:** **F**ile **S**ystem **Tab**le. A configuration file that lists filesystems that should be automatically mounted at boot time.
    * **Structure:** `device  mount_point  filesystem_type  options  dump_freq  pass_num`
    * **Example:** `/dev/sda1 /mnt/backup ext4 defaults 0 2`
    * **Crucial for persistence!** Always back up before editing, and test with `sudo mount -a`.

### 7.3 Disk Partitions

* **Partition:** A logical division of a physical storage device (e.g., hard drive).
* `fdisk`: Command-line utility for managing disk partitions (MBR and GPT partitions, but more focused on MBR).
    * `sudo fdisk /dev/sdb`: Opens `fdisk` for `/dev/sdb`. (Interactive, use `m` for menu, `p` to print partition table, `n` to create, `d` to delete, `w` to write changes, `q` to quit without saving).
* `parted`: A more modern and powerful partitioning tool, supports both MBR and GPT partition tables, and handles larger disks.
    * `sudo parted /dev/sdb`: Opens `parted` for `/dev/sdb`. (Interactive, use `print`, `mklabel gpt`, `mkpart primary ext4 0% 100%`, `quit`).
* `lsblk`: **L**i**s**t **Bl**oc**k** devices. Lists information about all available block devices (disks, partitions, LVM volumes) in a tree-like format. Very useful for quickly seeing your storage layout.
    * `lsblk`
    * `lsblk -f`: Shows filesystem type and UUIDs.
* `mkfs.<filesystem_type>`: **M**a**k**e **F**ile**s**ystem. Formats a partition with a specific filesystem.
    * `sudo mkfs.ext4 /dev/sdb1`: Formats `/dev/sdb1` with ext4.
    * `sudo mkfs.xfs /dev/sdb2`

### 7.4 LVM (Logical Volume Manager)

* LVM provides a more flexible way to manage disk space compared to traditional partitioning. It allows you to create logical volumes that span across multiple physical disks, resize them easily, and take snapshots.
* **Key Concepts:**
    * **Physical Volume (PV):** A physical disk or partition initialized for use by LVM (`pvcreate`).
    * **Volume Group (VG):** One or more PVs combined into a single storage pool (`vgcreate`).
    * **Logical Volume (LV):** A virtual partition created from a VG. LVs are what you format and mount (`lvcreate`).
* **Basic LVM Workflow:**
    1.  `sudo pvcreate /dev/sdb1 /dev/sdc1` (Initialize partitions as PVs).
    2.  `sudo vgcreate my_vg /dev/sdb1 /dev/sdc1` (Create a VG named `my_vg` from PVs).
    3.  `sudo lvcreate -L 10G -n my_lv my_vg` (Create a 10GB LV named `my_lv` in `my_vg`).
    4.  `sudo mkfs.ext4 /dev/my_vg/my_lv` (Format the LV).
    5.  `sudo mount /dev/my_vg/my_lv /mnt/mylvm` (Mount the LV).
* **Common LVM Commands:**
    * `pvdisplay`, `vgdisplay`, `lvdisplay`: Display information about PVs, VGs, and LVs.
    * `lvextend`, `lvreduce`: Extend or reduce the size of LVs.
    * `resize2fs` (for ext4) or `xfs_growfs` (for xfs): Resize the filesystem *after* resizing the LV.
    * `lvcreate --snapshot`: Create snapshots of LVs.

---

## 8. System Monitoring and Performance Tuning

Ensuring the health and optimal performance of Linux systems is a key DevOps responsibility.

### 8.1 System Performance Monitoring

* **`top` / `htop`:** (See section 2.4 for details). Provide real-time overview of processes, CPU, and memory usage.
    * **Key metrics to watch in `top`:**
        * **`load average`:** Average number of processes waiting in the run queue over 1, 5, and 15 minutes. High values indicate CPU contention.
        * **`%Cpu(s)`:** Breakdown of CPU usage (user, system, nice, idle, wait I/O (`wa`), hardware/software interrupts). High `wa` indicates I/O bottleneck.
        * **`Mem`:** Total, free, used, buffers, cache memory. Large cache is good.
        * **`Swap`:** Usage indicates memory pressure (swapping to disk is slow).
* **`free`:** Displays total, used, and free amounts of physical and swap memory.
    * `free -h`: Human-readable format.
    * **Example:** `free -h`
* `vmstat`: **V**irtual **M**emory **Stat**istics. Reports information about processes, memory, paging, block IO, traps, and CPU activity.
    * `vmstat 1`: Updates every 1 second.
    * **Key metrics:** `si` (swap in), `so` (swap out) - indicates swapping. `wa` (wait I/O) - indicates disk bottlenecks.
* `iostat`: **I/O Stat**istics. Reports CPU utilization and I/O statistics for devices, partitions, and network filesystems. Useful for diagnosing disk bottlenecks.
    * `sudo apt install sysstat` or `sudo dnf install sysstat` to get `iostat` and `sar`.
    * `iostat -xz 1`: Extended statistics (`x`), summarizes for all devices (`z`), updates every 1 second.
    * **Key metrics:** `%util` (device utilization), `await` (average wait time for I/O requests), `svctm` (average service time).
* `sar`: **S**ystem **A**ctivity **R**eport. Collects, reports, or saves system activity information. Can show historical data.
    * `sar -u 1 5`: Reports CPU utilization every 1 second for 5 times.
    * `sar -d 1 5`: Reports disk activity.
    * `sar -n DEV 1 5`: Reports network activity.

### 8.2 Log Management

Logs are critical for troubleshooting, auditing, and understanding system behavior.

* **`/var/log/`:** The primary directory for most system and application log files.
    * **Common logs:**
        * `/var/log/syslog` (Debian/Ubuntu) or `/var/log/messages` (RHEL/CentOS): General system activity.
        * `/var/log/auth.log` (Debian/Ubuntu) or `/var/log/secure` (RHEL/CentOS): Authentication attempts, sudo usage.
        * `/var/log/kern.log`: Kernel messages.
        * `/var/log/apache2/access.log`, `/var/log/nginx/access.log`: Web server access logs.
        * `/var/log/dmesg`: Kernel ring buffer messages (boot messages).
* **`journalctl` (Systemd Journal):** The primary tool for querying and viewing logs collected by `systemd-journald`. Provides a centralized logging system.
    * `journalctl`: Shows all logs from the beginning of the journal.
    * `journalctl -f`: Follows (tails) the journal in real-time.
    * `journalctl -u nginx.service`: Shows logs for the `nginx` service.
    * `journalctl -p err -b`: Shows error messages (`-p err`) from the current boot (`-b`).
    * `journalctl --since "2023-01-01 10:00:00"`: Shows logs from a specific time.
* **`logrotate`:** A utility for automatically rotating, compressing, and removing old log files. Prevents log files from consuming too much disk space. Configured in `/etc/logrotate.conf` and `/etc/logrotate.d/`.

### 8.3 Performance Tuning

* **CPU Tuning:**
    * Identify CPU-bound processes (`top`, `htop`).
    * Optimize applications or scripts.
    * Adjust process priorities (`nice`, `renice`).
* **Memory Tuning:**
    * Identify memory hogs (`top`, `htop`).
    * Reduce unnecessary services.
    * Adjust application memory limits.
    * Consider adding more RAM.
* **Disk I/O Tuning:**
    * Identify I/O-bound processes (`iostat`).
    * Optimize disk usage (e.g., separate logs onto a dedicated disk).
    * Use faster storage (SSD).
    * Tune filesystem options (e.g., `noatime` in `fstab`).
* **Network Tuning:**
    * Optimize network configuration parameters (e.g., TCP buffer sizes via `sysctl`).
    * Ensure proper firewall rules.
* **Kernel Parameters (`sysctl`):** Tune various kernel parameters at runtime. Changes are temporary unless configured persistently in `/etc/sysctl.conf` or `/etc/d.d/` files.
    * `sysctl -a`: Lists all kernel parameters.
    * `sysctl net.ipv4.ip_forward=1`: Enables IP forwarding (temporary).
    * `echo "net.ipv4.ip_forward = 1" | sudo tee -a /etc/sysctl.conf` (makes it persistent).
    * `sudo sysctl -p`: Applies changes from `sysctl.conf`.
* **Resource Limits (`ulimit`):** Set limits on system resources available to processes (e.g., number of open files, maximum memory usage). Configured per-user in `~/.bashrc`, `~/.profile`, or system-wide in `/etc/security/limits.conf`.
    * `ulimit -n`: Shows current open file limit.
    * `ulimit -n 65535`: Sets open file limit to 65535 (temporary for current shell).

---

## 9. Automated Task Scheduling

Automating routine tasks is a core principle of DevOps.

### 9.1 Cron Jobs

* `cron` is a **time-based job scheduler** in Unix-like operating systems. It allows users to schedule commands or scripts to run automatically at a specified date and time.
* **`crontab`:** The command used to edit and manage user-specific cron jobs. Each user (including root) has their own crontab file.
    * `crontab -e`: Edits the current user's crontab file. (First time prompts to choose editor).
    * `crontab -l`: Lists the current user's cron jobs.
    * `crontab -r`: **Removes all** of the current user's cron jobs. **Use with caution!**
* **Cron Syntax:**
    * A cron job entry consists of five time fields, followed by the command to be executed.
    * `* * * * * command_to_execute`
        1.  **Minute (0-59)**
        2.  **Hour (0-23)**
        3.  **Day of Month (1-31)**
        4.  **Month (1-12 or Jan-Dec)**
        5.  **Day of Week (0-7 or Sun-Sat, where 0 and 7 are Sunday)**
    * **Special Characters:**
        * `*`: Wildcard, matches all values. (e.g., `*` in minute means "every minute").
        * `,`: List separator. (e.g., `1,15,30` for minutes 1, 15, and 30).
        * `-`: Range separator. (e.g., `9-17` for hours 9 through 17).
        * `/`: Step value. (e.g., `*/10` in minute means "every 10 minutes").
    * **Examples:**
        * `0 2 * * * /path/to/daily_backup.sh`: Runs `daily_backup.sh` at 2:00 AM every day.
        * `*/5 * * * * /usr/bin/logger "Heartbeat"`: Logs "Heartbeat" every 5 minutes.
        * `0 0 1 * * /path/to/monthly_report.sh`: Runs `monthly_report.sh` at midnight on the 1st of every month.
* **System-wide Cron Jobs:**
    * `/etc/crontab`: System-wide crontab, often includes an additional field for the user to run the command as.
    * `/etc/cron.d/`: Directory for individual cron job files (useful for package-specific cron jobs).
    * `/etc/cron.hourly/`, `/etc/cron.daily/`, `/etc/cron.weekly/`, `/etc/cron.monthly/`: Directories where scripts placed inside will be executed hourly, daily, weekly, or monthly by default system cron jobs.

### 9.2 Anacron

* `anacron` is a utility that executes commands periodically, typically once a day, week, or month. Unlike `cron`, it does **not** assume the system is running continuously. It's designed for machines that might be turned off at scheduled execution times (e.g., laptops, desktop PCs).
* **How it works:** `anacron` checks if jobs were missed while the system was off. If a job's last execution date is older than its configured period, `anacron` runs it.
* **Configuration:** Typically configured in `/etc/anacrontab`.

---

## 10. Backup and Recovery

Robust backup and recovery strategies are paramount in DevOps to ensure data integrity and business continuity.

### 10.1 Creating Backups

* **`rsync` (Recommended for incremental backups):** Efficiently synchronizes files and directories, only transferring the changes.
    * `rsync -avz /source/dir/ /destination/dir/`: Archive mode (`a`), verbose (`v`), compress (`z`). Common for local or remote syncs.
    * `rsync -avz --delete /source/dir/ /destination/dir/`: Synchronizes and deletes files in the destination that are no longer in the source. **Use with extreme caution!**
    * `rsync -avz --exclude 'logs/' /source/dir/ /destination/dir/`: Excludes specific directories.
    * `rsync -avz --link-dest=/path/to/previous_full_backup /source/dir/ /destination/increment_backup/`: Creates incremental backups using hard links, saving disk space.
* **`tar` (For archiving and compression):** Creates compressed archives (tarballs) of files and directories. Excellent for full backups.
    * `tar -czvf my_backup.tar.gz /data/my_app/`: Creates a gzipped tarball of `/data/my_app/`.
    * `tar -cjvf my_backup.tar.bz2 /data/my_app/`: Creates a bzip2 compressed tarball (often smaller, but slower).
    * `tar -cJvf my_backup.tar.xz /data/my_app/`: Creates an xz compressed tarball (best compression, slowest).
* **`dd` (For disk cloning/imaging):** Copies data directly from one block device to another, sector by sector. Useful for creating full disk images or cloning drives.
    * `sudo dd if=/dev/sda of=/dev/sdb bs=4M status=progress`: Copies `/dev/sda` to `/dev/sdb`. `bs` (block size) improves speed, `status=progress` shows progress. **Extremely dangerous if `of` (output file) is wrong!**
    * `sudo dd if=/dev/sda of=/path/to/disk_image.img bs=4M`: Creates a disk image file.
* **Other Backup Tools:**
    * **`BorgBackup`:** Deduplicating archiver with encryption and compression.
    * **`Duplicity`:** Encrypted, signed, incremental backups using rsync algorithm.
    * **Cloud-specific backup solutions:** AWS S3, Google Cloud Storage, Azure Blob Storage, often with dedicated backup services.

### 10.2 Disaster Recovery

* **Implement a Disaster Recovery Plan:** A documented strategy for recovering your IT infrastructure and data in the event of a disaster.
    * **Key components:** **RTO (Recovery Time Objective** - max downtime), **RPO (Recovery Point Objective** - max data loss).
* **Regularly Test Backups:** Crucial to ensure backups are restorable and meet RTO/RPO targets. This often involves:
    * Periodically restoring data to a test environment.
    * Verifying data integrity.
    * Simulating disaster scenarios.
* **Offsite Storage:** Store backups in a physically separate location to protect against site-specific disasters (fire, flood).
* **Backup Retention Policies:** Define how long backups are kept (e.g., daily for 7 days, weekly for 4 weeks, monthly for 1 year).

---

## 11. Virtualization and Containers

These technologies are central to modern DevOps, enabling efficient resource utilization, isolation, and rapid deployment.

### 11.1 Basics of Virtualization

* **Virtualization:** The process of creating a **virtual (software-based)** version of something, rather than the actual (hardware-based) version. In computing, this often means creating virtual machines (VMs).
* **Hypervisor:** Software that creates and runs virtual machines.
    * **Type 1 (Bare-Metal):** Runs directly on hardware (e.g., KVM, VMware ESXi).
    * **Type 2 (Hosted):** Runs on top of an existing OS (e.g., VirtualBox, VMware Workstation).
* **KVM (Kernel-based Virtual Machine):** A **type 1 hypervisor** built into the Linux kernel. It allows the Linux kernel to function as a hypervisor, running multiple isolated virtual machines. Often managed with `libvirt` and tools like `virt-manager` or `virsh`.
* **VirtualBox:** A popular, open-source Type 2 hypervisor for desktops, allowing you to run VMs on your existing OS.

### 11.2 Docker Fundamentals

* **Containers:** Lightweight, isolated, and portable software packages that bundle an application and all its dependencies (libraries, frameworks, configuration files) into a single unit. They share the host OS kernel but run in isolated user spaces.
* **Docker Engine:** A daemon that builds, runs, and manages Docker containers.
* **Docker Image:** A **read-only template** that contains the application and all its dependencies. Used to create containers.
* **Docker Container:** A runnable instance of a Docker image. It's a lightweight, isolated environment where your application runs.
* **Installation:**
    * Follow official Docker documentation for your distribution (e.g., `sudo apt install docker.io`, then `sudo systemctl start docker`, `sudo systemctl enable docker`, and add your user to the `docker` group: `sudo usermod -aG docker $USER` and re-login).
* **Key Docker Commands:**
    * `docker version`: Display Docker version info.
    * `docker pull <image_name>`: Downloads a Docker image from a registry (e.g., Docker Hub).
    * `docker images`: Lists local Docker images.
    * `docker run <image_name>`: Creates and starts a container from an image.
        * `docker run -it ubuntu bash`: Runs an interactive shell in a new Ubuntu container.
        * `docker run -d -p 80:80 my_web_app_image`: Runs in detached mode (`-d`), maps host port 80 to container port 80 (`-p`).
        * `docker run --name my_container_name image`: Assigns a name to the container.
        * `docker run -v /host/path:/container/path image`: Mounts a volume (persistent storage).
        * `docker run --network my_custom_network image`: Connects to a specific Docker network.
    * `docker ps`: Lists running containers.
    * `docker ps -a`: Lists all containers (running and stopped).
    * `docker start <container_id_or_name>`: Starts a stopped container.
    * `docker stop <container_id_or_name>`: Stops a running container gracefully.
    * `docker restart <container_id_or_name>`: Restarts a container.
    * `docker rm <container_id_or_name>`: Removes a stopped container.
    * `docker rmi <image_id_or_name>`: Removes an image.
    * `docker logs <container_id_or_name>`: Displays container logs.
    * `docker exec -it <container_id_or_name> bash`: Executes a command inside a running container.
    * `docker build -t my_image .`: Builds an image from a Dockerfile in the current directory.

### 11.3 Dockerfile

* A `Dockerfile` is a text file that contains a set of instructions for building a Docker image. Each instruction creates a layer in the image.
* **Common Dockerfile Instructions:**
    * `FROM <base_image>`: Specifies the base image (e.g., `FROM ubuntu:22.04`).
    * `WORKDIR /app`: Sets the working directory inside the container.
    * `COPY . .`: Copies files from the host to the container.
    * `ADD <src> <dest>`: Similar to `COPY`, but can handle URLs and tar archives.
    * `RUN <command>`: Executes a command during the image build process (e.g., installing packages).
    * `CMD ["executable", "param1"]`: Provides defaults for an executing container (can be overridden by `docker run` command). Only one `CMD` per Dockerfile.
    * `ENTRYPOINT ["executable", "param1"]`: Configures a container that will run as an executable. Often used with `CMD` as arguments.
    * `EXPOSE <port>`: Informs Docker that the container listens on the specified network ports at runtime. (Doesn't actually publish the port).
    * `ENV <key>=<value>`: Sets environment variables.
* **Example Dockerfile:**
    ```dockerfile
    # Use an official Python runtime as a parent image
    FROM python:3.9-slim-buster

    # Set the working directory in the container
    WORKDIR /app

    # Copy the current directory contents into the container at /app
    COPY requirements.txt .
    COPY app.py .

    # Install any needed packages specified in requirements.txt
    RUN pip install --no-cache-dir -r requirements.txt

    # Make port 5000 available to the world outside this container
    EXPOSE 5000

    # Run app.py when the container launches
    CMD ["python", "app.py"]
    ```

### 11.4 Container Management with Docker Compose

* `docker-compose` is a tool for defining and running **multi-container Docker applications**. You define your application's services, networks, and volumes in a single `YAML` file (`docker-compose.yml`).
* **Benefits:** Simplifies the management of complex applications with multiple interdependent services (e.g., web app, database, cache).
* **Basic `docker-compose.yml` Structure:**

    ```yaml
    version: '3.8' # Specify Compose file format version

    services:
      web: # Name of your first service
        build: . # Build Dockerfile in current directory
        ports:
          - "80:5000" # Host_port:Container_port
        volumes:
          - .:/app # Mount current directory into /app in container
        depends_on: # Define service dependencies
          - db
      db: # Name of your second service
        image: postgres:13 # Use pre-built PostgreSQL image
        environment:
          POSTGRES_DB: mydatabase
          POSTGRES_USER: user
          POSTGRES_PASSWORD: password
        volumes:
          - db_data:/var/lib/postgresql/data # Persistent volume for database data

    volumes: # Define named volumes
      db_data:
    ```
* **Key Docker Compose Commands:**
    * `docker-compose up`: Builds, creates, starts, and attaches to containers for all services.
    * `docker-compose up -d`: Runs containers in detached mode (in the background).
    * `docker-compose down`: Stops and removes containers, networks, and volumes defined in the `docker-compose.yml` file.
    * `docker-compose ps`: Lists services with their status.
    * `docker-compose logs`: Displays log output from services.
    * `docker-compose exec <service_name> <command>`: Executes a command in a running service container.

---

## 12. Advanced Command-Line Tools

These tools leverage regular expressions and advanced filtering capabilities for powerful text processing and file management.

### 12.1 Text Processing

* **`grep`:** (Refer to section 2.9 for basic usage).
    * **Regular Expressions (Regex):** `grep` uses regular expressions for pattern matching.
        * `^pattern`: Matches lines starting with `pattern`.
        * `pattern$`: Matches lines ending with `pattern`.
        * `word1|word2`: Matches lines containing `word1` or `word2`.
        * `[abc]`: Matches any single character from the set.
        * `[0-9]+`: Matches one or more digits.
        * `.*`: Matches any character (except newline) zero or more times.
        * **Example:** `grep -E '^(Error|Warning)' /var/log/syslog` (Extended regex for OR condition).
        * **Example:** `grep -P '(?<=User ).*(?= logged in)' auth.log` (Perl-compatible regex for lookarounds).
* **`sed` (Stream Editor):** (Refer to section 2.9 for basic usage). Used for powerful text transformations, especially for substitutions.
    * `sed -i 's/old/new/g' filename.txt`: `-i` means "in-place edit" (modifies the file directly).
    * `sed -n '/pattern/p' filename.txt`: Prints only lines matching `pattern` (`-n` suppresses default output, `p` prints matching lines).
    * `sed '1,5d' filename.txt`: Deletes lines 1 to 5.
    * `sed '/^#/d' config.conf`: Deletes lines starting with `#` (comments).
* **`awk` (Pattern Scanning and Processing Language):** (Refer to section 2.9 for basic usage). Best for extracting and manipulating columnar data.
    * `awk '{print $NF}' logfile.txt`: Prints the last field (`$NF`).
    * `awk '$3 > 100 {print $1, $2}' data.txt`: Prints first and second fields if third field is greater than 100.
    * `awk 'BEGIN {FS=","} {print $1}' data.csv`: Sets field separator to comma.
    * `awk '/Error/ {count++} END {print "Errors found: " count}' logfile.log`: Counts lines containing "Error".

### 12.2 File Management

* **`find`:** (Refer to section 2.7 for detailed usage).
    * **Combining tests:** `find . -name "*.bak" -mtime +7 -delete`: Finds log files older than 7 days and deletes them.
    * **Permissions:** `find /var/www -type f -perm /002`: Finds files with write permission for others (any of the "others" bits set).
* **`xargs`:** Builds and executes command lines from standard input. Useful for passing a list of items (e.g., from `find` or `grep`) as arguments to another command.
    * `find . -name "*.bak" -print0 | xargs -0 rm`: Finds `.bak` files (null-separated output `-print0`), and safely removes them (`-0` for null-separated input). Prevents issues with spaces in filenames.
    * `ls *.txt | xargs wc -l`: Counts lines (`wc -l`) in all `.txt` files.

### 12.3 Network Configuration and Troubleshooting (Advanced `ip` and `ss`)

* **`ip` command (Deep Dive):**
    * `ip link set dev eth0 down/up`: Brings interface down/up.
    * `ip route add default via 192.168.1.1 dev eth0`: Adds a default gateway.
    * `ip neigh`: Displays ARP table (IP to MAC address mappings).
    * `ip monitor all`: Monitors network events in real-time.
* **`ss` command (Socket Statistics - Modern alternative to `netstat`):**
    * `ss -tunap`: Lists all TCP (`t`), UDP (`u`), numeric (`n`) connections with process name (`p`) and address (`a`).
    * `ss -lntu`: Lists all listening TCP and UDP sockets.
    * `ss -s`: Shows socket summary statistics.
* **`tcpdump`:** Packet analyzer that captures and displays TCP/IP and other packets being transmitted or received over a network. Powerful for low-level network troubleshooting.
    * `sudo tcpdump -i eth0`: Captures all traffic on `eth0`.
    * `sudo tcpdump -i eth0 port 80`: Captures traffic on port 80.
    * `sudo tcpdump -i eth0 host 192.168.1.100`: Captures traffic to/from a specific host.
    * `sudo tcpdump -i eth0 -w capture.pcap`: Saves captured packets to a file for later analysis (e.g., with Wireshark).
* **Wireshark:** A graphical network protocol analyzer. Can open `.pcap` files generated by `tcpdump` for detailed packet inspection.

---

## 13. Networking and Security Tools (Advanced)

### 13.1 SSH Configuration (Deep Dive)

* **`~/.ssh/config`:** (See section 5.5 for basic usage). More advanced options:
    * `ForwardAgent yes`: Allows using local SSH agent on remote server (useful for hopping between servers).
    * `ControlMaster auto` / `ControlPath` / `ControlPersist`: Multiplexes multiple SSH sessions over a single connection, speeding up subsequent connections.
    * `LocalForward`, `RemoteForward`: Create SSH tunnels for port forwarding.
        * `ssh -L 8080:localhost:80 user@remote_server`: Forwards remote port 80 to local port 8080.
* **SSH hardening:**
    * Disable password authentication on servers (`PasswordAuthentication no` in `/etc/ssh/sshd_config`).
    * Disable root login (`PermitRootLogin no`).
    * Change default SSH port.
    * Use strong, unique SSH keys.

### 13.2 Firewalls

Linux firewalls filter network traffic based on defined rules.

* **`iptables`:** The traditional, powerful, and highly flexible command-line firewall utility for Linux. Directly interacts with the Netfilter framework in the Linux kernel.
    * **Chains:** `INPUT`, `OUTPUT`, `FORWARD`.
    * **Rules:** Define what to do with packets (ACCEPT, DROP, REJECT).
    * **Tables:** `filter`, `nat`, `mangle`, `raw`.
    * **Example:**
        * `sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT`: Allows SSH.
        * `sudo iptables -A INPUT -j DROP`: Drops all other incoming traffic.
        * `sudo iptables -L -n -v`: Lists current rules.
        * **Persistence:** `iptables` rules are volatile; they need to be saved (e.g., with `iptables-save > /etc/sysconfig/iptables`) and restored on boot.
* **`firewalld` (Modern, Dynamic Firewall Daemon):** Used on RHEL/CentOS/Fedora. Provides a more user-friendly interface with zones and services, allowing changes without dropping existing connections.
    * `sudo systemctl start firewalld`
    * `sudo firewall-cmd --get-active-zones`: Shows active zones.
    * `sudo firewall-cmd --zone=public --add-service=http --permanent`: Allows HTTP service permanently in the public zone.
    * `sudo firewall-cmd --reload`: Applies permanent changes.
    * `sudo firewall-cmd --zone=public --list-all`: Lists all rules in the public zone.
* **`ufw` (Uncomplicated Firewall):** A user-friendly front-end for `iptables` on Debian/Ubuntu systems. Simple to use for basic firewalling.
    * `sudo ufw enable`: Enables the firewall.
    * `sudo ufw allow ssh`: Allows SSH traffic.
    * `sudo ufw status verbose`: Shows status and rules.

### 13.3 VPNs (Virtual Private Networks)

* VPNs create a secure, encrypted connection over a public network (like the internet).
* **OpenVPN:** A popular open-source VPN solution.
    * Requires server and client configuration.
    * Often used for site-to-site VPNs or for remote users to securely access internal networks.
* **WireGuard:** A newer, simpler, and faster VPN protocol, gaining popularity.

---

## 14. System Services and Daemons

Managing background processes and services is crucial for server operation.

### 14.1 Systemd

* `systemd` is the **dominant init system and service manager** for Linux. It manages processes after the kernel boots up, handles system services, and controls various aspects of the operating system.
* **Unit Files:** `systemd` manages services, mount points, devices, sockets, and other resources using "**unit files**" (e.g., `.service`, `.mount`, `.socket`). These are typically located in `/etc/systemd/system/` or `/lib/systemd/system/`.
* **Key `systemctl` Commands:** (Refer to section 2.9 for basic usage).
    * `systemctl list-units --type=service`: Lists all active service units.
    * `systemctl list-unit-files --type=service`: Lists all installed service unit files and their enabled/disabled status.
    * `systemctl cat <service_name>`: Displays the content of a unit file.
    * `systemctl edit --full <service_name>`: Edits a service unit file.
    * `systemctl set-default multi-user.target`: Sets the default boot target (e.g., multi-user.target for CLI, graphical.target for GUI).
    * `systemctl get-default`: Shows the current default boot target.
* **Creating Custom Service Units:**
    * You can create your own `.service` files to run custom applications or scripts as system services.
    * **Example (`/etc/systemd/system/my_app.service`):**
        ```ini
        [Unit]
        Description=My Custom Application Service
        After=network.target

        [Service]
        ExecStart=/usr/local/bin/my_app_script.sh
        Restart=always
        User=myuser
        Group=mygroup

        [Install]
        WantedBy=multi-user.target
        ```
    * After creating/modifying:
        1.  `sudo systemctl daemon-reload`: Reloads `systemd` configuration to detect new/changed unit files.
        2.  `sudo systemctl enable my_app.service`: Enables the service to start on boot.
        3.  `sudo systemctl start my_app.service`: Starts the service immediately.

### 14.2 Init Systems

* An init system is the **first process launched by the kernel (PID 1)** and is responsible for booting the rest of the user-space system.
* **`systemd`:** (Current standard). Parallelizes service startup, provides on-demand service activation, integrates with logging (`journald`), and offers many other features.
* **`SysVinit` (System V Init):** Older, traditional init system. Services are started sequentially based on runlevels. Still found on very old systems or embedded devices. Uses `init.d` scripts (e.g., `/etc/init.d/apache2 start`).
* **`Upstart`:** Developed by Ubuntu as an event-based replacement for `SysVinit`, primarily used by older Ubuntu versions before the switch to `systemd`.

---

## 15. Kernel and System Tuning

### 15.1 Kernel Modules

* Kernel modules are pieces of code that can be loaded and unloaded into the kernel as needed, extending its functionality without recompiling the entire kernel.
* `lsmod`: Lists currently loaded kernel modules.
* `modinfo <module_name>`: Displays information about a kernel module.
* `modprobe <module_name>`: Automatically loads a kernel module and its dependencies.
* `rmmod <module_name>`: Unloads a kernel module (if not in use).
* **Blacklisting modules:** Prevent specific modules from loading at boot (configured in `/etc/modprobe.d/`).

### 15.2 Kernel Parameters (`sysctl`)

* `sysctl` allows you to view and modify kernel parameters at runtime. These parameters control various aspects of the kernel's behavior (networking, memory, security).
* **`sysctl -a`:** Displays all current kernel parameters and their values.
* **Temporary change:** `sudo sysctl -w <parameter_name>=<value>`
    * **Example:** `sudo sysctl -w net.ipv4.ip_forward=1` (enables IP forwarding)
* **Persistent change:** Edit `/etc/sysctl.conf` or add new files in `/etc/sysctl.d/`. After editing, apply changes with `sudo sysctl -p`.
    * **Example:** Add `vm.swappiness=10` to `/etc/sysctl.conf` to reduce how aggressively the system uses swap.

### 15.3 Resource Limits (`ulimit`)

* `ulimit` (user limit) is a shell built-in command that controls the resources available to processes started by the current shell.
* **Types of limits:** Number of open files, maximum process size, CPU time, stack size, etc.
* `ulimit -a`: Shows all current limits.
* `ulimit -n`: Shows the maximum number of open file descriptors.
* **Setting limits (temporary for current shell):** `ulimit -n 65535` (sets open file limit).
* **Setting limits (persistent):**
    * **Per-user:** Add `ulimit` commands to `~/.bashrc` or `~/.profile`.
    * **System-wide:** Edit `/etc/security/limits.conf` (requires re-login for changes to apply).
        * **Example in `limits.conf`:**
            ```
            * soft nofile 65535
            * hard nofile 65535
            ```
            (Sets soft and hard limits for all users (`*`) on the number of open files (`nofile`)).

---

## 16. Advanced User and Group Management

### 16.1 Advanced User Management

* **Password Policies:** Enforce strong password policies (length, complexity, expiration) by configuring `/etc/login.defs` and using tools like `chage`.
    * `chage -l <username>`: Lists password aging information.
    * `chage -M 90 <username>`: Sets password max age to 90 days.
* **Account Locking/Unlocking:**
    * `passwd -l <username>`: Locks a user's password (prevents login).
    * `passwd -u <username>`: Unlocks a user's password.
* **Disabling Accounts:**
    * `usermod -L <username>`: Locks the account without changing the password.
    * `usermod -s /sbin/nologin <username>`: Sets the user's shell to `nologin`, preventing interactive logins.

### 16.2 Sudo Configuration (`visudo`)

* Always use `visudo` to edit `/etc/sudoers` to prevent syntax errors. `visudo` opens the file in a safe environment (usually `vi` or `nano`) and performs syntax checks on exit.
* **NOPASSWD:** Allows a user or group to run specific commands without entering a password.
    * `%devops ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart nginx` (Members of `devops` group can restart Nginx without password).
* **Runas Specification:** Specify which users/groups a command can be run as.
    * `user ALL=(root) /usr/sbin/shutdown` (user can run shutdown only as root).
* **Aliases:** Define command aliases within `sudoers` for easier management.
    * `Cmnd_Alias APACHE_CMDS = /usr/sbin/apachectl *, /usr/bin/systemctl restart apache2`
    * `devops ALL=(ALL) APACHE_CMDS`

### 16.3 PAM (Pluggable Authentication Modules)

* PAM is a framework that allows system administrators to plug in different authentication modules (e.g., password, biometrics, smart cards) without recompiling applications.
* **Configuration:** PAM configurations are typically located in `/etc/pam.d/`. Each service (e.g., `sshd`, `login`, `sudo`) has its own PAM configuration file.
* **Understanding PAM files:**
    * Lines specify module types (auth, account, password, session), control flags (required, requisite, sufficient, optional), and modules.
    * **Example (common password module):** `password    requisite     pam_pwquality.so retry=3 minlen=8 difok=3` (Enforces password quality).
* **Use Cases:**
    * Enforcing password complexity.
    * Implementing multi-factor authentication.
    * Integrating with LDAP or Active Directory for authentication.
    * Restricting user logins based on time of day or IP address.

---
