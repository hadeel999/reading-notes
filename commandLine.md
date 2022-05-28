# Bash Command Line Tutorials

## The Command Line
A command line, or terminal, is a text based interface to the system. Tou can type these cpmmands by your keyboard and feedback will be displayed under your command as a text.
The command line typically presents you with a prompt. As you type, it will be displayed after the prompt. Most of the time you will be issuing commands.

### Opening a terminal:
- If you're on a Mac then you'll find the program Terminal under Applications -> Utilities. An easy way to get to it is the key combination 'command + space' which will bring up Spotlight, then start typing Terminal and it will soon show up.
- If on Linux then you will probably find it in Applications -> System or Applications -> Utilities. Alternatively you may be able to 'right-click' on the desktop and there may be an option 'Open in terminal'.
- If you are on Windows and intend to remotely log into another machine then you will need an SSH client. A rather good one is Putty (free).

 
## Basic Navigation
Many tasks rely on being able to get to, or reference the correct location in the system. To do this, use these comands in below:
- pwd: Print Working Directory - ie. where are we currently.
- ls: List the contents of a directory.
- cd: Change Directories - ie. move to another directory.

### Important conepts:
#### Relative path: 
A file or directory location relative to where we currently are in the file system.
#### Absolute path:
A file or directory location in relation to the root of the file system.


## More About Files
New commands to get more about files:
- file: Obtain information about what type of file a file or directory is.
- ls -a: List the contents of a directory, including hidden files.

### Important concepts:
#### Everything is a file under Linux:
Even directories.
#### Linux is an extensionless system:
Files can have any extension they like or none at all.
#### Linux is case sensitive:
So you must beware of typos.


## Manual Pages
The manual pages are a set of pages that explain every command available on your system including what they do, the specifics of how you run them and what command line arguments they accept.
- man <command>: Look up the manual page for a particular command.
- man -k <search term>: Do a keyword search for all manual pages containing the given search term.
- /<term>: Within a manual page, perform a search for 'term'.
- n: After performing a search within a manual page, select the next found item.
- q: To exit from man pages.


## File Manipulation
New commands to deal with files:
- mkdir: Make Directory - ie. Create a directory.
- rmdir: Remove Directory - ie. Delete a directory.
- touch: Create a blank file.
- cp: Copy - ie. Copy a file or directory.
- mv: Move - ie. Move a file or directory (can also be used to rename).
- rm: Remove - ie. Delete a file.

### Important concepts:
#### No undo:
The Linux command line does not have an undo feature. Perform destructive actions carefully.
#### Command line options:
Most commands have many useful command line options. Make sure you skim the man page for new commands so you are familiar with what they can do and what is available.


## Cheat Sheet
A quick reference for the main points covered in this tutorial. [Cheat Sheet](https://ryanstutorials.net/linuxtutorial/cheatsheet.php)