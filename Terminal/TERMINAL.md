# Prep: Terminal 
### ``Terminals``, also known as ``command lines`` or ``consoles``, allow us to accomplish and automate tasks on a computer without the use of a graphical user interface. Using a terminal allows us to send simple text commands to our computer to do things like navigate through a directory or copy a file, and form the basis for many more complex automations and programming skills.

---

# The Command Line!
### A ``command line``, or ``terminal``, is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text.

## Here is an example:
```
 1. hashemsmadi:  ls -l /home/hashemsmadi
 2. drwxr-xr-x  3 hashemsmadi hashemsmadi  4096 Jan 16 20:04 my-notes
 3. drwxr-xr-x  6 hashemsmadi hashemsmadi  4096 Feb 16 22:20 netflix-clone
 4. drwxr-xr-x 34 hashemsmadi hashemsmadi  4096 Feb 15 17:29 node_modules
 5. hashemsmadi:

```
* Line 1 presents us with a prompt  ``hashemsmadi``. After that we entered a command ``ls``. Typically a command is always the first thing you type. After that we have what are referred to as command line arguments  ``ls -l /home/hashemsmadi``. Important to note, these are separated by spaces ``there must be a space between the command and the first command line argument also``. The first command line argument ``-l``  is also referred to as an option. Options are typically used to modify the behaviour of the command. Options are usually listed before other arguments and typically start with a dash `` -`` .
* Lines 2 - 4 are output from running the command. Most commands produce output and it will be listed straight under the issuing of the command. Other commands just perform their task and don't display any information unless there was an error.
* Line 5 presents us with a prompt again. After the command has run and the terminal is ready for you to enter another command the prompt will be displayed. If no prompt is displayed then the command may still be running (you will learn later how to deal with this).
--- 
# Basic Navigation!
### The first command we are going to learn is ``pwd`` which stands for Print Working Directory.  The command does just that. It tells you what your current or present working directory is. Give it a try now.
```
1. hashemsmadi: pwd
2. /mnt/c/Users/Smadi
3. hashemsmadi:
```
---

### It's one thing to know where we are. Next we'll want to know what is there. The command for this task is ``ls``. It's short for list. Let's give it a go.
---
```
1. hashemsmadi: ls
2. HR-management-system   Movies__Library   Netflix-Clone2
3. hashemsmadi:

```
---
```
 ls [options] [location] 
 ```
---
```
1. hashemsmadi: pwd
2. /mnt/c/Users/Smadi
3. hashemsmadi: ls Documents
4. file1.txt file2.txt file3.txt
5. ...
6. hashemsmadi: ls /home/hashemsmadi/Documents
7. file1.txt file2.txt file3.txt

```
---
* Line 1 - We ran ``pwd`` just to verify where we currently are.
* Line 4 - We ran ``ls`` providing it with a relative path. Documents is a directory in our current location. This command could produce different results depending on where we are. If we had another user on the system, bob, and we ran the command when in their home directory then we would list the contents of their Documents directory instead.
* Line 7 - We ran ls providing it with an absolute path. This command will provide the same output regardless of our current location when we run it.
---
```
cd [location]
```
---
```
hashemsmadi: cd Documents
hashemsmadi: ls
file1.txt file2.txt file3.txt
```
---
##### If you run the command cd without any arguments then it will always take you back to your home directory.

# Summary
```
pwd
Print Working Directory - ie. Where are we currently.

ls
List the contents of a directory.

cd
Change Directories - ie. move to another directory.

```
``` 
Relative path
A file or directory location relative to where we currently are in the file system.

Absolute path
A file or directory location in relation to the root of the file system.
```
---
# More About Files!
### Ok, the first thing we need to appreciate with linux is that under the hood, everything is actually a file. A text file is a file, a directory is a file, your keyboard is a file
## Linux is Case Sensitive

### This is very important and a common source of problems for people new to Linux. Other systems such as Windows are case insensitive when it comes to referring to files. Linux is not like this. As such it is possible to have two or more files and directories with the same name but letters of different case.
# Summary

```
file
obtain information about what type of file a file or directory is.

ls -a
List the contents of a directory, including hidden files.
```
---
```
Everything is a file under Linux
Even directories.

Linux is an extensionless system
Files can have any extension they like or none at all.

Linux is case sensitive
Beware of silly typos. 
```
---
# Manual Pages!
## The manual pages are a set of pages that explain every command available on your system including what they do, the specifics of how you run them and what command line arguments they accept.
---
``man <command to look up>``
---
```
1. hashemsmadi: man ls
2. Name
3.     ls - list directory contents
4.  
5. Synopsis
6.    ls [option] ... [file] ...
7.  
8. Description
9.    List information about the FILEs (the current directory by default). 10. Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.
10.  
11.    Mandatory arguments to long options are mandatory for short options too.
12. 
13.    -a, --all
14.        do not ignore entries starting with .
15. 
16.    -A, --almost-all
17.        do not list implied . and ..
 
...

```
---
## Let's break it down:

