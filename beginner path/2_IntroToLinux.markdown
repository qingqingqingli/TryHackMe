## linux commands

- su
- ls
- cat
- echo
- touch
- ssh
- &&
- &
- $
- |
- ;
- chmod
- chown
    - allow us to change the user and group of any file
    - You can only use chown if you are "above" that other user, meaning that chown is best done with the root(administrator) user.
    - You can also use chown without specifying a group. So you can just use chown user file if you only wanted to change the user but keep the group.
    
- rm
- mv
- ">"
- ">>"
- cp
- cd && mkdir

- ln 
    - ln is a weird one, because it has two different main uses. One of those is what's known as "hard linking", which completely duplicates the file, and links the duplicate to the original copy. Meaning What ever is done to the created link, is also done to the original file. It's important to be very careful with hard links, as depending on what you're doing it can be very easy to erase data from a file. The ln syntax is ```ln source destination```.
    - The next form of linking is symbolic linking(symlink). While a hard linked file contains the data in the original file, a symbolic link is just a glorified reference. Meaning that the actual symbolic link has no data in it at all, it's just a reference to another file. The syntax for a symbolic link is the exact same, but it uses the -s flag, so to create a symbolic link, you would run ```ln -s <file> <destination>```.
    
- find
    - It is worth noting that find is recursive, so it searches every directory that is in the original directory you provided. Meaning that if you were to run ```find /```, it would list every file on the OS. Another thing worth noting is that it can only list files in directories that you have permission to access, meaning you cant just list every file as every user.
    - The true power of this command though comes from the parameters you can provide it. You can use ```find dir -user```, to list every file owned by a specific user; you can use ```find dir -group``` to list every file owned by a specific group. The sheer customizability of the command is it's most powerful feature.
    
- grep
    - It allows you find data inside of data. When working with large files, or a large output, it is arguably the best way to narrow the output down to better find what your looking for. The syntax of the command is ```grep <string> <file>``` however file is optional if you're using piping.
    
- sudo
    - whoami is just a command that states your current user.
    - As you can see when using sudo the command is run as root. It is important to note that you need to have your current user's password to use it. Again like Windows, not every user has permission to use sudo, but most Linux OS' set up a user that has permissions when you install it. 
- Adding users and groups
    - t's important to note that only root has permissions to add users and groups, as seen with the failure when I attempted to run the commands without sudo. You may be wondering how to add a user to a group. that is done with the usermod command, the syntax for that is ```usermod -a -G <groups seperated by commas> <user>```. Meaning if I wanted to add the user noot to b I would run ```usermod -a -G b noot```.
    - id is a command that allows you to view basic information about a user.
    
- nano

- Basic shell scirpting
    - It is worth noting that the sh extension isn't technically needed if you provide a shebang(#!) , and then the path to the shell we want to use to run our command. The shebang MUST be in the beginning of the file.
    
- Important files and directories
    -  It is worth noting exactly how the linux file system works. Everything on the linux file system extends from "/". / is the equivalent of C: in Windows. Meaning that for example if you were to delete "/", you would delete every file on your system.
    - /etc/passwd - Stores user information - Often used to see all the users on a system
    - /etc/shadow - Has all the passwords of these users. 
    - /tmp - Every file inside it gets deleted upon shutdown - used for temporary files
    - /etc/sudoers - Used to control the sudo permissions of every user on the system
    - /home - The directory where all your downloads, documents etc are. - The equivalent on Windows is C:\Users\<user>
    - /root - The root user's home directory - The equivilent on Windows is C:\Users\Administrator
    - /usr - Where all your software is installed 
    - /bin and /sbin - Used for system critical files - DO NOT DELETE
    - /var - The Linux miscellaneous directory, a myriad of processes store data in /var
    - $PATH - Stores all the binaries you're able to run - same as $PATH on Windows. $PATH is an environment variable that contains all the binaries you're able to execute. 
    
- apt
    - A package is essentially a program, you can think of it like an exe file on windows. To install packages you need root permissions, as each package will likely modify some system critical directories such as /usr. The syntax to install packages is apt install package.

- processes
    - Every binary you execute on linux, is a process while it's run. A process is just another word for a running program. A list of user created processes can be viewed with the ```ps``` command
    - While this is technically all the user created processes, it's likely not the information you're looking for if you're going to be examining processes. To view a list of all system processes, you have to use the ```-ef``` flag
    - Every process that is currently running on the system is listed, along with some basic information about the process. Arguably the most interesting part about that list is the second column, the 3-5 digit numbers. Those are known as Process ID's(PID's) and they're how you interact with the processes. 90% of the time you'll likely be wanting to stop these processes and that's done with the ```kill``` command(an apt choice of naming I know). 
    - After running kill, the process no longer shows up! Another useful way to interact with PID's is through the command ```top```. ```top``` shows you what processes are taking up the most system resources, which allows you to manage the resource allocation on your system by killing unneeded processes.
    
## ssh

SSH is the act of remotely accessing a machine. SSH allows you to run commands interactively on the remote machine. This is done through the use of a program on the target machine, which allows the ssh client to interface with the target host.ln is a weird one, because it has two different main uses. One of those is what's known as "hard linking", which completely duplicates the file, and links the duplicate to the original copy. Meaning What ever is done to the created link, is also done to the original file. 

While the most common usage of a regular operating system is graphical(allowing you to see pictures, web browsers, file managers etc.) SSH works through a command line, meaning anything done on the target machine will be done through a command prompt similar to this.

 It is an invaluable tool, and how you will be accessing this machine to learn and to do the challenges. Depending on the operating system there are different ways of SSHing into a machine. This section will purely focus on the windows way(PuTTY), and after we learn more about linux commands, and how they work, we'll return back to this section and learn about the linux method.
