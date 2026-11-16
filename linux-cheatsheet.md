# Linux cheat sheet

## Moving around
## ls
- lists whats in a folder
- example: ls -a to list all files including hidden ones
- gotcha: plain ls hides files starting with a dot: -a shows them
- learned: Bandit, hidden file level

## cd
- change directory into a child/sub folder
- example: cd inhere
- gotcha: cd only works when moving from a folder into another.
 cd .. goes back to the parent folder. cd on a file gives "Not a directory"
- learned: All Bandit level

## pwd
- print working directory
- example: pwd
- gotcha: to show the directory a command is being run 
- learned: Hack the box

## Paths: / at the start vs no / at the start
- / at the start means the command to run at the top of the whole file system it is being run
- example: find /
- gotcha: when / is not at the start, it means the command will start from the current folder
- learned: bandit

## Reading files
## cat
- show a file content
- example: cat data.txt
- gotcha: this is used to view the information inside a partcular file.
 the result maybe useful depending on the file type and permissions.
cat on a binary file prints garbage in the terminal so "reset" is used to  fixe the terminal.
cat fails when a name starts with "-" unless it is written as "./-"
- learned: bandit

## file
- to determine the type of data in a file
- example: file data.txt
- gotcha: file judges by the content in a file and not neccessarily by extension
- learned: linux command org and bandit

## strings
- prints the human readable part of a file. 
- gotcha: it comes before grep on a binary file.
- example: strings data.txt
- learned: bandit

## Searching
## find (shape: find WHERE TESTS)
- find is used to find a file in a directory. 
the file being searched may have different option
- example: find / -type f means to find in the top of the whole file system for a 
file format that is human readable.
- gotcha: every test start with a -. c means bytes, ! reverses a test.

## grep   (shape: grep PATTERN FILE)
- used to find a paatern in a file 
- when dealing with strings patterns, the pattern should be in quotes or the shell
treats its like "*, |, >, $, !"

## Chaining commands
## |  (pipe)
- used to chain commands 
- the command before | serves as input to the ones after

## >  and  >>
- >: writes output to a file to replace whats there
- >>: writes output to the end of a file
- learned: linux command org

## 2>/dev/null
- throws away error messages to return only useful data. the 2 means stream 2, the 
error stream. stream 1 is a normal output and is printed on the screen.
- learned: bandit

## Changing text
## sort
- used to arrange lines in a file in a specific order. it has multiple options
- "-r" sorts in descending oerder
"-u" removes duplicates from sorted output
"-c" checks if a file is already sorted without printing the content into terminal

## unique
- comapres lines in a file that are next to eachother to find uniqueness
- learn: bandit

## base64
- encodes a data into base64 format
- if -d is added as an option, it decode the base64 to human readable strings
-without -d, base64 encodes. 

## Tricky characters
## .  (current folder, or a hidden file at the start of a name)
## -  (start of an option)
## --  (end of options)
## "quotes"  (keep spaces together)
## ~  (home)

## Keys
## Tab
## Ctrl+C vs Ctrl+Z
## Ctrl+Shift+C / Ctrl+Shift+V