* Line 3 tells us the actual command followed by a simple one line description of it's function.
* Lines 6 is what's called the synopsis. This is really just a quick overview of how the command should be run. Square brackets ``[ ]`` indicate that something is optional. ``(option on this line refers to the command line options listed below the description)``
* Line 9 presents us with a more detailed description of the command.
* Line 11 onwards Below the description will always be a list of all the command line options that are available for the command.

``Tip: To exit the man pages press 'q' for quit.``

## Searching
### It is possible to do a keyword search on the Manual pages. This can be helpful if you're not quite sure of what command you may want to use but you know what you want to achieve. 
---
``` 
man -k <search term>
```
---
#### If you want to search within a manual page this is also possible. To do this, whilst you are in the particular manual page you would like to search press forward slash ``/`` followed by the term you would like to search for and hit ``enter`` If the term appears multiple times you may cycle through them by pressing the ``n`` button for next.

# Summary

```
man <command>
Look up the manual page for a particular command.
man -k <search term>
Do a keyword search for all manual pages containing the given search term.
/<term>
Within a manual page, perform a search for 'term'
n
After performing a search within a manual page, select the next found item.

```
---
``The man pages are your friend.
Instead of trying to remember everything, instead remember you can easily look stuff up in the man pages.
``

---
# File Manipulation!

## We've got some basic foundation stuff out of the way. Now we can start to play around. To begin with we'll learn to make some files and directories and move them around. 
 
# Making a Directory
### Linux organises it's file system in a hierarchical way. Over time you'll tend to build up a fair amount of data . It's important that we create a directory structure that will help us organise that data in a manageable way. I've seen way too many people just dump everything directly at the base of their home directory and waste a lot of their time trying to find what they are after amongst 100's (or even 1000's) of other files. Develop the habit of organising your stuff into an elegant file structure now and you will thank yourself for years to come.
---
``mkdir [options] <Directory>
``
---
```
1. hashemsmadi: pwd
2. /mnt/c/Users/Smadi
3. hashemsmadi:
4. hashemsmadi: ls
5. bin Documents public_html
6. hashemsmadi:
7. hashemsmadi: mkdir linuxtutorialwork
8. hashemsmadi: ls
9. bin Documents linuxtutorialwork public_html
```
---
* Line 1 Let's start off by making sure we are where we think we should be. (In the example above I am in my home directory)
* Lines 2 We'll do a quick listing so we know what is already in our directory.
* Line 7 Run the command mkdir and create a directory linuxtutorialwork (a nice place to put further work we do relating to this tutorial just to keep it separate from our other stuff).
---
### There are a few useful options available for ``mkdir``. Can you remember where we may go to find out the command line options a particular command supports?
### The first one is ``-p`` which tells ``mkdir`` to make parent directories as needed (demonstration of what that actually means below). The second one is ``-v`` which makes mkdir tell us what it is doing (as you saw in the example above, it normally does not).
---
```
hashemsmadi: mkdir -p linuxtutorialwork/foo/bar
hashemsmadi:
hashemsmadi:cd linuxtutorialwork/foo/bar
hashemsmadi: pwd
/home/ryan/linuxtutorialwork/foo/bar
```
---
## Copying a File or Directory
### There are many reasons why we may want to make a duplicate of a file or directory. Often before changing something, we may wish to create a duplicate so that if something goes wrong we can easily revert back to the original. The command we use for this is cp which stands for copy.
---
``cp [options] <source> <destination>``
---
```
hashemsmadi: ls
example1 foo
hashemsmadi:
hashemsmadi: cp example1 barney
hashemsmadi: ls
barney example1 foo
```
---
# Summary
```
mkdir
Make Directory - ie. Create a directory.

rmdir
Remove Directory - ie. Delete a directory.

touch
Create a blank file.

cp
Copy - ie. Copy a file or directory.

mv
Move - ie. Move a file or directory (can also be used to rename).

rm
Remove - ie. Delete a file.

```
```
No undo
The Linux command line does not have an undo feature. Perform destructive actions carefully.

Command line options
Most commands have many useful command line options. Make sure you skim the man page for new commands so you are familiar with what they can do and what is available.
```
---
















