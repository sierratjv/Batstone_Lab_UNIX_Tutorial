# Notes from Dr. Golding's UNIX Workshop
# May 29, 2023
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

# May 30, 2023
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

~/split -b -d ">" fasta. (-b splits before the pattern, pattern is the > sign) -----> gives files, each with one fasta sequence (This is written by 
Dr. Golding, type ``~brian/bin/split -h`` to see the help page``)

# May 31, 2023
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

# Jun 1, 2023

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

### ``!$``
! means histroy reference; $ means the last thing (type ``cd !$`` gives the last command)

### alias ls="list" (type list is the same as ls, ls will still work)
ls (use alias); \ls (do not use alias)

# Jun 2, 2023
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

# June 5, 2023
## vi

``.`` repeats the last command

## .bashrc/.vimrc 
work every time when you use bash or vim

## variables
create variable, for example, type ``i=2``

show the variable, type ``echo $i`` (it will show 2) or ``echo "$i $j $k"`` for multiple variables

# June 8, 2023

## &
sleep 150 & (run jobs in backrgound) <br>
[1] 12698 

ps aux | grep 12698 (find jobs)

^Z (zombie jobs, Stop a job) <br>
type ``bg`` to run it in background

^C (kill job)
kill %jobID (kill job)

## chmod
chmod u+x (user can execute)

## .sh
#!/bin/bash

bourne shell, Bash (Bourne again shell)

```
  1 #!/bin/bash
  2 cd folder
  3 ls
  4 myname=xingyuan
  5 mydir=`pwd` ( use `program` to run a program)
  6 # this is a comment
  7 echo $myname
  8 echo "current working directory is $mydir"  
```
```
file1  file2  file3
xingyuan
current working directory is /home/xingyuan/unixworkshop/folder
```

`basename sample45.fasta .fasta`.alignment (assign output a name, basename is a program)

## Compute Canada/Digital Research Alliance of Canada
https://www.sharcnet.ca/my/front/

https://docs.alliancecan.ca/wiki/Technical_documentation

https://www.youtube.com/channel/UCCRmb5_GMWT2hSlALHlwIMg (watch the two videos for new users on the top)

account: https://ccdb.alliancecan.ca/account_application 

Run jobs:
- Running longer than the runtime will be killed (need to estimate the runtime); cannot run for 7 days (need to break down the jobs)

Login:
              ssh terminal            batch system
local computer ----------> login nodes --------> compute nodes

access files:

/home, /project, /scractch (no back up), nearline

Check software on a cluster:

```
module avail
module spider keyword_for_the_software
```

submit a serial job:
```
#!/bin/bash
#SBATCH --time=00-01:00:00 # DD-HH:MM
#SBATCH --account=def-user
module load python/3.6
```

submit a threaded job:

```
search online for commands
```

submit a. parallel job

view jobs:

commonly used slurm commands
- squene

# June 9, 2023
## if statement
```
[xingyuan@info114 ~]$ if [ -f file ]; then
> echo found
> else
> echo not found
> fi
found
```

```
[xingyuan@info114 ~]$ [[ -f file ]] && echo found || echo false
found
```

```
#!/bin/bash
# A script to read the first entry in a fasta file.
# run as 'scriptName < filename'
# or     'cat filename | scriptName'
read firstline; echo $firstline
while read abc; do 
    if [[ $abc =~ ">" ]]; then 
        echo "I am done everything in the file"
        exit; 
    fi
    echo $abc
done
echo "While loop is done ... I am done everything in the file"
```

```
#!/bin/bash
# A script to read the n^th entry ($1) in a fasta file.
# run as 'scriptName no < filename'
# or     'cat filename | scriptName no'
i=0
while read line; do 
    if [[ $line =~ ">" ]]; then
        let i=$i+1
    fi
    if [ $i -eq $1 ]; then
        echo $line
    fi
done

#########################################################

#!/bin/bash
# A script to read the n^th entry ($1) in a fasta file ($2).
# run as 'scriptName no filename'
## i=0
## { while read line; do 
##     if [[ $line =~ ">" ]]; then
##         let i=$i+1
##     fi
##     if [ $i -eq $1 ]; then
##         echo $line
##     fi
## done } < $2
```

