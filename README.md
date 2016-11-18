Installation of git

sudo apt-get update
sudo apt-get install git

Create your workspace

moin@moin-VirtualBox:~$ mkdir laravel
moin@moin-VirtualBox:~$ cd laravel
moin@moin-VirtualBox:~/laravel$

Introduce yourself

moin@moin-VirtualBox:~/laravel$ git config --global user.email "mointestapp1@gmail.com"
moin@moin-VirtualBox:~/laravel$ git config --global user.name "mointestapp1"


moin@moin-VirtualBox:~/laravel$ git config --list

user.email=mointestapp1@gmail.com
user.name=mointestapp1
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true


moin@moin-VirtualBox:~/laravel$ nano ~/.gitconfig

[user]
    name = mointestapp1
    email = mointestapp1@gmail.com


Intiallize git in your directory

moin@moin-VirtualBox:~/laravel$ git init


Create ssh key for secure transaction with your remote git repository

moin@moin-VirtualBox:~/laravel$ cd ~/.ssh && ssh-keygen

moin@moin-VirtualBox:~/.ssh$ ls

id_rsa  id_rsa.pub  known_hosts

moin@moin-VirtualBox:~/.ssh$ nano id_rsa.pub

copy this key and add it to your remote git repository web github.com

profile->Settings->SSH and GPG keys->New SSH key->


Title-> "personal windows"
Paste your key into the "Key" field. 


Clone from remote repository

moin@moin-VirtualBox:~/laravel$ git clone git@github.com:mointestaap1/projectmoin.git

Cloning into 'projectmoin'...
remote: Counting objects: 7, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 7 (delta 0), reused 4 (delta 0), pack-reused 0
Receiving objects: 100% (7/7), done.
Checking connectivity... done.


Add file to your local repo


moin@moin-VirtualBox:~/laravel$ git add .

moin@moin-VirtualBox:~/laravel$ git commit -m "Initial Commit" -a


Message will be applied to all added or modified files. This is okay for the first commit.


moin@moin-VirtualBox:~/laravel$ git add moin.txt

moin@moin-VirtualBox:~/laravel$ git commit -m "second Commit" moin.txt


Message will be applied to moin.txt file only in ssecond commit.


Push your changes to the remote server

moin@moin-VirtualBox:~/laravel$ git remote add origin git@github.com:mointestaap1/projectmoin.git
moin@moin-VirtualBox:~/laravel$ git remote -v

origin	git@github.com:mointestaap1/projectmoin.git (fetch)
origin	git@github.com:mointestaap1/projectmoin.git (push)


To remove your remote server address

moin@moin-VirtualBox:~/laravel$ git remote rm origin
moin@moin-VirtualBox:~/laravel$ git remote -v

Now push your code to master branch of your repository

moin@moin-VirtualBox:~/laravel$ git push origin master


Branch creation under the same directory

Branches are used to develop features isolated from each other. The master branch is the "default" branch when you create a repository. Use other branches for development and merge them back to the master branch upon completion.

create a new branch named "feature_x" and switch to it using

moin@moin-VirtualBox:~/laravel$ git checkout -b child

moin@moin-VirtualBox:~/laravel$ touch tanim.txt
moin@moin-VirtualBox:~/laravel$ git add .
moin@moin-VirtualBox:~/laravel$ git commit -m "adf" -a

moin@moin-VirtualBox:~/laravel$ git push origin child

Switch back to master

moin@moin-VirtualBox:~/laravel$ git checkout master

Merging all the content of child to master

moin@moin-VirtualBox:~/laravel$ git merge child

Next delete the child branch again

moin@moin-VirtualBox:~/laravel$ git branch -d child

In case you did something wrong, you can replace local changes using the command

moin@moin-VirtualBox:~/laravel$ git checkout index.php

If you instead want to drop all your local changes and commits, fetch the latest history from the server and point your local master branch at it like this

moin@moin-VirtualBox:~/laravel$ git fetch origin
moin@moin-VirtualBox:~/laravel$ git reset --hard origin/master
