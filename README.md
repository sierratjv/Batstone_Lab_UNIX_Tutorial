# Tips_and_Tricks
UNIX tips and tricks for beginners

## Softwares required
For Windows, download the free version of MobaXterm from https://mobaxterm.mobatek.net/. 

For Mac, use Terminal app. 

## Resources
[UNIX Tutorial for Beginners](http://www.ee.surrey.ac.uk/Teaching/Unix/)

[Bioinformatics_Data_Skills.pdf](https://github.com/sux21/Tips_and_Tricks/files/11593310/Bioinformatics_Data_Skills.pdf)

## Symobols in UNIX
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

## Info server 
Info server consists a head (called info) and serveral nodes (called info16, info17, info18, ...). Head and nodes are different computers.

Login to head: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). Type ``exit`` to leave the server.

Login to nodes, for example, info114: type ``ssh info114``. Then type ``password``. Type ``exix`` to leave the node and go back to the server head. 

In the head, type ``usage`` to see usage infomation of these computers.
```
 Usage script is located in /usr/local/bin 
 Collecting information ... please wait 

info:    13:43:05 up 37 days, 23:20, 11 users,  load average: 0.00, 0.02, 0.05

info16:  13:43:05 up 31 days,  2:52,  0 users,  load average: 0.00, 0.00, 0.00
info17:  13:43:05 up 31 days,  2:54,  1 user,  load average: 0.23, 0.33, 0.27
info18:  13:43:05 up 30 days, 23:01,  1 user,  load average: 0.17, 0.31, 0.37
info19:  13:43:05 up 30 days, 23:01,  0 users,  load average: 0.24, 0.15, 0.10
info20:  13:43:05 up 1 day, 23:47,  2 users,  load average: 0.35, 0.23, 0.09

info113:  13:43:05 up 205 days, 22:50,  5 users,  load average: 0.01, 0.10, 0.07
info114:  13:43:05 up 204 days, 13:16,  3 users,  load average: 0.97, 0.95, 0.91
info115:  13:43:05 up 205 days, 23:01,  6 users,  load average: 31.33, 26.07, 26.98
info2020: 13:40:01 up 584 days, 17:18,  8 users,  load average: 58.73, 57.01, 57.33
```

**Tips:**
- Run programs on **nodes**. Running programs on the head (which is the place when you login) will greatly slow the system. 

## ls - list directory contents
To list content in a directory, type ``ls``.

To list hidden files (files beginning with ``.``), type ``ls -a``. 

To list access rights of files, type ``ls -l``. Read [How to change directory permissions in Linux with chmod](https://www.pluralsight.com/blog/it-ops/linux-file-permissions) for instructions about how to change access rights. 

Type ``man ls`` to open the manual for the ``ls`` command. Type ``q`` and press <kbd>Enter</kbd> to exit.

**Wildcard** <br>
This allows you to work with multiple files at the same time using ``*`` symbol. 

To list files in the current directory beginning with **bio...**, type ``ls bio*`` .

To list files in the current directory ending with **...logy**, type ``ls *logy``.

To count the number of files ending in .fastq, type ``ls *.fastq | wc -l``. 

## man - format and display the on-line manual pages
This is useful for finding out different options for a command. For example, by typing ``man ls``, you can find different options for the command, ``ls -a``, ``ls -A``, ``cd --author``, etc. 

Type ``man command`` to see the manual of a command (``command`` is the command you want to look up).

**example**

Type ``man ls``. 

## cd - change directory 
Directory is a folder.

To move ahead one directory, type ``cd directory`` (``directory`` is the name of the directory you want to go to).

To move back one directory, type ``cd ..``.

To move to home directory from any directories, type ``cd``. 

## pwd - print name of current/working directory
To view the absolute pathname of a directory, ``cd`` to that directory first, then type ``pwd``.

## mkdir - make directories
To make a new directory, type ``mkdir directory``(``directory`` is the name for that directory). Type ``ls`` to verify the directory is made successfully. 

## rm - remove files or directories
To delete a file, type ``rm file`` (``file`` is the name of the file).

To delete an empty directory, type ``rmdir directory`` (``directory`` is the name of the directory).

Type ``rm -r directory`` to remove directory with its contents (``directory`` is the name of the directory which you want to delete). You will notice you have to enter "yes" before deleting each file. To delete the contents without doing that, run the command in shell script. See [Shell script](#shell-script).

## mv - move (rename) files

**Move all files from one directory to another directory**

``mv pathname_old_directory/* pathname_new_directory/`` (``*`` symbol selects all files in the old directory). 

## less - open files
To open a file, type ``less file`` (``file`` is the name of the file).

To close the file, type ``q`` and <kbd>Enter</kbd>.

To search for a certain word in the file, type ``/word`` and press <kbd>Enter</kbd> (``word`` is the word you want to search for). Press ``n`` to go to the next word.

To go to the end of the file, type ``G`` and press <kbd>Enter</kbd>.

## open - open any files
This can be used to open pdf, pptx, ect. 

Type ``open file`` to open the file (``file`` is the name of the file)

## scp - secure copy  
**From remote server to your local computer**

To copy one file, first exit the server, and type ``scp username@host:file_pathname destination_pathname``. 

To copy multiple files using wildcards, first exit the server, and type ``scp 'username@host:files_pathname_*' destination_pathname``.

**From your local computer to remote server**

Type ``scp file_pathname username@host:directory_pathname``.

## Extract files
To extract a tar.gz file, type ``tar -xf archive.tar.gz``

## Working in background 
It is useful for running time-consuming commands, so you can close your computer without terminating the commands.  

**Screen command**

Type ``screen`` to open a screen session.

Type ``exit`` to terminate the screen session. 

Type ``screen -ls`` to find the running screen session. If no screen session found, it will return ``No Sockets found...``. **Make sure there is no process running in screen before you exit the server**

**Nohup command**

Type ``nohup command &`` to run the process in background (``command`` is the command you want to run in background). After pressing <kdb>Enter</kdb>, it will return you the process ID (PID) for this process. 

Type ``ps x`` to show the nohup process. 

## Symbolic link
Read about symbolic link on [Symlink Tutorial in Linux – How to Create and Remove a Symbolic Link](https://www.freecodecamp.org/news/symlink-tutorial-in-linux-how-to-create-and-remove-a-symbolic-link/).

To create symbolic link, go to the directory where you want to create the symbolic link, type ``ln -s pathname_of_the_file .`` (the ``.`` at the end means that you want to put the symbolic link in the current directory).

**Tips:**
- Check the number of files before and after creating the symbolic link, by typing ``ls file_name | wc -l``. Use wildcards (* symbol) to select files, such as ``ls *fastq`` for selecting all files ending in fastq, and ``wc -l`` will count all the lines which you select.

**Troubleshooting:**
- If the system cannot find the symbolic link, check the pathname of the original files to see if they are the same one used to create the symbolic link. If not, re-create the symbolic link with the correct pathname. 

## Environmental variable
To show all environmental variables, type ``env``.

Steps for creating a environmental variable: <br>
1. Have the pathname ready; <br>
2. Type ``export AAA="pathname"``(``AAA`` is the name of the variable); <br> 
3. Then in any directories, type ``cd $AAA`` will allow you to enter that directory. If it is a program, typing ``$AAA`` in any directories can run this program;
4. Type ``echo $AAA`` to view the environmental variable that you created.

**PATH variable - one type of environmental variable**
The system checks the PATH variable when it runs a command. Thus, it is useful to store the pathname of commonly used programs (such as Python which is required to run SPAdes genome assembler) in the PATH variable. 

Read about PATH variable on [How To View and Update the Linux PATH Environment Variable](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable#step-3-mdash-permanently-adding-a-directory-to-the-path-variable). 

To view PATH, type ``echo $PATH``.

Steps for adding a directory to the PATH variable:
1. Type ``nano ~/.bashrc`` to open a file called ``.bashrc``;
2. Type ``export PATH=/the/file/path:$PATH`` in the ``.bashrc`` file (``/the/file/path`` is the pathname of the directory you want to add);
3. Press <kbd>Control</kbd> + <kbd>X</kbd>, then type ``Y`` to save the changes, then press ``Enter`` to exit ``.bashrc``;
4. To see the changes which you made on the PATH variable, you have to log out (types ``exit`` if you are on a server) and then log in again.
5. Type ``echo $PATH`` to see if changes are made successfully. Your new pathnames should be added to the start of the PATH variable. 

**Troubleshooting:**
- If the system still cannot find the program, check if the new directory is added to the **start of the PATH variable**. The command to do that is ``export PATH=/the/file/path:$PATH``. See why [here](https://stackoverflow.com/questions/9546324/adding-a-directory-to-the-path-environment-variable-in-windows#:~:text=The%20path%20works%20like%20first,the%20beginning%20of%20the%20command). 

## Shell Script
It is useful for saving a long command, so you don't need to type it each time.

Steps for creating a shell script:
1. Create a shell script; <br>
``nano shell_script.sh`` (``shell_script`` is the name of the file) <br>
2. In the opened text editor, type the following; <br>
```
#!/bin/bash 
command you want to run
```
The first line tells what program (e.g. bash) to use to interpret the script. The second line is the command you want to run. <br>
3. Exit shell script; <br>
4. Run shell script. <br>
``bash shell_script.sh`` <br>

# Run programs automatically 
## For Loop
It is useful for running a program for multiple files. 

For instructions, read [Lesson 06: For Loops](https://github.com/raynamharris/Shell_Intro_for_Bioinformatics_STG/blob/master/lessons/06_ForLoops.md).

An example I used to run Trimmomatic:
```
#!/bin/bash 
for R1 in *R1* 
do 
R2=${R1//R1_001.fastq/R2_001.fastq} 
R1_P=${R1//001.fastq/P_001.fq.gz} 
R1_UP=${R1//001.fastq/UP_001.fq.gz} 
R2_P=${R2//001.fastq/P_001.fq.gz} 
R2_UP=${R2//001.fastq/UP_001.fq.gz} 

java -jar /usr/local/trimmomatic/Trimmomatic-0.39/trimmomatic-0.39.jar PE /home/xingyuan/2018_strains/raw_reads/$R1 /home/xingyuan/2018_strains/raw_reads/$R2 /home/xingyuan/2018_strains/trim_2nd_attempt/$R1_P /home/xingyuan/2018_strains/trim_2nd_attempt/$R1_UP /home/xingyuan/2018_strains/trim_2nd_attempt/$R2_P /home/xingyuan/2018_strains/trim_2nd_attempt/$R2_UP ILLUMINACLIP:/usr/local/trimmomatic/Trimmomatic-0.39/adapters/NexteraPE-PE.fa:2:30:10:2:TRUE HEADCROP:15 
done
```
Use ``echo`` to check whether it is correct or not:
```
#!/bin/bash 
for R1 in *R1* 
do 
R2=${R1//R1_001.fastq/R2_001.fastq} 
R1_P=${R1//001.fastq/P_001.fq.gz} 
R1_UP=${R1//001.fastq/UP_001.fq.gz} 
R2_P=${R2//001.fastq/P_001.fq.gz} 
R2_UP=${R2//001.fastq/UP_001.fq.gz} 

echo java -jar /usr/local/trimmomatic/Trimmomatic-0.39/trimmomatic-0.39.jar PE /home/xingyuan/2018_strains/raw_reads/$R1 /home/xingyuan/2018_strains/raw_reads/$R2 /home/xingyuan/2018_strains/trim_2nd_attempt/$R1_P /home/xingyuan/2018_strains/trim_2nd_attempt/$R1_UP /home/xingyuan/2018_strains/trim_2nd_attempt/$R2_P /home/xingyuan/2018_strains/trim_2nd_attempt/$R2_UP ILLUMINACLIP:/usr/local/trimmomatic/Trimmomatic-0.39/adapters/NexteraPE-PE.fa:2:30:10:2:TRUE HEADCROP:15 
done
```
**Tips:**
- Write the loop in a shell script if it is very long.
- Use ``echo`` command to check whether you write the loop correctly or not.

**Troubleshooting:**
- Check whether there are any typos in the commands. 
