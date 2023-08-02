# Commands
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

## ls - list directory contents
Type ``ls``, and it will list contents in your current directory. 

Type ``ls -a``, and it will list hidden files (files beginning with ``.``) in your current directory.

Type ``ls --color``, it will list and colorize output in your current directory. 

Type ``ls -F``, it will list and classify the files in your current directory. For example, the name of a directory will have ``/`` at the end. 

Type ``ls -l``, it will list the infomation, such as file permissionns (drwx------), owner name, owner group, file size, last modification time. Learn about file permissions here: https://www.pluralsight.com/blog/it-ops/linux-file-permissions. 

Type ``ls -S``, it will list the files from largest size to smallest size.

Type ``man ls``, this will open a manual page for ls, it has all the options of how to use ls. Press <kbd>q</kbd> to quit the manual.

You can also combline the flags, such as ``ls -lS``.

## man - format and display the on-line manual pages
Type ``man cmd`` to see the manual of a command (``cmd`` is the command you want to look up).

Type ``man man`` to open a manual page for man. 

## cd - change directory 
To move ahead one directory, type ``cd dir`` (``dir`` is the directory you want to go to).

To move back one directory, type ``cd ..``.

To move to home directory from any directories, type ``cd`` or ``cd ~``. 

## pwd - print name of current/working directory
Type ``pwd``, it will print the path of your current directory.

## mkdir - make directories
To make a new directory, type ``mkdir dir``(``dir`` is the name for that directory). Type ``ls`` to verify the directory is made successfully. 

## touch 
Type ``touch file1 file2 file3``, it will create file1, file2, file3. 

## cp - copy files and directories
Type ``cp file1 file2``, it will copy contents in file1 to file2 (if file2 exists, it will ask whether to overwrite it or not; if file2 does not exit, it will create file2).

Type ``cp file{1..5} folder``, it will copy file1, file2, file3, file4, file5 to a directory called folder (folder needs to be existed before copying files). 

## rm - remove files or directories
**This command can be dangerous. For example, ``rm *`` will remove everything from your current directory. There is no recovery for removed files.**

To delete a file, type ``rm file`` . 

To delete an empty directory, type ``rmdir dir``. 

Type ``rm -r dir``, it will go into to the directory and removes everyting. 

## mv - move (rename) files
Type ``mkdir dir1 dir2`` to create two directories named dir1 and dir2. Type ``ls`` to confirm.

Type ``cd dir1`` to go into dir1, and type ``touch file1, file2, file3`` to create 3 files. Type ``ls`` to confirm. Type ``cd ..`` to exit dir1.

Type ``mv dir1/* dir2/`` to move contents from dir1 to dir2 (* symbol selects all files in dir1). Type ``ls dir1``, it should return nothing, meaning dir1 is empty. Type ``ls dir2``, you should have file1, file2, file3 in dir2, meaning the 3 files are transferred.

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

## sed
convert .txt to .csv, ``sed 's/ \+/,/g' file.txt > file.csv``

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

To remove symbolic link, use ``rm``. When remove symbolic link, don't include ``/``. If not, you will get the following error:
```
[xingyuan@info114 tools]$ rm bin/
rm: cannot remove `bin/': Is a directory
[xingyuan@info114 tools]$ rmdir bin/
rmdir: failed to remove `bin/': Not a directory
[xingyuan@info114 tools]$ rmdir bin
rmdir: failed to remove `bin': Not a directory
[xingyuan@info114 tools]$ rm bin
rm: remove symbolic link `bin'? y
```

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

## wget
use ``md5sum file`` or ``sha256sum file`` to verify the download.

## Conda
offical website: https://docs.conda.io/projects/conda/en/4.6.1/index.html 

Intro: https://docs.conda.io/projects/conda/en/4.6.1/user-guide/getting-started.html

Commands: https://docs.conda.io/projects/conda/en/4.6.1/commands.html#conda-general-commands

list Conda environments: ``conda info --envs``

list channals: ``conda config --show channels``

see conda: ``conda info``

## Perl 
View perl include path (@INC), type ``perl -e "print qq(@INC)"``

add dir to @INC: ``export PERL5LIB=/home/foobar/code``

## Convert .txt to .csv (veiw files in excel or google spreadsheets)
``cat ifile.txt | tr -s '[:blank:]' ',' > ofile.txt``

## For Loop
It is useful for running a program for multiple files. 

For instructions, read [Lesson 06: For Loops](https://github.com/raynamharris/Shell_Intro_for_Bioinformatics_STG/blob/master/lessons/06_ForLoops.md).

manipulating string (useful for writing loop): https://mywiki.wooledge.org/BashFAQ/100, https://tldp.org/LDP/abs/html/string-manipulation.html

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
