# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > **List of Command Line Commands:**  
`pwd` (or $PWD, or =+) : prints working directory (which is the current directory you are in)  
`mkdir` (-p is useful) : makes new empty directory of your name choice (-p will make parent and children - can nest down)  
`rmdir` : removes empty directories -rarely like using this (although dangerous rm -r works)  
`touch` : creates a new file with the name you give it - although technically a file timestamp changer  
`rm` : deletes files (-r recursive; -f force)  
`rename` : renames a file(s) - given regex characteristics s(ubstitute)/patternin/patternout/[(g)lobal (i)case] filename(s)  
`ls -a` : a argument lists all files/directories  
`cp` : copy target1 --> target2 (can take arguments like most cli commands)  
`wc` : wordcount  
`mv` : moving files from one place to another  
`echo` : print out command or input  
`ping` : ICMP echo test for network hosts  
`traceroute` : returns number of hops to a server from host machine  
`ip` : show/manipulate routing (also ipstables)  
`netstat` : print network connections, routing tables, stats  
`nmap` : get a network mapping of a target  
`ftp` : file transfer protocol (though unsecure)  
`wget` : non-interactive network downloader  
`curl` : transfer a url (data) to/from a server  
`ssh` : secure shell (logins, transfers, remote controls)  
`$HOME (~)` : returns home directory  
`$PATH` : prints shell path traversal  
`cat` : concantenate files/read files  
`cut` : remove sections from each line of files  
`paste` : merge lines of files  
`join` : join lines of two files on a common field  
`comm` : compare two sorted files line by line  
`diff` : compare files line by line  
`printf` : format and print data  
`tr` : translate or delete characters  
`sort` : sort lines of text  
`uniq` : report or omit repeated lines  
`nl` : number lines  
`fold` : wrap each line to a specified length  
`fmt` : simple text formater  
`grep` : print line matching patterns (general regular expressions)  
`sed` : stream line editor (challenging little beast)  
`head` : output first part of a file (takes args)  
`tail` : output last part of file  
`tee` : read from stdin and write to stdout/files - while also showing in terminal  
`id` : display user identity  
`chmod` : change file modifications ((type)(owner permissions)(group permissions)(world permissions)  
`su/sudo` : run as superuser/root  
`chown` : change owner for files  
`chgrp` : change files groups  
`ps` : report process snapshots (useful with aux but doesnt take a (-) like tar, I don't know why....)  
`top` : display tasks  
`bg/fg` : place job in backgroup or foreground  
`jobs` : list active jobs  
`kill` : kill a single process (PID)  
`killall` : kill processes by name  
`shutdown` : shutdown/restart machine (usually use this with shutdown -r now)  
`tree` : show tree of directories and files  
`pstree` : show a tree of processes  
`vmstat` : snapshot of system resource usage  
`printenv` : print part or all of the environment of shell  
`set` : set shell options and environment variables  
`export` : export environment and subsuquently executed programs  
`alias` : create an alias for a command (lost after shell quit - so is just a temporary alias)  
`PS1=`(set your cli prompt)  
`mount` : mount a file system  
`umount` : unmount a file system  
`fsck` : check and repair file system  
`fdisk` : partition manipulator  
`mkfs` : make file system  
`dd` : STAY AWAY - write block (d)ata (d)irectly  
`ifconfig` : show / configure network interface  
`locate` : find files by name  
`find` : search for files in a directory hierarchy (this one is a beast: has options, tests and actions)  
`xargs` : build and execute command lines from standard input - essentially a utility for building an execution pipeline from stdin - executes /bin/echo over input  
`xargs` - basically used to do some operations on a long(ish!?) list of filenames produced by the previous command; {} arg list marker if taking >1 arg at a time  
`stat` : (file) display file or file system status  
`cron` : executes commands on a preset schedule by daemon (daemon is just a guy who always likes to run behind you)  
---

### Q2.  List Files in Unix  

What do the following commands do (note these differ from Linux and Mac):

> > **ls:**  
`ls`: list files/directories in the current directory  
`ls -a`: list files/directories (a)ll options - so gets hidden files - in current directory  
`ls -l`: list files/directories (l)ong - returns a long list, with each file/dir on a new line and extended information  
`ls -lh`: list files/directories (l)ong (h)uman-readable (honestly with long options I don't think it does anything except turn the file size column into something truncating the 000's - returns a long list, with each file/dir on a new line and extended information    
`ls -lah`: list files/directories (l)ong (a)ll (h)uman-readable - just use ls -al.....   
`ls -t`: list files/directories (t)ime modified - newest on top  
`ls -Glp`: list files/directories (G)(CLIColor Enabled) (l)ong (p)(path extensions further down get an end appended slash (/))  
`ls -Glp`: list files/directories (G)roup-removal (l)ong (p)(path extensions further down get an end appended slash (/))  
---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> >
Command  |  Action
------------ | -------------
`ls -r` | list files/directories (r)everse alphabetical
`ls -al PIPE grep '^d'` | list files/directories directories only
`ls -i` | list files/directories (i)node  
`ls -m` | list files/directories co(m)ma separated  
`ls -Q` | list files/directories (Q)uote names in ""  
`ls -R` | list files/directories (R)ecursively - going to be a big LS depending where you are in a filesystem  
`ls -s` | list files/directories (s)ize  
`ls -1` | list files/directories (1) file per line - good if you want a vertical list of some other combination of the hierarchy  

---

### Q4.  Xargs   
What does `xargs` do? Give an example of how to use it.

> > **xargs:**  
Builds and execute command lines from standard input - essentially a utility for building an execution pipeline from stdin - executes /bin/echo over input. It is basically used to do some operations on a long(ish!?) list of filenames produced by the previous command(s). If run empty on CLI will need to be executed with ctrl+d, can handle delimiters with -d, number of lines to split -n, and ask for user confirmation -p. Mostly useful with CLI commands that accept standard input (grep, awk, find, echo).  

---

> > **examples:**
`echo a b c d | xargs -p`  
#just going to echo a b c d if prompted by user  
`find . -name "*.py" | xargs rm -rf`  
#find files in current directory and its subdirectories ending in .py and loop over removing them  
`find ./foo -type f -name "*.txt" | xargs rm`  
#find files in current directories child foo and under ending in .txt and loop over removing them  
`find . -type f -name "*.md" | xargs wc -m -l`  
#find files in current directory and its subdirectories that are a file and named ending in .md and loop over returning number of lines in each file, number of characters in each file and filename  
`find . -type f -name "*.md" | xargs grep "boom"`   
#find files in current directory and its subdirectories that are files with name ending in .md and search them for a match to word "boom" returning file name and the line(s) containing boom  

---
