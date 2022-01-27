# Terminal and Bash commands

## Paths to files and folders

- [Relative and absolute paths](https://github.com/FoundCompBio-Spr22/Intro_Week1/blob/main/Filesystems.md)

- Compare your answers to the practice exercise about paths with someone next to you. If your answers were different, discuss why.

 ```
 Absolute has the / at the beginning. 
 ```
 
## Practical Computing tips

- [Practical Computing Tips](https://github.com/FoundCompBio-Spr22/Intro_Week1/blob/main/ComputingTips.md)

## Your remote Linux computer

- LSU VPN (to work from off campus) - Available from TigerWare (GlobalProtect VPN Client)

- [ondemand.smic.hpc.lsu.edu](https://ondemand.smic.hpc.lsu.edu)

```
Practice Exercise

(1) Log on to HPC OnDemand
(2) Go to Files -> Home Directory
(3) Look at the header bar at the top. What is the path to your home directory?
(4) Using the "New File" and "New Dir" buttons at the top, create these
    directories and files in your home folder:
  - /home/<yourUserName>/myBiologyClasses - directory
  - /home/<yourUserName>/myBiologyClasses/CellBiology - directory
  - /home/<yourUserName>/myBiologyClasses/CellBiology/CellBioImportantNotes.txt - file
  - /home/<yourUserName>/myBiologyClasses/Ecology - directory
  - /home/<yourUserName>/myBiologyClasses/Ecology/EcologyImportantNotes.txt - file
  - /home/<yourUserName>/myBiologyClasses/Evolution - directory
  - /home/<yourUserName>/myBiologyClasses/Evolution/EvolutionImportantNotes.txt - file
(5) For each of your `.txt` files, click the "Edit" button, add some relevant text,
    and save your changes.
```

```
# Notes 1/27/22
- Current working directory for HPC: Home. Always start with home directory (~ -> indicates home directory)
- PWD "print working directory" shows absolute path to help with navigating where you are. 
- cd -> "change directory", move to a new working directory in homw folder 
- cd -> start typing folder name, "tab" twice shows the folders that match it and will fill in the rest of the name. 
- press up and down arrow on command allows you to scroll through command history. 
- bash -> name of shell we are using when logged into smic shell, we are using this today. 
- zsh is another kind of shell and may need different commands. 
- shell is the environment of commands we can work with on the command line. 
```

## Introduction to the Command Line

### Terminal

 - Built in to Linux (and Mac OS X)
 - By default,__usually__ uses the bash shell (interpreter)
 - The command prompt
 - Tab completion
 	- Double tapping tab will list all files with that beginning
 - Scrolling through history

### Commands related to navigating the filesystem

- `touch filename.txt` will create file
- `pwd` - print working directory - or - "where am I?"
- `ls` - list directory contents
- `ls -l` - long list
    - Everything has three types of permissions
        - Read
        - Write
        - Execute
    - And three groups whose permissions can be controlled
        - Owner
        - Group
        - Others
- [Wikipedia on Unix Permissions](https://en.wikipedia.org/wiki/File_system_permissions#Notation_of_traditional_Unix_permissions)
- `la` - list with hidden files
- `cd` - change directory
    - will accept absolute or relative paths
- `chmod` - change permissions - specify who (ugo), how (+ or -), and what (rwx)
- `man <command>` - gives us the manual page and options for any Unix command (q will get out of manual page)
- [Notes about command-line navigation](https://github.com/FoundCompBio-Spr22/Shell_Week2/blob/main/CommandLine_Navigating.md)

```
# Notes 1/27/22
- view contents of folder "ls" -> list
- touch nameoffile.txt -> creates a new folder quickly
- nano can also make a folder, opens up nano environment and shows us the contents of the file. control x to save it. 
- cat foldername.tst -> displays text stored in the file. cat = concatenate as well. 
- cat is the command and anything we type after is the argument, cat is capable of many command line arguments. 
- wildcards -> * represents any text that can go in a particular pattern. 
    - Ex: cat *.txt -> will find any file with .txt at the end. 
- some commands can take flags, which are options that change the behavior of the command in some way. every command
has it own manual page, which is a description of what the command does. 
    - Ex: man.ls -> shows the manual page for ls, scroll up and down with arrow key. 
    - flags start with a - always. they are case sensitive as well. single letter flags always have a single dash. 
    - there are synonyms for the flags as well, they are listed next to the first one. 
    - exit with "q" -> means quit. 
    - one useful flag is: ls -d which gives us a single dot (.) - always a shortcut for the folder we are currently         in. 
    - .. is a shortcut for the parent of our working directory. 
    - ls -l -> shows us a long list, displaying more info than names of files. directory and file names are color           coded. shows time and date was last edited, file size. 
    - ls -lh -> the h is human-readable sizes, shows sizes we understand. this shows who owns the files and folders,         the root, 9 characters in 3 sets of 3, there are always 3 different kinds of permissions related to a folder: 
            - r -> reading (allow people to read file)
            - w -> writing 
            - x -> executing (when a file is a porgram this is used)
    - the first set of 3 -> permissions to who owns the file directory (user) 
    - the second set -> permissions everyone else in group has (anyone else in users)
    - the third set -> anyone else in users. 
    - we can change permissions -> "chmod ugo (user, group, others) only vhange user, u, u-w indicates losing write permissions then add the file 
        - chmod u-w file.txt -> does not display anything immeduately, but when you type ls -l it will show a difference in the permissions. change to + to add back permissions. 
        - chmod ugo+w file.txt  changes it for everyone. 
        - if you don't own a file, you may not be able to change permissions for it. you must own it. 
- mv (move file using relative or absolute paths) from (file name) to (filename)/
    - file mv file 
- change file name -> mv currentplace.txt newname.txt -this will preserve context of file. 
```

```
Practice Exercise

(1) Use the cd command to navigate up and down through the folders you created in the previous exercise.
(2) After each change of directory, use pwd to check the absolute path of your location.
(3) In folders with text files, use ls to examine the folder's contents.
```

### Commands related to files and folders

- `cp` - copies a file
    - `cp originalFile.txt newFile.txt`
- `mv` - moves __or__ renames a file
    - To change location, use paths: `mv myFile.txt ./folder/myFile.txt`
    - To change name, just use different names: `mv myFile.txt newName.txt`
- `cat filename.txt` - view file contents - can be called on multiple files and will conCATenate their contents
    - `cat file1.txt file2.txt file3.txt` will show all files in command line
    - `cat *.txt` shows all text in files with the file ending .txt
- `ls *.txt` show all files that end in .txt
    - `ls ../*.txt` go up one directory then tell me the txt files there (still within the same directory)
- `head -n #` - view the first # of lines of a file
- `tail -n #` - view the last # of lines of a file
- `less` - view the contents of a file a little at a time nice way to scroll through
- `touch filename.txt` - quickly create a new file
- `nano filename.txt` - this is actually an entire text editing program (type text like normal)
    - write out is save and ^=control (^O) exit (^X)
- `wc` - print out the length of a file in lines, words, and characters

```
**# Notes 1/27/22**
- if file is super long, you may not want to use cat. use head file.txt to show first 10 lines of the file. 
- head -n# changes the number of lines on display
- tail shows the last 10 lines of a file, sometimes the lines can be empty. 
- less -> takes into a new window to scroll up and down file to find what you need. q to exit. 
- wc file.txt - word count that shows the #lines, #words, #characters. 
- mkdir makes a new directory. 
- rmdir deletes directory only if its **empty**. it permnately deletes it. 
- rm* deletes every file in a directory. dont actually use this. 
- echo "text" will write it back to you. 
- echo "text" >> file.txt (>> apends text to the file, redirects output to file instead of displaying back to the screen), see with "cat". 
- echo "text" > file.txt to replace contents of the file. 
```

```
Practice Exercise

(1) Create a file with the touch command.
(2) Make a copy of the file using cp.
(3) Rename the original version of the file to something else with mv.
(4) Use nano to add different text to each copy and save it.
(5) View the contents of each file with cat.
(6) Check the sizes of each file with wc.
```

- `echo` - prints something to the screen (or elsewhere, as directed)
- `>>` - appends to file
    - `echo "some text here" >> myTextFile.txt`
- `>` - writes to (or over!) file
    - `echo "more text here" > myTextFile.txt`
- __WARNING - BIG WARNING - PAY ATTENTION__ - `rm` _permanently_ removes a file
    - No going back - always use this VERY carefully
    - I know people who've accidentally erased their __entire computers__ using this command
    - `rm -r` recursively removes a directory and everything inside it - even more dangerous than just `rm`!
    - This is the reason permissions are so important. If someone doesn't have write permissions on a file or folder, they shouldn't be able to delete it.
- `mkdir MyDirectory` - create a new (empty) directory (folder)
- `rmdir MyDirectory` - remove an empty directory !!WARNING!!
- wildcards - * is especially useful - matches anything
- `grep` - find only lines matching some particular string

```
Practice Exercise

(1) Create a series of new text files, with some filenames starting with one letter and some starting with another.
(2) Use echo and output redirection (> or >>) to add content to the files.
(3) With one command, list all the files that start with one particular letter.
(4) Make a new directory
(5) Move all files that start with one particular letter into the new directory.
(6) Try to remove that directory with rmdir. Can you?
(7) Extract all the lines from the files you created that contain one particular word of your choosing.
```

- [Notes about editing files and folders from the command line](https://github.com/FoundCompBio-Spr22/Shell_Week2/blob/main/CommandLine_Editing.md)

### Commands related to the Unix environment

- Can create a variable and assign value using `=`
    - `myVariable=2`
- Can print value of variable using `echo` and starting name with `$`
    - `echo $myVariable`
- `|` - the Unix pipe can be used to send the output of one command into the input of another
    - `history | tail -n 20 >> endOfHistory.txt`

