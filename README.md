Git is a ditributed version control system.
Git is a free software distributed under the GPL.
Git has a mutable index called stage.
Git tracks changes of files.
Creating a new branch is quick and simple.

What is Git?
============
Git is the most advanced distributed version comtrol system. It tracks the changes of all text files, not binary files. Git was created by Linus, who also created linux.  

install Git
===========
install git on linux(ubuntu):  

    $ sudo apt-get install git

after installing git, the name and email address should be set:  

    $ git config --global user.name "ruanUbuntuVM"
    $ git config --global user.email "ruan.xj92@gmail.com"

create a repository
===================
find a proper location to create an empty directory:  

    $ cd /home/ubuntu-dv/Documents
    $ mkdir learngit
    $ cd learngit
    
make the directory git trackable:  
    
    $ git initubuntu-dv@ubuntudv-VirtualBox:~
    
write something in `README.md` and add it in the repository

    $ vim README.md  
    $ git add README.md  

tell git to add the file with `git commit`

    $ git commit -m "wrote a readme file"
    
time machine
============
check the status of repository with `git status`:  
    
    $ git status
    
see the changes of a file e.g.:  
    
    $ git diff README.md
    
check the change history with `git log`:  

    $ git log

or a simpler display:  
 
    $ git log --pretty=oneline
    
return to last version:  

    $ git reset --hard HEAD^
    
or return to otehr version:

    $ git rest --hard 3628164
    
`3628164` could be other commit id 
Version returing is veryu fast, because only the pointer is changed.  

