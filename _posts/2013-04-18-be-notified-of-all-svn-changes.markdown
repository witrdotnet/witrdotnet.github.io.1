---
author: admin
comments: false
date: 2013-04-18 07:44:00+00:00
layout: post
link: https://witr.net/quotation/?p=68
slug: be-notified-of-all-svn-changes
title: be notified of all svn changes
wordpress_id: 68
categories:
- jabber
- linux
- network
- svn
---

If you want like me have been notified of all svn changes, the following script I wrote for you.  
  
Prerequisite :  




  * svn installed


  * svn well configured for user executing script




<blockquote>#!/bin/bash  
  
export SVN_UPDATES_HOME=/mnt/scripts/svnUpdates  
export SVN_UPDATES_LAST=$SVN_UPDATES_HOME/tmp/svnUpdatesLast.txt  
export SVN_UPDATES_TMP=$SVN_UPDATES_HOME/tmp/svnUpdates.txt  
export SVN_UPDATES_DIFF_TMP=$SVN_UPDATES_HOME/tmp/svnUpdatesDiff.txt  
export SVN_UPDATES_DIFF_LOG=$SVN_UPDATES_HOME/log/svnUpdatesLog  
  
if [[ -s $SVN_UPDATES_LAST ]]  
then  
  echo "copy last svn log to tmp"  
  cp $SVN_UPDATES_LAST $SVN_UPDATES_TMP  
else  
  touch $SVN_UPDATES_TMP  
fi  
  
for log in 1 2 3  
do  
  echo "svn log - try:$log"  
  svn log -v -l5 -rHEAD:1 https://svn.witr.net > $SVN_UPDATES_LAST  
  if [[ -s $SVN_UPDATES_LAST ]]  
  then  
    echo "svn logged successfully in try:$log"  
    break  
  fi  
done  
  
if [[ -s $SVN_UPDATES_LAST ]]  
then  
  echo "proceed to diff last with tmp"  
  diff $SVN_UPDATES_LAST $SVN_UPDATES_TMP | grep -E "^<" | sed s/^.// > $SVN_UPDATES_DIFF_TMP  
  diffsCount=$(wc -l $SVN_UPDATES_DIFF_TMP | awk {'print $1'})  
  if [ $diffsCount -gt 0 ]  
  then  
      "diffs found: send notification"  
      datetime=$(date "+%Y%m%d-%H%M%S")  
      logFile=$SVN_UPDATES_DIFF_LOG$datetime  
      cp $SVN_UPDATES_DIFF_TMP $logFile  
      ### put here the way you want be notified (mail, jabber, ...)  
      ### echo "==== svn updated cf. $logFile ====" | sendxmpp mabrouk@openfire.witr.net  
      ### cat $logFile | sendxmpp mabrouk@openfire.witr.net  
  fi  
fi  
</blockquote>

Here I choose to be notified by message sent from jabber server from my account to my account.  
Prerequisite : sendxmpp installed : apt-get install sendxmpp  


<blockquote>echo "==== svn updated cf. $logFile ====" | sendxmpp mabrouk@openfire.witr.net  
cat $logFile | sendxmpp mabrouk@openfire.witr.net  
</blockquote>

Finally, schedule the script in your crontab (executed each minute recommanded)  


<blockquote>* * * * * /mnt/scripts/svnUpdates/svnUpdates.sh </blockquote>



