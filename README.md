# Tips_and_Tricks
The purpose of this document is to store a list of commands for quick finding. For what these commands mean and more complex usage of these commands, go to the websites embedded or search online. This document also includes tips and troubleshootings for commands. 

## Info server 
Login to head: type ``ssh username@info.mcmaster.ca``. Then type ``password`` (You don't see the characters when you enter the password). Type ``exit`` to leave the server.

Login to nodes, for example, info114: type ``ssh info114``. Then type ``password``. Type ``exix`` to leave the node and go back to the server head. 

**Tips:**
- Run programs on **nodes**. Running programs on the head (which is the place when you login) will greatly slow the system. 

## Symobols in UNIX
``.`` represents the current directory. 

``..`` represents the parent of the current directory. 

``~`` represents the home directory.

## Using Keyboard

Press ``Enter`` to run the command that you type in. 

Press ``Control``+``C`` to delete the command that you type in.

Press ``↑`` to search the commands that you typed before.

Tab complete: if you want to save time for typing ``cd Desktop``, you can type ``cd Des`` and the press ``Tab``. If ``Destop`` is the only directory beginning with ``Des...``, it will complete the command ``cd Desktop``. If not, it will return all files begining with ``Des...``, and then press ``Tab`` to select the file you want. 

Press ``Control``+``A`` to go to the beginning of a command.

Press ``Control``+``E`` to go to the end of a command.

Press ``Control``+``Z`` to stop a process that is running.

# Commonly used commands 
[Go Back to Top](#tips_and_tricks)

## First read [UNIX Tutorial for Beginners](http://www.ee.surrey.ac.uk/Teaching/Unix/).

## List 
To list content in a directory, type ``ls``.

To list hidden files (files beginning with ``.``), type ``ls -a``. 

To list access rights of files, type ``ls -l``. Read [How to change directory permissions in Linux with chmod](https://www.pluralsight.com/blog/it-ops/linux-file-permissions) for instructions about how to change access rights. 

## Change directory 
To move ahead one directory, type ``cd directory`` (``directory`` is the name of the directory you want to go to).

To move back one directory, type ``cd ..``.

To move to home directory from any directories, type ``cd``. 

## Make directory
To make a new directory, type ``mkdir directory``(``directory`` is the name for that directory). Type ``ls`` to verify the directory is made successfully. 

## Remove file or directory
To delete a file, type ``rm file`` (``file`` is the name of the file).

To delete a directory, it has to be empty; then type ``rmdir directory`` (``directory`` is the name of the directory).

## Pathname
To view the absolute pathname of a directory, ``cd`` to that directory first, then type ``pwd``.

## Wildcard
It is useful for running a command for multiple files. 

To list files in the current directory beginning with **bio...**, type ``ls bio*`` .

To list files in the current directory ending with **...logy**, type ``ls *logy``.

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
3. Press ``Control``+``X``, then type ``Y`` to save the changes, then press ``Enter`` to exit ``.bashrc``;
4. To see the changes which you made on the PATH variable, you have to log out (types ``exit`` if you are on a server) and then log in again.
5. Type ``echo $PATH`` to see if changes are made successfully. Your new pathnames should be added to the start of the PATH variable. 

**Troubleshooting:**
- If the system still cannot find the program, check if the new directory is added to the **start of the PATH variable**. The command to do that is ``export PATH=/the/file/path:$PATH``. See why [here](https://stackoverflow.com/questions/9546324/adding-a-directory-to-the-path-environment-variable-in-windows#:~:text=The%20path%20works%20like%20first,the%20beginning%20of%20the%20command). 

# Commands for working with files
[Go Back to Top](#tips_and_tricks)

## Opening and Reading File
To open file in a new window, type ``less document`` (``document`` is the name of the file).

To close the file, type ``q`` and press ``Enter``.

To search for a certain word in the file, type ``/word`` and press ``Enter`` (``word`` is the word you want to search for). Press ``n`` to go to the next word.

To go to the end of the file, type ``G`` and press ``Enter``.

## Copy Files 
**From server to your own computer**

To copy one file, first exit the server, and type ``scp username@host:document_pathname destination_pathname``. 

To copy multiple files using wildcards, first exit the server, and type ``scp 'username@host:documents_pathname_*wildcards' destination_pathname``.

**Tips:**
- When using wildcards, first use ``ls`` command to check whether the correct files are selected. 

## Move Files

**Move all files from one directory to another directory**

``mv pathname_old_directory/* pathname_new_directory/`` (``*`` symbol selects all files in the old directory). 

# Commands for making your work easy
[Go Back to Top](#tips_and_tricks)

## Shell Script
It is useful for saving a long command, so you don't need to type it each time.

Steps for creating a shell script:
1. Create a shell script; <br>
``nano shell_script.sh`` (``shell_script.sh`` is the name of the file) <br>
2. In the opened text editor, type the following; <br>
```
#!/bin/bash 
command you want to run
```
The first line tells what program (e.g. bash) to use to interpret the script. The second line is the command you want to run. <br>
3. Exit shell script; <br>
4. Run shell script. <br>
``bash shell_script.sh`` <br>

## For Loop
It is useful for running a program for multiple files. 

For instructions, read [Lesson 06: For Loops](https://github.com/raynamharris/Shell_Intro_for_Bioinformatics_STG/blob/master/lessons/06_ForLoops.md).

**Tips:**
- Write the loop in a shell script if it is very long.
- Use ``echo`` command to check whether you write the loop correctly or not.

**Troubleshooting:**
- Check whether there are any typos in the commands. 

## Delete a directory with files

Type ``rm -r directory`` to remove directory with its contents (``directory`` is the name of the directory which you want to delete. It is inconvient because you have to type ``yes`` for every file before deleting it. 
 
**Tips:**
- Use shell script to run the ``rm -r`` command. 

## Working in background 
It is useful for running time-consuming commands, so you can close your computer without terminating the commands. 

To send a process running in foreground into background, use ``Control+Z`` to stop the process first and type ``bg &`` to run it in background. 

**Screen command**

Type ``screen`` to open a screen session.

Type ``exit`` to terminate the screen session. 

Type ``screen -ls`` to find the running screen session. If no screen session found, it will return ``No Sockets found...``. 

**Nohup command**

Type ``nohup command &`` to run the process in background (``command`` is the command you want to run in background). After pressing ``Enter``, it will return you the process ID (PID) for this process. 

Type ``ps x`` to show the nohup process. 

# Bioinformatics Programs
**Tips:**
- For learning a program, read the official article about how the program works, and then read the manual on the official website for the command for running the program.
- For running a program, make detailed notes on what files are the input files, what files are the output files, and the locations of these input and output files.
- For running a program, run the program for one sample to check whether it runs correctly before running the program for all samples.

### SPAdes
For official website, go to [SPAdes](https://cab.spbu.ru/software/spades/). <br>
The most early information about SPAdes was a talk, but I could not find the video recording of it. The talk was "Alekseyev M. A. SPAdes: новый ассемблер геномов с поддержкой одноклеточного секвенирования. (talk), 2011." <br>
For official artical, read [Bankevich A, Nurk S, Antipov D, Gurevich AA, Dvorkin M, Kulikov AS, Lesin VM, Nikolenko SI, Pham S, Prjibelski AD, Pyshkin AV, Sirotkin AV, Vyahhi N, Tesler G, Alekseyev MA, Pevzner PA. SPAdes: a new genome assembly algorithm and its applications to single-cell sequencing. J Comput Biol. 2012 May;19(5):455-77](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3342519/). 

### Quast
For official website, go to [Quast](https://quast.sourceforge.net/). <br>
For official article, read [Alexey Gurevich and others, QUAST: quality assessment tool for genome assemblies, Bioinformatics, Volume 29, Issue 8, April 2013, Pages 1072–1075](https://academic.oup.com/bioinformatics/article/29/8/1072/228832).

### Bandage
For official website, go to [Bandage](http://rrwick.github.io/Bandage/). <br>
For official article, read [Ryan R. Wick and others, Bandage: interactive visualization of de novo genome assemblies, Bioinformatics, Volume 31, Issue 20, October 2015, Pages 3350–3352](https://academic.oup.com/bioinformatics/article/31/20/3350/196114). 

### FastQC 
For official website, go to [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/). <br>
For an article explaining duplication level: read [Why does FASTQC show unexpectedly high sequence duplication levels (PCR-duplicates)?](https://dnatech.genomecenter.ucdavis.edu/faqs/why-does-fastqc-show-unexpectedly-high-sequence-duplication-levels-pcr-duplicates/). 

### MultiQC
For official website, go to [MultiQC](https://multiqc.info/). <br>
For official article, read [Philip Ewels and others, MultiQC: summarize analysis results for multiple tools and samples in a single report, Bioinformatics, Volume 32, Issue 19, October 2016, Pages 3047–3048](https://academic.oup.com/bioinformatics/article/32/19/3047/2196507).

### Trimmomatic
For official website, go to [Trimmomatic: A flexible read trimming tool for Illumina NGS data](http://www.usadellab.org/cms/?page=trimmomatic). <br> 
For official article, read [Anthony M. Bolger and others, Trimmomatic: a flexible trimmer for Illumina sequence data, Bioinformatics, Volume 30, Issue 15, August 2014, Pages 2114–2120](https://academic.oup.com/bioinformatics/article/30/15/2114/2390096). 

### Mauve
For official website, go to [mauve](https://darlinglab.org/mauve/mauve.html). <br>
For official article, read [Darling AC, Mau B, Blattner FR, Perna NT. Mauve: multiple alignment of conserved genomic sequence with rearrangements. Genome Res. 2004 Jul;14(7):1394-403. doi: 10.1101/gr.2289704. PMID: 15231754; PMCID: PMC442156.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC442156/). 

### GapFiller
An earlier artical, [Nadalin F, Vezzi F, Policriti A: GapFiller: a preprocessing step for the de novo assembly problem [abstract]. Proceedings on the 8th annual meeting of the Bioinformatics Italian Society. 2011, 13-14](http://bioinformatics.hsanmartino.it/bits_library/library/01025.pdf). <br>
For official artical, read [Nadalin, F., Vezzi, F. & Policriti, A. GapFiller: a de novo assembly approach to fill the gap within paired reads. BMC Bioinformatics 13 (Suppl 14), S8 (2012). https://doi.org/10.1186/1471-2105-13-S14-S8](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-13-S14-S8). 

### Prokka
For official website, go to [Prokka: rapid prokaryotic genome annotation](https://github.com/tseemann/prokka). <br>
For official artical, read [Torsten Seemann, Prokka: rapid prokaryotic genome annotation, Bioinformatics, Volume 30, Issue 14, July 2014, Pages 2068–2069, https://doi.org/10.1093/bioinformatics/btu153](https://academic.oup.com/bioinformatics/article/30/14/2068/2390517).

