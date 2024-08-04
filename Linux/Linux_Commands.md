Command	Function

man *command*            help command
open *~/path*            opens the specified folder in the GUI
cat **filename**         opens the specified file in the terminal 
cat > **filename**       creats a file and the editor is activated
>                        redirection
|                        translate 
^c                       to save the file and exit the editor

pwd	                     Shows the current working directory’s path
whoami                   Shows who are you logged in as
sudo                     Runs a command as a superuser

ls	                     lists a directory’s content
ls -a                    list all files including hidden
ls -l                    list long all the files
ls -R                    recursively opens all the folders in the current folder
            
cd	                     changes the working directory to home directory
cd ..                    previous folder
cd ../folder./path       to change the folders, we can use the path

mkdir	                 Creates a new directory
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
-iname for non casesensitive

chmod u=rwx,g=rw,o=r *directoryName*         	Modifies a file’s read, write, and execute permissions
chmod 777 OR chmod 421 *FileName*               4=read(r) 2=right(w) 1=execute(x) 

chown [OPTIONS] USER[:GROUP] *FileName*	            Changes a file, directory, or symbolic link’s ownership
chown *username* *FileName*                         To change the owner of a file or directory to a specified user
chown *:groupname* *FileName*                       To change the group of a file or directory to a specified group
chown *username:groupname* *FileName*               To change both the user and group ownership
chown -R *username:groupname* *directoryName*       To change the ownership of a directory and all its contents recursively,
chown --reference=*reference_file* *target_file*    To change the owner of a f/d to match the owner of another f/d

file	Checks a file’s type
zip and unzip	Creates and extracts a ZIP archive
tar	Archives files without compression in a TAR format
nano, vi, and jed	Edits a file with a text editor
cat	Lists, combines, and writes a file’s content as a standard output
grep	Searches a string within a file
sed	Finds, replaces, or deletes patterns in a file
awk	Finds and manipulates patterns in a file
sort	Reorders a file’s content
cut	Sections and prints lines from a file
tee	Prints command outputs in Terminal and a file

su	Runs programs in the current shell as another user
useradd and userdel	Creates and removes a user account
top	Displays running processes and the system’s resource usage
htop	Works like top but with an interactive user interface
ps	Creates a snapshot of all running processes
uname	Prints information about your machine’s kernel, name, and hardware
hostname	Shows your system’s hostname
time	Calculates commands’ execution time
systemctl	Manages system services
watch	Runs another command continuously
jobs	Displays a shell’s running processes with their statuses
kill	Terminates a running process
shutdown	Turns off or restarts the system
ping	Checks the system’s network connectivity
wget	Downloads files from a URL
curl	Transmits data between servers using URLs
scp	Securely copies files or directories to another system
rsync	Synchronizes content between directories or machines
lfconfig	Displays the system’s network interfaces and their configurations
netstat	Shows the system’s network information, like routing and sockets
traceroute	Tracks a packet’s hops to its destination
nslookup	Queries a domain’s IP address and vice versa
dig	Displays DNS information, including record types
history	Lists previously run commands
man	Shows a command’s manual
echo	Prints a message as a standard output
ln	Links files or directories
alias and unalias	Sets and removes an alias for a file or command
cal	Displays a calendar in Terminal
apt-get	Manages Debian-based distros package libraries