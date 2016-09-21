---
author: admin
comments: false
date: 2014-09-05 17:55:12+00:00
layout: post
link: https://witr.net/quotation/?p=662
slug: extract-git-repository-sub-folder-as-new-git-repository
title: extract git repository sub-folder as new git repository
wordpress_id: 662
categories:
- git
---


**Problem :**

we have a git repository located in user@server:/home/witr/git-repos/witr.git
witr.git contains 3 projects: proj1, proj2 and proj3
projects are growing up. And cloning witr.git become too slow cause of the size.

**Solution :**
extract each project as a new git repository.
Follow steps bellow to extract proj1 (do the same for other projects).

1. on server : initialize new git repository proj1

    
    
    $ cd /home/witr/git-repos
    $ git init --bare proj1
    


2. on local machine : extract proj1 as new git 

    
    
    $ git clone user@server:/home/witr/git-repos/witr.git
    $ cd witr
    $ git branch branch-proj1
    $ git filter-branch -f --subdirectory-filter path/to/proj1 branch-proj1
    $ cd ..
    $ mkdir proj1-tmp
    $ cd proj1-tmp
    $ git init
    $ git pull ../witr branch-proj1
    $ git remote add proj1 user@server:/home/witr/git-repos/proj1.git
    $ git push proj1 master
    


3. on local machine : ensure that all is right

    
    
    $ cd /path/tmp/
    $ git clone user@server:/home/witr/git-repos/proj1.git
    $ cd proj1
    $ git log --pretty=format:"%an %ad %s" -10
    



=====================
local machine commands could be automated with following bash script

    
    
    #!/bin/bash
    
    REMOTE_GIT=user@server:/home/witr/git-repos/$1.git
    
    echo "start extract $REMOTE_GIT"
    cd witr
    
    echo "create and filter branch-$1"
    git branch branch-$1
    git filter-branch -f --subdirectory-filter $1 branch-$1
    
    echo "create new local git repo branch-$1"
    cd ..
    mkdir branch-$1
    cd branch-$1
    git init
    git pull ../witr branch-$1
    
    echo "push to remote git $REMOTE_GIT"
    git remote add $1 $REMOTE_GIT
    git push $1 master
    
    echo "done"
    
    




