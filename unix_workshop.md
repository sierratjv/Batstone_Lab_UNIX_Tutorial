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
**pwd**

``pwd`` - present working directory.

**cd** 

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

**ls**

ls - lists files in the current directory (folders are directories (/) in UNIX; binary (*) is excuatable file)
   
ls -flags arguments - flags change the behaviour of the command
                    - two types - POSIX flags - single letters

``ls -a``

``ls -aF`` - directories are shown with /

``ls -S`` lists from larger files to smaller

``ls -r`` lists files name from 'Z' to 'A'

``ls -l`` 

``ls -lFSr``

``ls --color=auto``

``muscle -in file -out file`` (normally, -i for input, -o for output)

``muscle -o infile -i outfile``

**rm** (you cannot recover files in UNIX)

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

**open** - open any files


