Git is a ditributed version control system.
Git is a free software distributed under the GPL.
Git has a mutable index called stage.
Git tracks changes of files.
Creating a new branch is quick and simple.

What is Git?
============
Git is the most advanced distributed version comtrol system. It tracks the changes of all text files, not binary files. Git was created by Linus, who also created linux.  

Install Git
===========
install git on linux(ubuntu):  

    $ sudo apt-get install git

after installing git, the name and email address should be set:  

    $ git config --global user.name "ruanUbuntuVM"
    $ git config --global user.email "ruan.xj92@gmail.com"

Create a repository
===================
find a proper location to create an empty directory:  

    $ cd /home/ubuntu-dv/Documents
    $ mkdir learngit
    $ cd learngit
    
make the directory git trackable:  
    
    $ git init
    
write something in `README.md` and add it in the repository

    $ vim README.md  
    $ git add README.md  

tell git to add the file with `git commit`

    $ git commit -m "wrote a readme file"
    
Time machine
============
check the status of repository with `git status`:  
    
    $ git status
    
see the difference of a file e.g.:  
    
    $ git diff README.md
    
check the modification history with `git log`:  

    $ git log

or a simpler display:  
 
    $ git log --pretty=oneline
    
return to last version:  

    $ git reset --hard HEAD^
    
or return to otehr version:

    $ git rest --hard 3628164
    
`3628164` could be other commit id 
Version returing is veryu fast, because only the pointer is changed.  

Git provids `git reflog` to track all the history commands:  

    $ git reflog

Working directory and stage
---------------------------
Working directory is the directory initiated with `git init`, like '/learngit'.  
There is a hiden directory `.git` in working directory. It is not a working directory but storing a lot, including `stage` and branches.   
`stage` is the temporary directory storing files added by `git add`. `git commit` added the files from `stage` to corelated branch.

manage modification
-------------------
Each modification of files must be `git add filename` into `stage` before added into a branch with `git commit ...`.  
So, `git add ...` adds modification of a file from working directory to `stage`. `git commit ...` adds all the modifacation from `stage` to a branch.  

discard modification
--------------------
use `git checkout -- <file>` to discard changes in working directory before `git add <file>`

	$ git checkout -- <file>

`--` is important, without which `git checkout <branchname>` means change to other branch.

use `git reset HEAD <file>` to diacard changes before `git add <file>`

	$ git reset HEAD <file>

delete files
------------
Normly delete a file on linux:  

	$ rm <file>

Delete a file from a git repository:  

	$ git rm <file>

If you regret, and want to recover the file from repository:  
	
	$ git checkout -- <file>

Remote repository
=================
GitHub.com is a website keeping git repositories. It could be used to keep public repositories remotely.
Before really starting using github, SSH key is required. SSH key is generated:  

	$ ssh-keygen -t rsa -C "<emailaddress>"

Input all the required information if necessary, otherwise, let them be default or empty.
Find SSH key pair in 

	$ cd ~/.ssh

copy the content in `id_rsa.pub`. paste them in   
github.com ==> personal settings ==> SSH & GPG Keys ==> New SSH Key  
input tile and paste public key in `key`, click `Add SSH key`  
Adding remote repository
------------------------
Since having a local git repository and remote git repository, here is how them work together.
first create a remote repository:  

github.com ==> New repository ==> input the name as remoteRepositoryname and description ==> Create repository  

connect local repository with remote repository:  

	$ git remote add origin git@github.com:<yourGitHubName>/<remoteRepositoryname>.git
 
`origin` is the default name of git. 
push the content of local repository to remote:

	git push -u origin master

after pushing, the repository can be seen on github.com
Now, any changed in local git repository can be pushed to remote repository:  

	git push origin master

SSH warning
-----------
The fisrt `clone` or `push` to github may receive a massage from github like:  

	The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
	RSA key fingerprint is xx.xx.xx.xx.xx.
	Are you sure you want to continue connecting (yes/no)?

clone from remote repository:  

	git clone <remoteRepository>

e.g. `git clone git@github.com:michaelliao/gitskills.git` 
<remoteRepository> supports https and ssh supported origin git:// address.
