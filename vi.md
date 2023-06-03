# vi editor
Learn how to use vi editor

Type ``vimtutor`` to open the tutorial page. 

A summary of this tutorial is below:

### Lesson 1.1:  MOVING THE CURSOR
**To move the cursor, press the h,j,k,l keys as indicated.**
```
             ^
             k              
       < h       l >              
             j                     
             v
```
 ### Lesson 1.2: EXITING VIM
To exit without saving changes, type
```
 :q! <ENTER> 
```
or type
```
ZZ
```
### Lesson 1.3: TEXT EDITING - DELETION
```
Press the  x  key to delete the unwanted character.
```
### Lesson 1.4: TEXT EDITING - INSERTION
```
Press  i  and type in the necessary additions. This is the INSERT mode. Press <ESC> to return to NORMAL mode. 
```
### Lesson 1.5: TEXT EDITING - APPENDING
```
Press  A  and type in the necessary additions. Cursor is placed at the end of a line. This is the INSERT mode. 
```
### Lesson 1.6: EDITING A FILE
To save changes and exit, type
```
:wq <ENTER>
```
### Lesson 2.1: DELETION COMMANDS
To delete a word, move cursor to the beginning of the word, and type
```
dw
```
### Lesson 2.2: MORE DELETION COMMANDS
To delete to the end of the line, type
```
d$
```
### Lesson 2.3: ON OPERATORS AND MOTIONS
```
        d   motion

  Where:
    d      - is the delete operator.
    motion - is what the operator will operate on (listed below).

  A short list of motions:
    w - until the start of the next word, EXCLUDING its first character.
    e - to the end of the current word, INCLUDING the last character.
    $ - to the end of the line, INCLUDING the last character.
    
  Thus typing  de  will delete from the cursor to the end of the word.
 
  NOTE: Pressing just the motion while in Normal mode without an operator will
        move the cursor as specified.
```
### Lesson 2.4: USING A COUNT FOR A MOTION
```
Type  2w  to move the cursor two words forward.

Type  3e  to move the cursor to the end of the third word forward.

Type  0  (zero) to move to the start of the line.
```
### Lesson 2.5: USING A COUNT TO DELETE MORE
```
d   number   motion

for example, type d2w to delete two words
```
### Lesson 2.6: OPERATING ON LINES
To delete the a line, type 
```
dd
```
### Lesson 2.7: THE UNDO COMMAND
```
Press  u  to undo the last commands

Press U to undo the changes of the whole line

Press CTRL-R to undo the undos
```
### Lesson 3.1: THE PUT COMMAND
```
Type  dd  to delete the line.

Type p to put this line a line under the cursor.
```
### Lesson 3.2: THE REPLACE COMMAND
```
Type  rx  to replace the character at the cursor with  x
```
### Lesson 3.3: THE CHANGE OPERATOR
```
Type ce to delete to the end of a word, including the character at the cursor

Type cc to delete the whole line
```
### Lesson 3.4: MORE CHANGES USING c





