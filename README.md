# Tips_and_Tricks
UNIX commands for beginners
# Useful websites to learn basix UNIX commands:
UNIX Tutorial for Beginners. http://www.ee.surrey.ac.uk/Teaching/Unix/index.html. 
# Contents:
[Access rights of files](#access-rights-of-files) <br>
[Environmental variable](#environmental-variable) <br>
[Info server](#info-server) <br>
[List (ls)](#list-ls) <br>
[Working in background (nohup, screen)](#working-in-background-nohup-screen) <br>
[Symbolic link](#symbolic-link) <br>
[Tab complete](#tab-complete) <br>
[Pathnames](#pathnames)  <br>

## Access rights of files
Read this website for instructions: https://www.pluralsight.com/blog/it-ops/linux-file-permissions.

To list access rights of files, type ``ls -l``. 

An example of the result is ``-rwxrw-r-- 1 ee51ab beng95 2450 Sept29 11:52 file1``. 

## Environmental variable
Reference: https://www3.ntu.edu.sg/home/ehchua/programming/howto/Environment_Variables.html#:~:text=You%20can%20set%20an%20environment,.%20)%20is%20hidden%20by%20default.

It is global system variable accessible by all the processes/users running under the Operating System (OS), such as Windows, macOS and Linux. It is useful for storing system-wide values.

PATH is one type of environmental variable which stores directory.

Steps for creating a PATH environmental variable for directory: <br>
1. Have the pathname of the file ready. See [Pathnames](#pathnames) of how to find the pathname; <br>
2. Type ``export PATH="pathname"``(``PATH`` is the name of the variable; call it whatever you want); <br> 
3. Then in any directories, type ``cd $PATH`` will allow you to enter that directory.

## Info server
Login to Info sever: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). 

Exit Info server: type ``exit``.

## List (ls)
To list content in a directory, type ``ls``.

To list hidden files (files beginning with ``.``), type ``ls -a``. 

To list access rights of files, type ``ls -l``. 

## Pathnames
To find the absoulte path of a directory, in that directory, type ``pwd``.

## Symbolic link

Troubleshooting: 

- When changing the path for creating the symbolic link, remember to redo the symbolic link. 

## Tab complete
This saves time for typing out a command. 

For example, if you want to go to the **Applications** directory, you can type **"cd Applications"**. Instead of typing out **"Applications"** in full, you can type **"App"** and the press **"Tab"**. If **"Applications"** is the only directory beginning with **"App"**, it will return you **"cd Applications"**. If not, it will return all files begining with **"App"**, and then press **"Tab"** to select the file you want. 

## Working in background (nohup, screen)
