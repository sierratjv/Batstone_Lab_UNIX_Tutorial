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

### rm 
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

### touch 
create file

### open 
open any files

## May 30, 2023
**command format: flags and arguments**

cmd -flags --flags args args args

### cp 
**require at least two arguments**

cp afile bfile

**copy many files to a directory**

cp * ffile

cp -u file2 file1 (u is update, file2 must be newer than file1 to copy, file1 will be overwritten)

cp -pr file1 file2 (overwrite file2 with file1)

cp -r (recurs, go down a dirctory and copy everything, copy a directory to another directory)

### mv
mv bfile cfile

### cat

### rev 
revese the lines in a file

### more, less
read how big is your screen, and gives a screenful information, hit enter gives one lines, hit 10 gives 10 lines, /words searches for words (type n search the next word), q (control + D) for get out

### man
maual pages

synopsis - tell you how to run the program (OPTION means optional)

### top
what happens in the computer (how many jobs are running, sleeping means waiting for input, load average, CPU usage ...)

PID - process ID for that job, USER - who owns the job, PR, NI - priority for that jobs (low priority, low number)

### ps - process status
list what the computer is doing

ps aux (all the things that are running)

### head 
show first few lines of a file

### tail 
tail (see last 10 lines)

tail -60 (see last 60)

### wc - word count
wc !$

### sort

sort -r (reverse order)

sort -k2 (name)

sort -r -k2

### tr - translate

tr "ACGT" "TGCA" (create complementary strand)

### cut 

-d" " -f2 tosort.lst

### split 
cut files horizontally

~/split -b -d ">" fasta. (-b splits before the pattern, pattern is the > sign) -----> gives files, each with one fasta sequence

## May 31, 2023
### grep - global regular expression parser (flags -c -v -i -l -n)
grep pattern file

-c count number

-n what lines

### find
command: find path

find directory -iname "pattern" (go to the directory and find pattern)
```
[xingyuan@info114 trim_2nd_attempt]$ find spades-214C/ -iname "scaffolds.fasta"
spades-214C/scaffolds.fasta
spades-214C/K55/scaffolds.fasta
```
find directory -iname "pattern" -exec command (find and excute a command)

### different types of grep

zgrep (search compressed file)

pgrep (search for paragraph which separated by empty lines)

fgrep (search arguments)

egrep 

agrep (search approximate matching)

Different types of zip files (zip the sequencing files)

*.zip    zip file

*.gz     gzip / gunzip

*.bz     bzip2 / bunzip2

*.xz     xz / unxz

*.tgz    tar gzip'ed  file

tar cvf directory file.tar

### wget/curl

### rsh 
remote shell

### ssh 
secure shell

**on infoserv**
don't run more than 6 jobs

``usage``

``uptime``

``which R`` check with version of R 

``host info`` look up what is info

### scp (work the same as cp)
secure copy

yourLapTop% scp std#@info.mcmaster.ca:file newfile (this has to be done on your laptop, not the server)

yourLapTop% scp file std#@info.mcmaster.ca:newfile (this has to be done on your laptop, not the server)

## Jun 1, 2023

### scp 
``xingyuansu@Xingyuans-MacBook-Pro Desktop % scp xingyuan@info.mcmaster.ca:/home/xingyuan/unixworkshop/example.fasta.\* .`` (**the \ skips the sections**)

### > stdout (aka the screen) to a file
###   stderr (aka something 
###   stdin 
align example.fasta.1 example.fasta.2
```
ALIGN calculates a global alignment of two sequences
 version 2.0uPlease cite: Myers and Miller, CABIOS (1989) 
 resetting matrix to DNA
 example.fasta.1 :  251 nt
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:   251 nt vs.
> M00719:224:000000000-AJ0H0:1:1101:19693:2191 1:   251 nt
scoring matrix: DNA, gap penalties: -16/-4
80.3% identity;		Global alignment score: 772

               10        20         30        40        50         
exampl ACCGCTACATCTCCATCTTCTAC-ATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCA
        :::::::::::::::::::::: :::::::: :::::::::::::::::::::::::::
       TCCGCTACATCTCCATCTTCTACCATCGTTCCCCCAACTCCTTATCAGATCGGAAGAGCA
               10        20        30        40        50        60

      60        70        80        90       100       110         
exampl CACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTG--ATTAAA
       :::::::::::::::::::::::::::: :::::::::::::::: ::::::  :: :: 
       CACGTCTGAACTCCAGTCACTAAGGCGACTCTCGTATGCCGTCTTTTGCTTGTAATAAAT
               70        80        90       100       110       120

       120       130       140       150       160       170       
exampl ATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTT
       :  :::::::::     :::::::::: :::  :  :  : : : :::::: : :: :::
       ACTTCTTTCTTTCCCCCTTTTTTTTTTATTTCCTCCTTCTCTCTCTCTTTTTTCTTCTTT
              130       140       150       160       170       180

       180       190       200       210       220       230       
exampl TTTTTTTTTTTCTTTTTTTTTTTCTTTTCCTTTTTTTTTTTTTTTTTTCTTTTTTTTTTT
       : :: : : ::::::::: :::: :: ::::  ::::: :::: : ::  :: :: ::  
       TCTTCTCTCTTCTTTTTTCTTTT-TTCTCCTCATTTTTGTTTTCTCTT--TTCTTCTTGC
              190       200        210       220         230       

       240       250 
exampl TTTTTTTTTTTTTT
        :::::::::  ::
       ATTTTTTTTTACTT
       240       250 
```

