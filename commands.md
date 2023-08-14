# 2. Commands
[Go to the main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)

**If any commands below that do not work as expected, use the info cluster. Ask Dr. Golding (golding@mcmaster.ca) for an account. Type ``ssh username@info.mcmaster.ca`` and the password to login (You don't see the password when typing).**

## Symbols
``.`` represents the current directory. 

``..`` represents the previous directory of your current directory. 

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

You can also combline the options, such as ``ls -lS``.

## man 
**An interface to the on-line reference manuals**

Type ``man ls`` to open a manual page for ls.

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

## ln -s
**Create a symbolic link to a file (shortcut to a file)**

Type ``touch file`` to create a file. Type ``ln -s file link`` to create symbolic link to the file. Type ``ls -l``. The symbolic link has an arrow pointing to the actual file. 
```
[xingyuan@infoserv unix_workshop]$ touch file
[xingyuan@infoserv unix_workshop]$ ln -s file link
[xingyuan@infoserv unix_workshop]$ ls -l
total 0
-rw-rw-r-- 1 xingyuan xingyuan 0 Aug  6 13:17 file
lrwxrwxrwx 1 xingyuan xingyuan 4 Aug  6 13:18 link -> file
```
When you want to create a copy of a very large file, you can use ``ln -s`` instead of ``cp``, since the size of symbolic link is smaller than the large file. For example, the contigs.fasta has a siz of 7262077, but size of the symbolic link is only 13.
```
[xingyuan@infoserv spades-101A]$ ls -l contigs.fasta link 
-rw-rw-r-- 1 xingyuan xingyuan 7262077 May 19 13:11 contigs.fasta
lrwxrwxrwx 1 xingyuan xingyuan      13 Aug 14 11:41 link -> contigs.fasta
```
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

Type ``less file`` to view a file. Type "/pattern", to search for word "pattern". Press <kbd>n</kbd> to go to the next pattern. Press <kbd>N</kbd> to go to the previous pattern. Press <kbd>q</kbd> to stop viewing the file.

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

## grep
**Find a pattern from files and print the lines with that patterns**

Type ``nano file``. Write these words ``biology biology chemistry physics physics physics`` in the file vertically. Save and close the file. Type ``more file`` to check. Type ``grep "biology" file``, it should give the two lines with "biology":
```
[xingyuan@infoserv unix_workshop]$ more file
biology 
biology 
chemistry 
physics 
physics 
physics
[xingyuan@infoserv unix_workshop]$ grep "biology" file
biology 
biology 
```

**Count the number of a pattern**

Type ``grep -c "biology" file``, and it should give ``2``:
```
[xingyuan@infoserv unix_workshop]$ grep -c "biology" file
2
```

## find
**Search for files**

Type ``find directory -iname "pattern"``. It will go to the directory and find the pattern.

In the example, searching "file" in the home directory (``~``). ``-iname`` option lets the match to be case insensitive, so ``file`` and ``File`` are found:
```
[xingyuan@infoserv ~]$ find ~ -iname "file"
/home/xingyuan/trash/file
/home/xingyuan/.conda/pkgs/perl-5.26.2-h14c3975_0/lib/5.26.2/x86_64-linux-thread-multi/auto/File
/home/xingyuan/.conda/pkgs/perl-5.26.2-h14c3975_0/lib/5.26.2/x86_64-linux-thread-multi/File
/home/xingyuan/.conda/pkgs/perl-5.26.2-h14c3975_0/lib/5.26.2/TAP/Formatter/File
/home/xingyuan/.conda/pkgs/perl-5.26.2-h14c3975_0/lib/5.26.2/File
/home/xingyuan/.conda/pkgs/perl-file-which-1.23-pl526_0/lib/site_perl/5.26.2/x86_64-linux-thread-multi/auto/File
/home/xingyuan/.conda/pkgs/perl-file-which-1.23-pl526_0/lib/site_perl/5.26.2/File
```

## wget
**Download file from internet**

Type ``wget https://github.com/broadinstitute/picard/releases/download/3.1.0/picard.jar`` to download a program called picard. 

## ssh
**Connect to a remote computer**

Type ``username@info.mcmaster.ca`` to connect to info cluster. Enter the password. You don't see the password when you are typing. 

Type ``username@graham.computecanada.ca`` to connect to graham cluster. 

## scp 
**Copy a file from a remote computer to your local computer.**

Login to info cluster. Type ``touch file`` create a file. Type ``pwd`` to get the path to the file:
```
[xingyuan@infoserv unix_workshop]$ touch file
[xingyuan@infoserv unix_workshop]$ pwd
/home/xingyuan/unix_workshop
```
Open another screen, on your local computer, type ``scp username@info.mcmaster.ca:path/to/file destination``:
```
(base) MacBook-Pro: ~ > scp xingyuan@info.mcmaster.ca:/home/xingyuan/unix_workshop/file .
xingyuan@info.mcmaster.ca's password: 
(base) MacBook-Pro: ~ > ls
Applications/ Documents/    Library/      Music/        Public/       file
Desktop/      Downloads/    Movies/       Pictures/     Zotero/
```
The ``.`` means copying to the current directory. 

**Copy multiple files** 

On your local computer, type ``scp xingyuan@info.mcmaster.ca:/home/xingyuan/unix_workshop/\file* .`` (Use ``\`` in front of file*.):
```
(base) MacBook-Pro: ~ > scp xingyuan@info.mcmaster.ca:/home/xingyuan/unix_workshop/\file* .
xingyuan@info.mcmaster.ca's password: 
(base) MacBook-Pro: ~ > ls
Applications/ Downloads/    Music/        Zotero/       file3
Desktop/      Library/      Pictures/     file1         file4
Documents/    Movies/       Public/       file2         file5
(base) MacBook-Pro: ~ > 
``` 

## history
Type ``history`` to see the commands you typed before.

## alias
**Make your own commands**

Type ``alias ls="ls -F"``. The next time you type ``ls``, it is the same as typing ``ls -F``:
```
[xingyuan@infoserv ~]$ ls
2018_strains  R  rhizo_ee  snap  tools	trash  unix_workshop
[xingyuan@infoserv ~]$ alias ls="ls -F"
[xingyuan@infoserv ~]$ ls
2018_strains/  R/  rhizo_ee/  snap/  tools/  trash/  unix_workshop/
```

Type ``alias``. This will list the aliases you currently have. 

Other examples of aliases:
```
alias ls="ls --color -F"
alias rm="rm -i"
alias hi="history"
alias ll="ls -hl"
```

## variables
Type ``i=2`` to create a variable i. Type ``echo $i`` to show the variable:
```
[xingyuan@infoserv ~]$ i=2
[xingyuan@infoserv ~]$ echo $i
2
```
You can also store the output from a command into variable. For example, the output from ls is given to the variable i:
```
[xingyuan@info114 unix_workshop]$ ls
file1  file2  file3  file4  file5
[xingyuan@info114 unix_workshop]$ i=`ls`
[xingyuan@info114 unix_workshop]$ echo $i
file1 file2 file3 file4 file5
```

**PATH variable**

**Be careful of not overwrting the PATH variable when you add a new directory to it. Keep a copy of the PATH variable when you edit it for the first time**

It includes directories that will be checked when you run a command. When you type a command, it will search PATH to find a program to run that command. The command cannot be run if the program is not found. Type ``echo $PATH`` to show the PATH variable:
```
[xingyuan@infoserv ~]$ echo $PATH
/home/xingyuan/tools/GenAPI/bin:/home/xingyuan/tools/tbl2asn:/home/xingyuan/tools/interproscan-5.62-94.0:/home/xingyuan/tools/jdk-20.0.1/bin:/home/xingyuan/tools/barrnap:/usr/local/prokka/bin:/usr/local/perl5.24/perl-5.24.0/perl:/usr/local/mummer/current/:/home/xingyuan/tools/Spine-0.3.2:/usr/local/qualimap_v2.2.1:/usr/local/bwa/current:/usr/local/samtools/1.11/samtools:/usr/local/python3/Python-3.5.1:/usr/local/spades/version.3.15.2/bin:.:/home/xingyuan/bin:/usr/lib64/qt-3.3/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/home/xingyuan/.local/bin:/home/xingyuan/bin
```

## .bashrc
.bashrc is a script that will be run when you login to bash. It is useful to write your aliases and variables in the .bashrc file, so they become your default settings. 

.bashrc is located in your home directory. Type ``ls -a ~/`` to see .bashrc file. 

To edit the .bashrc, type ``nano .bashrc``. Lines beginning with ``# `` are comments. Add ``set -o noclobber`` to your .bashrc, which prevents overwriting a file. After you edit your .bashrc, exit and login to the bash again. The new settings should work now. 

Example of a .bashrc file
```
# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi

# Uncomment the following line if you don't like systemctl's auto-paging feature:
# export SYSTEMD_PAGER=

# type mc to do mkdir, cd, pwd at once
function mc() {  # make and change to directory
    mkdir $1;
    cd $1;
    pwd;
}

# no overwrite
set -o noclobber

# aliases
alias ls="ls --color -F"
alias rm="rm -i"
alias quast="/home/xingyuan/tools/quast-5.2.0/quast.py"
alias ssh="ssh -X"
alias hi="history"
alias ll="ls -hl"

# variables
TOOLS=/home/xingyuan/tools

# add directories to PATH
export PATH=/usr/local/python3/Python-3.5.1:/usr/local/spades/version.3.15.2/bin:$PATH
export PATH=/usr/local/samtools/1.11/samtools:$PATH
export PATH=/usr/local/bwa/current:$PATH
export PATH=/usr/local/qualimap_v2.2.1:$PATH
export PATH=/home/xingyuan/tools/Spine-0.3.2:$PATH
```

[Go to the main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)
