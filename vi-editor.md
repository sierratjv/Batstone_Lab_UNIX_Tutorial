# vi editor
Learn how to use vi editor

Type ``vimtutor`` to open the tutorial page. 

A summary of this tutorial is below:

### Lesson 1.1:  MOVING THE CURSOR
To move the cursor, press the h,j,k,l keys as indicated. You can also use arrow keys on keyboard. 
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
Type ce to delete to the end of a word, including the character at the cursor. It will be in the INSERT mode to make new changes.

Type cc to delete the whole line. It will be in the INSERT mode to make new changes.
```
### Lesson 3.4: MORE CHANGES USING c
```
c    [number]   motion

for example, c$ will delete to the end of the line. It will be in the INSERT mode to make new changes.
```
### Lesson 4.1: CURSOR LOCATION AND FILE STATUS
To see the filename and position in the file, type 
```
CTRL G
```
To set ruler, type
```
:set ruler
```
To go to the start of the file, type
```
gg
```
To go to the bottom of the file, type
```
G
```
To go to a specific line, type
```
the line number and the type G
```
### Lesson 4.2: THE SEARCH COMMAND
To search a word in forward direction, type
```
\word and press <ENTER>. To search for the same phrase again, simply type  n. To search for the same phrase in the opposite direction, type  N 
```
To search a word in backward direction, type
```
?word and press <ENTER>. Use n or N to go to the next word. 
```
To go back where you came from, press
```
CTRL + O. Press CTRL + I to go forward.
```
### Lesson 4.3: MATCHING PARENTHESES SEARCH
To find a matching brackets, such as ),], or }, place cursor on the bracket and type
```
%
```
### Lesson 4.4: THE SUBSTITUTE COMMAND
To substitute one word, type
```
:s/old word/new word
```
To substitute all words in a line, type
```
:s/old word/new word/g 
```
To substitute words between two lines, type
```
:#,#s/old word/new word/g          (#, # are the line numbers)
```
To subtitute all words in the file, type
```
:%s/old word/new word/g
```
To ask for confirmation before substituting, type
```
:%s/old word/new word/gc
```
### Lesson 5.1: HOW TO EXECUTE AN EXTERNAL COMMAND
Type
```
:!command <ENTER>

for example, type :!ls
```
### Lesson 5.2: MORE ON WRITING FILES
To save changes and name file, type
```
:w FILENAME
```
To remove the file, type
```
:!rm TEST
```
### Lesson 5.3: SELECTING TEXT TO WRITE
To save part of the file, type
```
v  motion  :w FILENAME
```
### Lesson 5.4: RETRIEVING AND MERGING FILES
To insert another file, type
```
:r FILENAME
```
### Lesson 6.1: THE OPEN COMMAND 
```
Type  o  to open a line below the cursor and place you in Insert mode. Type capital O to open a line above cursor.
```
### Lesson 6.2: THE APPEND COMMAND
```
Type  a  to insert text AFTER the cursor. This will open the INSERT mode.
```
### Lesson 6.3: ANOTHER WAY TO REPLACE
```
Type a capital  R  to replace more than one character. This will open the REPLACE mode. 
```
### Lesson 6.4: COPY AND PASTE TEXT
```
Type v to open VISUAL to select text to copy

Type y to copy

Type p to paste
```
### Lesson 6.5: SET OPTION
To search a word without considering it is upper-case or lower-case, type
```
:set ic

To disable this option, type :set noic

Examples of some options:
'ic' 'ignorecase'       ignore upper/lower case when searching
'is' 'incsearch'        show partial matches for a search phrase
'hls' 'hlsearch'        highlight all matching phrases

use "no" in front of the option to disable the option
```
### Lesson 7.1: GETTING HELP
Type 
```
:help
```
some options:
:help w
:help c_CTRL-D
:help insert-index
:help user-manual
### Lesson 7.2: CREATE A STARTUP SCRIPT
Set your defaults using .vimrc
```
Create a .vimrc in your home directory(~):  touch .vimrc 

Edit .vimrc when you are in another file, type :e ~/.vimrc to ope            
```
### Lesson 7.3: COMPLETION
```
  1. Make sure Vim is not in compatible mode:  :set nocp

  2. Look what files exist in the directory:  :!ls   or  :!dir

  3. Type the start of a command:  :e

  4. Press  CTRL-D  and Vim will show a list of commands that start with "e".

  5. Type  d<TAB>  and Vim will complete the command name to ":edit".

  6. Now add a space and the start of an existing file name:  :edit FIL

  7. Press <TAB>.  Vim will complete the name (if it is unique).

NOTE:  Completion works for many commands.  Just try pressing CTRL-D and
       <TAB>.  It is especially useful for  :help .
```

