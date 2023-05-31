# Notes from Dr. Golding's UNIX Workshop
## May 29, 2023
### Introduction
different versions of UNIX: AIX, HP/UX, SunOS, ULTRIX, OSX, FreeBSD, LINUX

GNU Free Software Foundation

different versions of LINUX: Red Hat, Centos, Mageia, Debian, Ubuntu, ... 

SHELL: you interact with a remote UNIX computer through SHELL. 

Different versions of SHELLs: sh, csh, tcsh, ksh, bash, zsh. 

Types of programming languages: scripted (R, python, bash), not scripted but it is Object Orientation (C++), compiled (C, fortran)

### Commands (cmd)
### pwd

``pwd`` - present working directory.

### cd 
``cd`` - change directory.

``cd``, ``cd ~``, ``cd /home/brain`` take you home.

``cd ~alessia`` take you to alessia's home (the command is not ``cd ~/alessia``)

``/`` is the root of the file system.

``/home`` is where people's home directories are stored.

``/usr``.

``/usr/local`` is where to find all softwares specific to this machine here.

``.`` means 'here'.

``..`` means ``one directory up``.

Relative path - example: ``../../home/brian/../brian`` is equal to  ``/home/brian``.

Absolute path. 

### ls

ls - lists files in the current directory (folders are directories (/) in UNIX; binary (*) is excuatable file)
   
ls -flags arguments - flags change the behaviour of the command
                    - two types - POSIX flags - single letters
                    
``ls -a``

``ls -aF`` - directories are shown with /

``ls -R`` - list all subdirectories

``ls -S`` lists from larger files to smaller

``ls -r`` lists files name from 'Z' to 'A'

``ls -l`` 

``ls -lFSr``

``ls --color=auto``

``muscle -in file -out file`` (normally, -i for input, -o for output)

``muscle -o infile -i outfile``

## rm 
**use ls to double check before removing**
you cannot recover files in UNIX

rm 

rm -r (r means recursive, go in and delete)

rm * (* means anything) - everything will be deleted

^C  (control C) - mean kill/stop a command

rmdir

create files

case sensitive          B*G*H             
                        [b-y]* - all files begin with b to y
                        {b,c,d}* === [b-d]*

NO SPACES in command

"a file with spaces" - how to type files with spaces

a\ file\ with\ spaces - how to type files with spaces

a\{this

a\#

a\(

## touch 
create file

## open 
open any files

## May 30, 2023
**command format: flags and arguments**

cmd -flags --flags args args args

## cp 
**require at least two arguments**

cp afile bfile

**copy many files to a directory**

cp * ffile

cp -u file2 file1 (u is update, file2 must be newer than file1 to copy, file1 will be overwritten)

cp -pr file1 file2 (overwrite file2 with file1)

cp -r (recurs, go down a dirctory and copy everything, copy a directory to another directory)

## mv
mv bfile cfile

## cat

## rev 
revese the lines in a file

## more, less
read how big is your screen, and gives a screenful information, hit enter gives one lines, hit 10 gives 10 lines, /words searches for words (type n search the next word), q (control + D) for get out

## man
maual pages

synopsis - tell you how to run the program (OPTION means optional)

## top
what happens in the computer (how many jobs are running, sleeping means waiting for input, load average, CPU usage ...)

PID - process ID for that job, USER - who owns the job, PR, NI - priority for that jobs (low priority, low number)

## ps - process status
list what the computer is doing

ps aux (all the things that are running)

**check the files downloaded to see whether it is correct**
## head 
show first few lines of a file

## tail 
tail (see last 10 lines)

tail -60 (see last 60)

## wc - word count
wc !$

## sort

sort -r (reverse order)

sort -k2 (name)

sort -r -k2

## tr - translate
tr "ACGT" "TGCA" (create complementary strand)

## cut -d" " -f2 tosort.lst

## split 
cut files horizontally

~/split -b -d ">" fasta. (-b splits before the pattern, pattern is the > sign) -----> gives files, each with one fasta sequence





