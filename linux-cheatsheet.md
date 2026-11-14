# Linux cheat sheet

## Moving around
## ls
- lists whats in a folder
- exanple: ls -a to list all files including hidden ones
- gotcha: plain ls hodes files starting with a dot: -a shows them
- learned: Bandit, hidden file level

## cd
- change directory into a child/sub folder
- example: cd inhere
- gotcha: cd only works when moving from a folder into another. cd .. goes back to the parent folder
- learned: All Bandit level

## pwd
- print working directory
- example: pwd
- gotcha: to show thw directory a command is being run 
- learned: Hack the box

## Paths: / at the start vs no / at the start
- / at the start means the command to run at the topmost folder in the working directory
- example: find / means to find from the topmost folder
- gotcha: when / is not at the start, it means the command will go through all the entire working directory without bein constrained to the topmost one
- learned: bandit

## Reading files
## cat
- show a file content
- example: cat data.txt
- gotcha: this is used to view the information inside a partcular file. the result may useful depending on the file type and permissions
- learned: bandit

## file
- to determin the type of data in a file
- exammple: file data.txt
- gotcha: 
- learned: linux command org and bandit

## strings
- convert the data inside a file to strings

## Searching
## find (shape: find WHERE TESTS)
- find is used to find a file in a directory. the file being searched may have different option

## grep   (shape: grep PATTERN FILE)
- used to find a paatern in a file 
- when dealing with strings input when chained to pipe symbol, the pattern should be in quotes
## Chaining commands
## |  (pipe)
- used to chain commands 
- the command before | serves as input to the ones after

## >  and  >>
- >: writes output to a file to replace whats there
- >>: writes output to the end of a file
- learned: linux command org

## 2>/dev/null
- throws away error compression to return only useful data
- learned: bandit

## Changing text
## sort
-s

## uniq
- finds unique items ina file and either retuns how many times they are repeated or ignores them
- learn: bandit

## base64
- converts a data into base64 format
- if -d is added as a suffix, it decode the base64 to human readable strings

## Characters that trick you
## .  (current folder, or a hidden file at the start of a name)
## -  (start of an option)
## --  (end of options)
## "quotes"  (keep spaces together)
## ~  (home)

## Keys
## Tab
## Ctrl+C vs Ctrl+Z
## Ctrl+Shift+C / Ctrl+Shift+V
