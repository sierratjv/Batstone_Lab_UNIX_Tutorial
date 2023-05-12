# Tips_and_Tricks
UNIX commands for beginners
# Useful websites to learn basix UNIX commands:
UNIX Tutorial for Beginners. http://www.ee.surrey.ac.uk/Teaching/Unix/index.html. 
# Contents:
[Learn these first](#learn-these-first) <br>
[List (ls)](#list-ls) <br>
[Access rights of files](#access-rights-of-files) <br>
[Environmental variable](#environmental-variable) <br>
[Info server](#info-server) <br>
[Working in background (nohup, screen)](#working-in-background-nohup-screen) <br>
[Symbolic link](#symbolic-link) <br>
[Tab complete](#tab-complete) <br>
[Pathnames](#pathnames)  <br>

## Learn these first

### Symobols in UNIX
``.`` represents the current directory. 

``..`` represents the parent of the current directory. 

``~`` represents the home directory.

### List (ls)
To list content in a directory, type ``ls``.

To list hidden files (files beginning with ``.``), type ``ls -a``. 

To list access rights of files, type ``ls -l``. 

### Change directory (cd)
To move ahead one directory, type ``cd directory`` (``directory`` is the name of the directory you want to go to).

To move back one directory, tyep ``cd ..``.

### Access rights of files
Read [this website](https://www.pluralsight.com/blog/it-ops/linux-file-permissions) for instructions.

To list access rights of files, type ``ls -l``. 

An example of the result is ``-rwxrw-r-- 1 ee51ab beng95 2450 Sept29 11:52 file1``. 

### Environmental variable
It is global system variable accessible by all the processes/users running under the Operating System (OS), such as Windows, macOS and Linux. It is useful for storing system-wide values.  
- To show all environmental variables, type ``env``.
- Steps for creating a environmental variable for directory: <br>
1. Have the pathname of the directory ready. See [Pathnames](#pathnames) of how to find the pathname; <br>
2. Type ``export PATH="pathname"``(``PATH`` is the name of the variable; call it whatever you want); <br> 
3. Then in any directories, type ``cd $PATH`` will allow you to enter that directory. 

#### PATH variable (one type of environmental variable)
It contains a list of directories which the system checks before running a command. 

An example of PATH looks like ``/usr/local/python3/Python-3.5.1:/usr/local/spades/version.3.15.2/bin:.:/home/xingyuan/bin:/usr/lib64/qt-3.3/bin:/usr/lib64/openmpi/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/opt/dell/srvadmin/bin:/home/xingyuan/.local/bin:/home/xingyuan/bin``.

``spades`` is a genome assembler program which is part of the PATH. This allows the user to run ``spades`` at any directory by typing ``spades.py [options] -o <output_dir>``. 

- To view PATH, type ``echo $PATH``.
- When adding program directories to the PATH variable, add to the **beginning** of the PATH by typing ``export PATH=/the/file/path:$PATH``. This is because the directories near the start will be ran first. Read more [here](https://stackoverflow.com/questions/9546324/adding-a-directory-to-the-path-environment-variable-in-windows#:~:text=The%20path%20works%20like%20first,the%20beginning%20of%20the%20command). 
- To see the changes which you made on the PATH variable, you have to log out (types ``exit`` if you are on a server) and then log in again. Then type ``echo $PATH`` to see if changes are made successfully. 

Reference: 
[How To View and Update the Linux PATH Environment Variable](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable#step-3-mdash-permanently-adding-a-directory-to-the-path-variable)

### Info server
**Things to pay attention**:
- Run programs on **nodes**. Running programs on the head (which is the place when you login) will greatly slow the system.  

Login to Info sever head: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). Type ``exit`` to leave the server.

Login to nodes, for example, info114: type ``ssh info114``. Then type ``password``. Type "exit" to leave the node and go back to the server head. 

### List (ls)
To list content in a directory, type ``ls``.

To list hidden files (files beginning with ``.``), type ``ls -a``. 

To list access rights of files, type ``ls -l``. 

### Symbolic link
Read more [here](https://www.freecodecamp.org/news/symlink-tutorial-in-linux-how-to-create-and-remove-a-symbolic-link/).

To create symbolic link, type ``ln -s <path to the file/folder to be linked> <the path of the link to be created>``.

Troubleshooting: 
- When changing the path for creating the symbolic link, remember to redo the symbolic link. 

### Tab complete
This saves time for typing out a command. 

For example, if you want to go to the **Applications** directory, you can type **"cd Applications"**. Instead of typing out **"Applications"** in full, you can type **"App"** and the press **"Tab"**. If **"Applications"** is the only directory beginning with **"App"**, it will return you **"cd Applications"**. If not, it will return all files begining with **"App"**, and then press **"Tab"** to select the file you want. 

### Working in background (nohup, screen)