cat example.fasta.1 example.fasta.2 (**but it is present to the screen**)
```
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:N:0:1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCACACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTGATTAAAATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTCTTTTCCTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTTTTTTTTTTTTTTT
> M00719:224:000000000-AJ0H0:1:1101:19693:2191 1:N:0:1
TCCGCTACATCTCCATCTTCTACCATCGTTCCCCCAACTCCTTATCAGATCGGAAGAGCACACGTCTGAACTCCAGTCACTAAGGCGACTCTCGTATGCCGTCTTTTGCTTGTAATAAATACTTCTTTCTTTCCCCCTTTTTTTTTTATTTCCTCCTTCTCTCTCTCTTTTTTCTTCTTTTCTTCTCTCTTCTTTTTTCTTTTTTCTCCTCATTTTTGTTTTCTCTTTTCTTCTTGCATTTTTTTTTACTT
```

cat example.fasta.1 example.fasta.2 > alignment (**">" send standard out to a file**) 

(**standard error still goes to the screen**)
standard error:
```
ALIGN calculates a global alignment of two sequences
 version 2.0uPlease cite: Myers and Miller, CABIOS (1989) 
 resetting matrix to DNA
 example.fasta.1 :  251 nt
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:   251 nt vs.
> M00719:224:000000000-AJ0H0:1:1101:19693:2191 1:   251 nt
scoring matrix: DNA, gap penalties: -16/-4
80.3% identity;		Global alignment score: 772
```

align example.fasta.1 example.fasta.2 &> alignmnet
```
 resetting matrix to DNA
 example.fasta.1 :  251 nt
ALIGN calculates a global alignment of two sequences
 version 2.0uPlease cite: Myers and Miller, CABIOS (1989) 
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:   251 nt vs.
> M00719:224:000000000-AJ0H0:1:1101:19693:2191 1:   251 nt
scoring matrix: DNA, gap penalties: -16/-4
80.3% identity;		Global alignment score: 772

               10        20         30        40        50         
exampl ACCGCTACATCTCCATCTTCTAC-ATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCA
        :::::::::::::::::::::: :::::::: :::::::::::::::::::::::::::
       TCCGCTACATCTCCATCTTCTACCATCGTTCCCCCAACTCCTTATCAGATCGGAAGAGCA
               10        20        30        40        50        60

      60        70        80        90       100       110         
exampl CACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTG--ATTAAA
       :::::::::::::::::::::::::::: :::::::::::::::: ::::::  :: :: 
       CACGTCTGAACTCCAGTCACTAAGGCGACTCTCGTATGCCGTCTTTTGCTTGTAATAAAT
               70        80        90       100       110       120

       120       130       140       150       160       170       
exampl ATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTT
```

###   pipe  cmd1 | cmd2 (sends the output

ps aux | more (show what the computer is doing)

ps aux | grep brian

pdftotext (change pdf to a text; work in pipe)

### history (show command you show before)

### !! (give last command you typed, same as cd !$) 

### !$
! means histroy reference; $ means the last thing (type ``cd !$`` gives the last command)

### alias ls="list" (type list is the same as ls, ls will still work)
ls (use alias); \ls (do not use alias)

## Jun 2, 2023
### toss 
throw things away, same as ``cat > /dev/null``

### rsync 
only transfer the differences of a file, not the whole file

### set -o noclobber (prevent overwriting files)

### editors (vi, emacs, pluma, xedit, pico, nano, red, gedit)

### vi 
[cheat_sheet_vi.pdf](https://github.com/sux21/Tips_and_Tricks/files/11638264/cheat_sheet_vi.pdf)

type i to edit

control C to exit edit

w go forward to a word, b go backward a word

type ``:q!`` to exit

type ``vimtutor``

## June 5, 2023
## vi

``.`` repeats the last command

## .bashrc/.vimrc 















