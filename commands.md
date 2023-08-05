# 1. Commands
[Go back to the main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)

**If any commands below that do not work as expected, use the info cluster. Ask Dr. Golding for an account. Type ``ssh username@info.mcmaster.ca`` and the password to login (You don't see the password when typing).**

## Symbols
``.`` represents the current directory. 

``..`` represents the parent of the current directory. 

``~`` represents the home directory.

## Using Keyboard
Press <kbd>Control</kbd> + <kbd>C</kbd> to delete the command that you type in.

Press <kbd>↑</kbd> to search the commands that you typed before.

Tab complete: if you want to save time for typing ``cd Desktop``, you can type ``cd Des`` and the press <kbd>Tab</kbd>. If ``Destop`` is the only directory beginning with ``Des...``, it will complete the command ``cd Desktop``. If not, it will return all files begining with ``Des...``, and then press <kbd>Tab</kbd> to select the file you want. 

Press <kbd>Control</kbd> + <kbd>A</kbd> to go to the beginning of a command.

Press <kbd>Control</kbd> + <kbd>E</kbd> to go to the end of a command.

Press <kbd>Control</kbd> + <kbd>Z</kbd> to stop a command that is running.

## ls 
**List directory contents**

Type ``ls``, and it will list contents in your current directory. 

Type ``ls -a``, and it will list hidden files (files beginning with ``.``) in your current directory.

Type ``ls --color``, it will list and colorize output in your current directory. 

Type ``ls -F``, it will list and classify the files in your current directory. For example, the name of a directory will have ``/`` at the end. 

Type ``ls -l``, it will list the infomation, such as file permissionns (drwx------), owner name, owner group, file size, last modification time. Learn about file permissions here: https://www.pluralsight.com/blog/it-ops/linux-file-permissions. 

Type ``ls -S``, it will list the files from largest size to smallest size.

Type ``man ls``, this will open a manual page for ls, it has all the options of how to use ls. Press <kbd>q</kbd> to quit the manual.

You can also combline the flags, such as ``ls -lS``.

## man 
**An interface to the on-line reference manuals**

Type ``man cmd`` to see the manual of a command (``cmd`` is the command you want to look up).

Type ``man man`` to open a manual page for man. 

## cd 
**Change the current directory** 

To move ahead one directory, type ``cd dir`` (``dir`` is the directory you want to go to).

To move back one directory, type ``cd ..``.

To move to home directory from any directories, type ``cd`` or ``cd ~``. 

## pwd 
**Print name of current/working directory**

Type ``pwd``, it will print the path of your current directory.

## mkdir 
**Make directories**

To make a new directory, type ``mkdir dir``(``dir`` is the name for that directory). Type ``ls`` to verify the directory is made successfully. 

## touch 
**Create files** 

Type ``touch file1 file2 file3``, it will create file1, file2, file3. 

## cp 
**copy files and directories**

Type ``cp file1 file2``, it will copy contents in file1 to file2 (if file2 exists, it will ask whether to overwrite it or not; if file2 does not exit, it will create file2).

Type ``cp file{1..5} folder``, it will copy file1, file2, file3, file4, file5 to a directory called folder (folder needs to be existed before copying files). 

## rm 
**Remove files or directories**

**This command can be dangerous. For example, ``rm *`` will remove everything from your current directory. There is no recovery for removed files.**

To delete a file, type ``rm file`` . 

To delete an empty directory, type ``rmdir dir``. 

Type ``rm -r dir``, it will go into to the directory and removes this directory and every files inside. 

## mv 
**Move files** 

Type ``mkdir dir1 dir2`` to create two directories named dir1 and dir2. Type ``ls`` to confirm.

Type ``cd dir1`` to go into dir1, and type ``touch file{1..3}`` to create 3 files in dir1. Type ``ls`` to confirm. Type ``cd ..`` to exit dir1.

Type ``mv dir1/* dir2/`` to move contents from dir1 to dir2 (* symbol selects all files in dir1). Type ``ls dir1``, it should return nothing, meaning dir1 is empty. Type ``ls dir2``, you should have file1, file2, file3 in dir2, meaning the 3 files are transferred from dir1 to dir2.

**Rename files or directories** 

Type ``mv dir1 dir3``, this will change the name of dir1 to dir3. 

## open
**View pdf or html**

Type ``open file`` to open a .html or a .pdf file. 

## cat
**View files** 

Type ``nano file`` to create and edit a file (nano is a text editor). Type ``math, physics, chemistry, biology`` to create contents in the file. Press <kbd>Control</kbd> + <kbd>X</kbd>, then press <kbd>Y</kbd>, and press <kbd>Enter</kbd> to save and close the file. Type ``cat file``, and you should see ``math, physics, chemistry, biology``. 

**Combine contents from different files** 

Type ``nano file2``, and write ``geography, history, computer science``. Save and close file2. Type ``cat file2`` to check the contents. Type ``cat file file2``, and you should see:
```
math, physics, chemistry, biology
geography, history, computer science
```
Type ``cat file file2 > file3`` to redirect the output to file3. Type ``cat file3`` and you should see:
```
math, physics, chemistry, biology
geography, history, computer science
```

## more
**View files** 

Type ``more file`` to view a file. This will read how big is your screen and give you a screenful information. Press <kbd>Enter</kbd> to see the rest of the contents. Press <kbd>q</kbd> to stop viewing the file.

## less
**View files** 

Type ``less file`` to view a file. This is similar to more. Press <kbd>q</kbd> to stop viewing the file.

## rev
**Reverse lines of files** 

Type ``nano file`` to create a file and type ``abcdef``. Save and close the file. Type ``cat file`` and it should give ``abcdef``. Type ``rev file`` and it should give ``fedcba``.

## head 
**Output the first part of files** 

Type ``nano file``. Type number 1 to 15 vertically. Save and close the file. Type ``cat file`` and it should give:
```
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
```
Type ``head file`` and it should give the first 10 lines of the file (1 to 10). Type ``head -12 file`` and it should give the first 12 lines (1 to 12). 

## tail
**Output the last part of files** 

Type ``tail file`` and it should give the last 10 lines (6 to 15). 

## wc
**Count number of files in a directory** 

Type ``touch file{1..10}`` to create 10 files. Type ``ls file*`` (* symbol will match with any characters after "e"), and it should give ``file1  file10  file2  file3  file4  file5  file6  file7  file8  file9``. Type ``ls file* | wc -l``, and it should give ``10`` (| symbol takes the output from the previous command and passes to the next command.)

## sort

## tr
**Translate or delete characters** 

Type ``nano file`` and write ``ATCG``. Save and close the file. Type ``more file`` and it should give ``ATCG``. 

## cut

## split

## grep
**Get a pattern from a files**

Type ``nano file``. Write these words ``biology biology chemistry physics physics physics`` in the file. Save and close the file. Type ``more file`` to check. 

## find

## wget, curl

## rsh, ssh

## scp 

## history

## alias

## toss

## rsync 

## .bashrc

[Go back to the main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)
