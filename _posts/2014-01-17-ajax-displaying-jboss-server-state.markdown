---
author: admin
comments: false
date: 2014-01-17 20:08:52+00:00
layout: post
link: https://witr.net/quotation/?p=698
slug: ajax-displaying-jboss-server-state
title: ajax displaying jboss server state
wordpress_id: 698
categories:
- ajax
- javascript
- jboss
- php
---


We aim to have web page which displays continually three jboss7 servers states.
For this we need the shell script (status.sh) to be found [here](http://quote.witr.net/?p=378).


### environment requirement




servers in same machine :
  * apache server


  * three jboss7 servers: jboss1, jboss2, jboss3




### get result of status.sh in our php file


Following php code displays one jboss server state

    
    
    echo exec('/path/to/script/status.sh /path/to/jboss/home')
    


For our example we need three php files containing the previous one line php code corresponding to each one of the three jboss server : state-jboss1.php, state-jboss2.php, and state-jboss3.php


### ajax state display


We need here the load() method of jquery javascript framework.

    
    
      <span id="jboss"></span><br></br>
    
      <script language="javascript">
          $('#jboss').load('state-jboss.php');
      </script>
    




### continuous update of servers state


We'll resort to javascript timer

    
    
    setInterval(function(){$('#jboss').load('state-jboss.php')},3000);
    




### deloyment




root folder :
  * create folder jboss-state in apache server root www

files :
  * www/jboss-state/status.sh


  * www/jboss-state/index.html


  * www/jboss-state/state-jboss1.php


  * www/jboss-state/state-jboss2.php


  * www/jboss-state/state-jboss3.php




### full code


status.sh (myArtifactName string in code must be replaced by the right artifact name)

    
    
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
    


state-jboss1.php

    
    
    
    


state-jboss2.php

    
    
    
    


state-jboss3.php

    
    
    
    


index.html

    
    
    <html>
      <body>
        Jboss1 state : <span id="jboss1"></span><br></br>
        Jboss2 state : <span id="jboss2"></span><br></br>
        Jboss3 state : <span id="jboss3"></span><br></br>
    
        <script language="javascript">
            setInterval(function(){$('#jboss1').load('state-jboss1.php')},3000);
            setInterval(function(){$('#jboss2').load('state-jboss2.php')},3000);
            setInterval(function(){$('#jboss3').load('state-jboss3.php')},3000);
        </script>
      </body>
    </html>
    




