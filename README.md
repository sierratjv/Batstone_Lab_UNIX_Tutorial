# Tips_and_Tricks
UNIX commands for beginners

# Contents:
[Symbols in UNIX](#symobols-in-unix) <br>
[Learn these commands first](#learn-these-commands-first) <br>
[Useful commands to simplify things](#useful-commands-to-simplify-things) <br>
[Info server](#info-server) <br>
[Tab complete](#tab-complete) <br>


### Symobols in UNIX
``.`` represents the current directory. 

``..`` represents the parent of the current directory. 

``~`` represents the home directory.

## Learn these commands first

### Read [UNIX Tutorial for Beginners](http://www.ee.surrey.ac.uk/Teaching/Unix/index.html)

### List 
To list content in a directory, type ``ls``.

To list hidden files (files beginning with ``.``), type ``ls -a``. 

To list access rights of files, type ``ls -l``. Read [this website](https://www.pluralsight.com/blog/it-ops/linux-file-permissions) for instructions about how to change access rights. 

### Change directory 
To move ahead one directory, type ``cd directory`` (``directory`` is the name of the directory you want to go to).

To move back one directory, type ``cd ..``.

### Make directories
To make a new directory, type ``mkdir directory``(``directory`` is the name for that directory). Type ``ls`` to verify the directory is made successfully. 

### Remove files or directories
To delete a file, type ``rm file`` (``file`` is the name of the file).

To delete a directory, it has to be empty; then type ``rmdir directory`` (``directory`` is the name of the directory).

### Pathnames
To view the absolute pathname of a directory, ``cd`` to that directory first, then type ``pwd``.

## Useful commands to simplify things 

### Wildcards 
It allows you to select the files you want to list. 

To list files in the current directory beginning with **bio...**, type ``ls bio*`` .

To list files in the current directory ending with **...logy**, type ``ls *logy``.

## Shell Script
Steps for creating a shell script:
1.  Create a shell script <br>
```shell_script_1``` <br>
```nano shell_script.sh``` <br>
2. In the opened text editor, type the following <br>
```shell_script_2``` <br>
```#!/bin/bash``` <br>
```command you want to run``` <br>
The first line tells what program (e.g. bash) to use to interpret the script. The second line is the command you want to run. <br>
3.  execute the shell script <br>
```shell_script_3``` <br>
```bash shell_script.sh``` <br>

### Environmental variable
This is very useful for going to a directory or running a program because it allows to do these at any directories. 

To show all environmental variables, type ``env``.

Steps for creating a environmental variable: <br>
1. Have the pathname ready; <br>
2. Type ``export AAA="pathname"``(``AAA`` is the name of the variable); <br> 
3. Then in any directories, type ``cd $AAA`` will allow you to enter that directory. If it is a program, typing ``$AAA`` in any directories can run this program. 
4. Type ``echo $AAA``

**PATH variable - one type of environmental variable**
It contains a list of directories which the system checks before running a command. Thus, it is useful to put the pathname of a program there if if you want to run that program. Read more about on [this website](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable#step-3-mdash-permanently-adding-a-directory-to-the-path-variable). 

An example of PATH looks like ``/usr/local/python3/Python-3.5.1:/usr/local/spades/version.3.15.2/bin:.:/home/xingyuan/bin:/usr/lib64/qt-3.3/bin:/usr/lib64/openmpi/bin:/usr/local/bin:/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/opt/dell/srvadmin/bin:/home/xingyuan/.local/bin:/home/xingyuan/bin``.

``spades`` is a genome assembler program which is part of the PATH. This allows the user to run ``spades`` at any directory by typing ``spades.py [options] -o <output_dir>``. 

To view PATH, type ``echo $PATH``.

Steps for add a directory to the PATH variable:
1. Type ``nano ~/.bashrc`` to open a file called ``.bashrc``;
2. Type ``export PATH=/the/file/path:$PATH`` in the ``.bashrc`` file (``/the/file/path`` is the pathname of the directory you want to add);
3. Press ``Control+X``, then type ``Y`` to save the changes, then press ``Enter`` to exit ``.bashrc``;
4. To see the changes which you made on the PATH variable, you have to log out (types ``exit`` if you are on a server) and then log in again.
5. Type ``echo $PATH`` to see if changes are made successfully. Your new pathnames should be added to the start of the PATH variable. 

**Troubleshooting**:
- If the system still cannot find the program, check if the new directory is added to the **start of the PATH variable**. The command to do that is ``export PATH=/the/file/path:$PATH``. This may be because the directories near the start of the PATH variable will be ran first. Read more [here](https://stackoverflow.com/questions/9546324/adding-a-directory-to-the-path-environment-variable-in-windows#:~:text=The%20path%20works%20like%20first,the%20beginning%20of%20the%20command). 

### Symbolic link
Read more [here](https://www.freecodecamp.org/news/symlink-tutorial-in-linux-how-to-create-and-remove-a-symbolic-link/).

To create symbolic link, type ``ln -s <path to the file/folder to be linked> <the path of the link to be created>``.

Troubleshooting:
- When the system cannot find the symbolic link, check the pathname of the original files to see if they are the same one used to create the symbolic link. If not, re-create the symbolic link with the correct pathname. 

### Tab complete
This saves time for typing out a command. 

For example, if you want to go to the **Applications** directory, you can type **"cd Applications"**. Instead of typing out **"Applications"** in full, you can type **"App"** and the press **"Tab"**. If **"Applications"** is the only directory beginning with **"App"**, it will return you **"cd Applications"**. If not, it will return all files begining with **"App"**, and then press **"Tab"** to select the file you want. 

### Working in background (nohup, screen)

## Info server
**Things to pay attention**:
- Run programs on **nodes**. Running programs on the head (which is the place when you login) will greatly slow the system.  

Login to Info sever head: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). Type ``exit`` to leave the server.

Login to nodes, for example, info114: type ``ssh info114``. Then type ``password``. Type "exit" to leave the node and go back to the server head. 