## suck up infomation and put into variable
[xingyuan@info114 ~]$ name=`wc file`
[xingyuan@info114 ~]$ echo $name
5 33 200 file

## while
```
[xingyuan@info114 unixworkshop]$ while read line; do 
> echo $line
> done < file
#!/bin/bash
echo "Files in $HOME/Downloads older than 30 days are"
find $HOME/Downloads -mtime +30
read -p "Press key to continue.." -n1 -s < /dev/tty
# find $HOME/Downloads -mtime +30 -exec rm {} ;
```
(same result as cat)

```
[xingyuan@info114 unixworkshop]$ while read line; do echo $line; echo ""; done < file
#!/bin/bash

echo "Files in $HOME/Downloads older than 30 days are"

find $HOME/Downloads -mtime +30

read -p "Press key to continue.." -n1 -s < /dev/tty

# find $HOME/Downloads -mtime +30 -exec rm {} ;
```

```
[xingyuan@info114 unixworkshop]$ while read line; do
> echo $line
> while read line; do
> echo $line
> done < example.fasta.1
> done < file
#!/bin/bash
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:N:0:1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCACACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTGATTAAAATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTCTTTTCCTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTTTTTTTTTTTTTTT
echo "Files in $HOME/Downloads older than 30 days are"
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:N:0:1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCACACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTGATTAAAATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTCTTTTCCTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTTTTTTTTTTTTTTT
find $HOME/Downloads -mtime +30
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:N:0:1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCACACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTGATTAAAATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTCTTTTCCTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTTTTTTTTTTTTTTT
read -p "Press key to continue.." -n1 -s < /dev/tty
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:N:0:1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCACACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTGATTAAAATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTCTTTTCCTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTTTTTTTTTTTTTTT
# find $HOME/Downloads -mtime +30 -exec rm {} ;
> M00719:224:000000000-AJ0H0:1:1101:17878:2093 1:N:0:1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCGGAAGAGCACACGTCTGAACTCCAGTCACTAAGGCGAATCTCGTATGCCGTCTTCTGCTTGATTAAAATCTCTTTCTTTTTTTTTTTTTTTTTTTTTTTTTTTTCTTTTTTTTCTTTTCTTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTCTTTTCCTTTTTTTTTTTTTTTTTTCTTTTTTTTTTTTTTTTTTTTTTTTT
```

# June 12, 2023
## link

``ln -s original_file new_file``

## Redirect

'cmd args > outfile' sents output to a file
'cmd args < infile' gets input 

## alignment practice

# June 13, 2023
## split help
``~brian/bin/split -h``

## alignment 
### clustalo
default format, fasta
```
clustalo -i ~brian/example.fasta -o clustalo.aln -v --threads=5
```

clustal format, align line by line 
```
clustalo -i ~brian/example.fasta -o clustalo.aln -v --threads=5 --outfmt=clustal
```

phylip format, title is 10 characters, 2 numbers at the top (1st: number of sequences, 2nd: lenghth of the sequence)
```
clustalo -i ~brian/example.fasta -o clustalo.2.aln -v --threads=5 --outfmt=phylip
```

In UNIX, bin/ is executable files. 

### blast
blastn: nucleotide

blastp: protein

blastx: DNA to protein, and search protein

```
scratch/blastdb/ (blast database), allows to search locally

BOLD: barcode of life database, elephant database, ...

refseq_protein: curated, people think it is true
```

```
blastn -query ~brian/exampleForBlast.fasta -out results113.out -db /scratch/blastdb/nt_v5
```

