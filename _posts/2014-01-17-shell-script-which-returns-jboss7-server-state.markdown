---
author: admin
comments: false
date: 2014-01-17 19:43:51+00:00
layout: post
link: https://witr.net/quotation/?p=697
slug: shell-script-which-returns-jboss7-server-state
title: get jboss7 server state with shell script
wordpress_id: 697
categories:
- jboss
- shell
---


Shell script (status.sh) bellow returns three jboss server state :



   
  * STOPPED : jboss is stopped (script could not connect with jboss-cli)

   
  * STARTING : jboss is starting (its state is running but project is not deployed)

   
  * RUNNING : jboss is ready (its state is running and project is deployed successfully)


Use :


<blockquote>
 > ./status.sh /path/to/jbossHome
</blockquote>



This script may be improved ...
Also you need to replace in code myArtifactName fake value by your right value

    
    
    #!/bin/bash
    
    res=$($1/bin/jboss-cli.sh --commands="connect,read-attribute server-state" 2>&1)
    
    if [[ $res != 'running' ]]
    then
            echo "STOPPED ($res)"
    else
            artifactDeployed=$($1/bin/jboss-cli.sh --commands="connect,deploy -l" | grep myArtifactName | grep OK  2>&1)
            if [[ X$artifactDeployed == 'X' ]]
            then
                    echo "STARTING ($res / $artifactDeployed)"
            else
                    echo "RUNNING ($res / $artifactDeployed)"
            fi
    fi
    



