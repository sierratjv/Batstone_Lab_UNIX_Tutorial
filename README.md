# Tips_and_Tricks

## First learn UNIX commands on [this website](http://www.ee.surrey.ac.uk/Teaching/Unix/).

## Symobols in UNIX
``.`` represents the current directory. 

``..`` represents the parent of the current directory. 

``~`` represents the home directory.

## Keyboard

Press ``Enter`` to run the command that you type in. 

Delete the command that you type in: press ``Control``+``C``.

Use ``↑`` to search the commands that you typed before.

Tab complete: if you want to save time for typing ``cd Desktop``, you can type ``cd Des`` and the press ``Tab``. If ``Destop`` is the only directory beginning with ``Des...``, it will complete the command ``cd Desktop``. If not, it will return all files begining with ``Des...``, and then press ``Tab`` to select the file you want. 

## List 
To list content in a directory, type ``ls``.

To list hidden files (files beginning with ``.``), type ``ls -a``. 

To list access rights of files, type ``ls -l``. Read [this website](https://www.pluralsight.com/blog/it-ops/linux-file-permissions) for instructions about how to change access rights. 

## Change directory 
To move ahead one directory, type ``cd directory`` (``directory`` is the name of the directory you want to go to).

To move back one directory, type ``cd ..``.

## Make directories
To make a new directory, type ``mkdir directory``(``directory`` is the name for that directory). Type ``ls`` to verify the directory is made successfully. 

## Remove files or directories
To delete a file, type ``rm file`` (``file`` is the name of the file).

To delete a directory, it has to be empty; then type ``rmdir directory`` (``directory`` is the name of the directory).

## Pathnames
To view the absolute pathname of a directory, ``cd`` to that directory first, then type ``pwd``.

## Wildcards 
To list files in the current directory beginning with **bio...**, type ``ls bio*`` .

To list files in the current directory ending with **...logy**, type ``ls *logy``.

## Opening and Reading Files
To open file in a new window, type ``less document`` (``document`` is the name of the file).

To close the file, type ``q`` and press ``Enter``.

To search for a certain word in the file, type ``/word`` and press ``Enter`` (``word`` is the word you want to search for). Press ``n`` to go to the next word.

## Shell Script
Steps for creating a shell script:
1.  Create a shell script <br>
```nano shell_script.sh``` <br>
2. In the opened text editor, type the following <br>
```#!/bin/bash``` <br>
```command you want to run``` <br>
The first line tells what program (e.g. bash) to use to interpret the script. The second line is the command you want to run. <br>
3.  execute the shell script <br>
```bash shell_script.sh``` <br>

## Environmental variable
To show all environmental variables, type ``env``.

Steps for creating a environmental variable: <br>
1. Have the pathname ready; <br>
2. Type ``export AAA="pathname"``(``AAA`` is the name of the variable); <br> 
3. Then in any directories, type ``cd $AAA`` will allow you to enter that directory. If it is a program, typing ``$AAA`` in any directories can run this program. 
4. Type ``echo $AAA``

**PATH variable - one type of environmental variable**
Read about PATH variavle on [this website](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable#step-3-mdash-permanently-adding-a-directory-to-the-path-variable). 

To view PATH, type ``echo $PATH``.

Steps for adding a directory to the PATH variable:
1. Type ``nano ~/.bashrc`` to open a file called ``.bashrc``;
2. Type ``export PATH=/the/file/path:$PATH`` in the ``.bashrc`` file (``/the/file/path`` is the pathname of the directory you want to add);
3. Press ``Control``+``X``, then type ``Y`` to save the changes, then press ``Enter`` to exit ``.bashrc``;
4. To see the changes which you made on the PATH variable, you have to log out (types ``exit`` if you are on a server) and then log in again.
5. Type ``echo $PATH`` to see if changes are made successfully. Your new pathnames should be added to the start of the PATH variable. 

**Troubleshooting:**
- If the system still cannot find the program, check if the new directory is added to the **start of the PATH variable**. The command to do that is ``export PATH=/the/file/path:$PATH``. The problem may be because the directories near the start of the PATH variable will be ran first. Read more [here](https://stackoverflow.com/questions/9546324/adding-a-directory-to-the-path-environment-variable-in-windows#:~:text=The%20path%20works%20like%20first,the%20beginning%20of%20the%20command). 

## Symbolic link
Read about symbolic link on [this webiste](https://www.freecodecamp.org/news/symlink-tutorial-in-linux-how-to-create-and-remove-a-symbolic-link/).

To create symbolic link, type ``ln -s <path to the file/folder to be linked> <the path of the link to be created>``.

**Troubleshooting:**
- If the system cannot find the symbolic link, check the pathname of the original files to see if they are the same one used to create the symbolic link. If not, re-create the symbolic link with the correct pathname. 

## Working in background (nohup, screen)

## Info server
**Things to pay attention**:
- Run programs on **nodes**. Running programs on the head (which is the place when you login) will greatly slow the system.  

Login to head: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). Type ``exit`` to leave the server.

Login to nodes, for example, info114: type ``ssh info114``. Then type ``password``. Type ``exix`` to leave the node and go back to the server head. 