```
/usr/local/blast/2.13.0+/bin/blastn -query ~brian/exampleForBlast.fasta -out crap3 -db /scratch/blastdb/nt
```

```
/usr/local/blast/2.13.0+/bin/blastn -query ~brian/exampleForBlast.fasta -out resultNCBI.out -db nt -remote
```
(-remote sends the query to blast, use nt database on NCBI, don't send query after query, very slow)

Make blast database:
```
makeblastdb -in Streptomyces_venezuelae.faa -title "Streptomyces venezuelae" -dbtype prot

Will create 3 index files: .phr, .pin, .psq
```

Blast E.coli against Streptomyces venezuelae database just created
```
blastp -query 
```

# June 14, 2023
## alignment
### diamond 
preprocess using reads before search, use diamond if search for many reads. But use blast if search for one read.

## quality control
### fastp
it has a manual page, ``man fastp``
```
~brian/fastp 701-501_S1_L001_R1_001.fastq.gz 701-501_S1_L001_R2_001.fastq.gz bioproject16

=

fastp --in1 701-501_S1_L001_R1_001.fastq.gz --in2 701-501_S1_L001_R2_001.fastq.gz --merge --merged_out Trimmed/bioproject16_merged.fastq.gz --out1 Trimmed/bioproject16_r1.fastq.gz --out2 Trimmed/bioproject16_r2.fastq.gz --detect_adapter_for_pe --correction --low_complexity_filter --cut_right --cut_right_window_size 4 --cut_right_mean_quality 15 --cut_front --cut_front_window_size 1 --cut_front_mean_quality 3 --cut_tail --cut_tail_window_size 1 --cut_tail_mean_quality 3 --overlap_len_require 15 --length_required 30 --html FastpLogs/bioproject16.html --json FastpLogs/bioproject16.json --thread 5 --report_title bioproject16 --unpaired1 Trimmed/bioproject16_u1.fastq.gz --unpaired2 Trimmed/bioproject16_u2.fastq.gz --failed_out FailedQC/bioproject16_failed.fastq.gz
```

### fastqc 
``fastqc --help``

``fastqc -o myfastqc 701-501_S1_L001_R1_001.fastq.gz 701-501_S1_L001_R2_001.fastq.gz``

# June 15, 2023
## align reads back to genome
### bwa

index allows to map reads back to genome quicker

type ``gbk`` and press ``tab`` twice, there is ``gbk2fasta`` to change gbk file to fasta file

type ``fasta`` and press ``tab`` twice, you will find ``fasta2fasta      fasta2phy        fasta2snps       fastaFromBed     
fasta2fastq      fasta2phyI       fasta2stockholm``

### samtools
change ``sam`` to ``bam`` files 

### cdhit
find does read back to a gene

### edgeR, deseq2, voom
analyze gene expression

## phylogenetic trees
### iqtree
more samples, more possible trees, but program cannot go through all trees

```
options:
-t  provide a starting tree 
-wbt write bootstrap trees to .ufboot file (default: none)

RATE HETEROGENEITY different sites evolve at different rates


example: iqtree -s clustalo.aln -bb 1000 -wbt

.log file:

Alignment has 25 sequences with 441 columns and 284 patterns (229 informative sites)      column: width of alignment 

```
Change name in vi:
```
%s/Rabbit/\=printf(">Rabbit%d", line('.'))
```

visualize trees:
```
ssh -Y xingyuan@info.mcmaster.ca
ssh -X info113
(download XQuartz)

figtree clustalo.aln.contree
```

# June 16, 2023
## Tex and Latex 
markdown language

https://ctan.org

https://overleaf.org

https://en.wikibooks.org/wiki/LaTeX

https://tex.stackexchange.com

```
pdflatex first_page.tex

output: first_page.pdf 
```

Many commands exist within environments. They begin with \begin{cmd}.

Many characters are special to the system. Escape if needed.

fixed length: \setlength







