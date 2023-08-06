# If statements, While loops, For loops

[Go to main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)

## Example 1: Check if a file exists
Type the followings ``if [ -f file ]; then``, ``echo found``, ``else``, ``echo not found``, ``fi``. This should output "found" if a file named "file" exists and "not found" if it does not exist.
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














[Go to main page](https://github.com/sux21/Batstone_Lab_UNIX_Tutorial/tree/main)
