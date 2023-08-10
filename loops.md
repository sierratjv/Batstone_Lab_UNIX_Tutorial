# If statements, While loops, For loops

[Go to main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)

## Example 1: Check if a file exists
Type ``if [ -f file ]; then``, ``echo found``, ``else``, ``echo not found``, ``fi``. This should output "found" if a file named "file" exists and "not found" if it does not exist.
```
[xingyuan@info114 unix_workshop]$ if [ -f file ]; then
> echo found
> else
> echo not found
> fi
not found
```
You can also write the if statement in a script. Type ``vi example1.sh`` to create and edit a file. Type the following in the script (The first line has to be ``#!/bin/bash`` which tells the computer to run the script using bash because the default shell is sh):
```
#!/bin/bash
if [ -f file ]; then
  echo found
else
  echo not found
fi
```
Press <kbd>ZZ</kbd> to save and exist the script. Type ``more example1.sh`` to view the script. Type ``chmod +x example1.sh`` to make the script executable. Type ``./example1.sh`` to run the script. It should give "found" or "not found".
```
[xingyuan@info114 unix_workshop]$ vi example1.sh 
[xingyuan@info114 unix_workshop]$ more example1.sh 
#!/bin/bash
if [ -f file ]; then
  echo found
else
  echo not found
fi
[xingyuan@info114 unix_workshop]$ chmod +x example1.sh 
[xingyuan@info114 unix_workshop]$ ./example1.sh
not found
```

## Example 2: Extract sequences from a file
Type ``vi example2.fasta`` and copy the following DNA sequences to the file:
```
>seq1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCG
>seq2
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCG
>seq3
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCG
>seq4
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCG
>seq5
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCG
```
The following script will extract the first sequence in the list:
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
This should be the output from the script:
```
[xingyuan@info114 unix_workshop]$ vi example2.sh
[xingyuan@info114 unix_workshop]$ chmod +x example2.sh 
[xingyuan@info114 unix_workshop]$ ./example2.sh < example2.fasta 
>seq1
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCG
I am done everything in the file
```
## Example 3: Extract any sequences (using the sequences file from example 2)
Try this script:
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
```
If you want the 4th sequence, you can do:
```
[xingyuan@info114 unix_workshop]$ vi example3.sh 
[xingyuan@info114 unix_workshop]$ chmod +x example3.sh 
[xingyuan@info114 unix_workshop]$ ./example3.sh 4 < example2.fasta 
>seq4
ACCGCTACATCTCCATCTTCTACATCGTTCCTCCAACTCCTTATCAGATCG
```
## Example 4: Print 1 to 10 using a for loop 
Type ``for i in {1..10}; do``, ``echo $i``, ``done``. This should give:
```
[xingyuan@info114 unix_workshop]$ for i in {1..10}; do
> echo $i
> done
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
```
## Example 5: Use for loop to run a software for multiple samples
**If you know how to run a program for one sample, you can use for loop to run it for all your samples. Below is an example of running a program call SPAdes (a genome assembler for bacteria and some viruses)**
```
#!/bin/bash
for R1 in *R1*; do
R2=${R1//R1_P_001.fastq.gz/R2_P_001.fastq.gz}

spades.py --careful -1 $R1 -2 $R2 -o /home/xingyuan/rhizo_ee/spades_assembly/${R1%_*_L002_*gz}
done
```
``*R1*`` picks up all the files containing R1 and stores the files into the variable R1 (type ``echo $R1`` should show all the files). This line ``R2=${R1//R1_P_001.fastq.gz/R2_P_001.fastq.gz}`` modifies variable R1 to a new variable R2. ``${R1%_*_L002_*gz}`` is the output directory name which is also modified from variable R1. Learn how to manipulate strings at https://tldp.org/LDP/abs/html/string-manipulation.html. 



[Go to main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)
