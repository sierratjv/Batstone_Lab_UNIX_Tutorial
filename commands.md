# 1. Commands
[Go back to the main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)

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
Type ``ls``, and it will list contents in your current directory. 

Type ``ls -a``, and it will list hidden files (files beginning with ``.``) in your current directory.

Type ``ls --color``, it will list and colorize output in your current directory. 

Type ``ls -F``, it will list and classify the files in your current directory. For example, the name of a directory will have ``/`` at the end. 

Type ``ls -l``, it will list the infomation, such as file permissionns (drwx------), owner name, owner group, file size, last modification time. Learn about file permissions here: https://www.pluralsight.com/blog/it-ops/linux-file-permissions. 

Type ``ls -S``, it will list the files from largest size to smallest size.

Type ``man ls``, this will open a manual page for ls, it has all the options of how to use ls. Press <kbd>q</kbd> to quit the manual.

You can also combline the flags, such as ``ls -lS``.

## man 
Type ``man cmd`` to see the manual of a command (``cmd`` is the command you want to look up).

Type ``man man`` to open a manual page for man. 

## cd 
To move ahead one directory, type ``cd dir`` (``dir`` is the directory you want to go to).

To move back one directory, type ``cd ..``.

To move to home directory from any directories, type ``cd`` or ``cd ~``. 

## pwd 
Type ``pwd``, it will print the path of your current directory.

## mkdir 
To make a new directory, type ``mkdir dir``(``dir`` is the name for that directory). Type ``ls`` to verify the directory is made successfully. 

## touch 
Type ``touch file1 file2 file3``, it will create file1, file2, file3. 

## cp 
Type ``cp file1 file2``, it will copy contents in file1 to file2 (if file2 exists, it will ask whether to overwrite it or not; if file2 does not exit, it will create file2).

Type ``cp file{1..5} folder``, it will copy file1, file2, file3, file4, file5 to a directory called folder (folder needs to be existed before copying files). 

## rm 
**This command can be dangerous. For example, ``rm *`` will remove everything from your current directory. There is no recovery for removed files.**

To delete a file, type ``rm file`` . 

To delete an empty directory, type ``rmdir dir``. 

Type ``rm -r dir``, it will go into to the directory and removes everyting. 

## mv 
Type ``mkdir dir1 dir2`` to create two directories named dir1 and dir2. Type ``ls`` to confirm.

Type ``cd dir1`` to go into dir1, and type ``touch file1, file2, file3`` to create 3 files in dir1. Type ``ls`` to confirm. Type ``cd ..`` to exit dir1.

Type ``mv dir1/* dir2/`` to move contents from dir1 to dir2 (* symbol selects all files in dir1). Type ``ls dir1``, it should return nothing, meaning dir1 is empty. Type ``ls dir2``, you should have file1, file2, file3 in dir2, meaning the 3 files are transferred from dir1 to dir2.

## cat

## rev

## more

## less

## head 

## tail

## wc

## sort 

## tr

## cut

## split

## grep

## find

## wget, curl

## rsh, ssh

## scp 

## history

## alias

## toss

## rsync 

## 

