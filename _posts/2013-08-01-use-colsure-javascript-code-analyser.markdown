---
author: admin
comments: false
date: 2013-08-01 08:04:00+00:00
layout: post
link: https://witr.net/quotation/?p=22
slug: use-colsure-javascript-code-analyser
title: Use colsure (javascript code analyser)
wordpress_id: 22
categories:
- javascript
---



First of all you must have easy_install python module : cf. [get-easyinstall-python-module](http://quote.witr.net/?p=23)

Install closure linter :

    
    cd /tmp
    sudo easy_install http://closure-linter.googlecode.com/files/closure_linter-latest.tar.gz




<blockquote>Downloading http://closure-linter.googlecode.com/files/closure_linter-latest.tar.gz
Processing closure_linter-latest.tar.gz
Writing /tmp/easy_install-Xt6LOk/closure_linter-2.3.11/setup.cfg
Running closure_linter-2.3.11/setup.py -q bdist_egg --dist-dir /tmp/easy_install-Xt6LOk/closure_linter-2.3.11/egg-dist-tmp-w7sS6l
zip_safe flag not set; analyzing archive contents...
Adding closure-linter 2.3.11 to easy-install.pth file
Installing fixjsstyle script to /usr/local/bin
Installing gjslint script to /usr/local/bin

Installed /usr/local/lib/python2.7/dist-packages/closure_linter-2.3.11-py2.7.egg
Processing dependencies for closure-linter==2.3.11
Searching for python-gflags
Reading https://pypi.python.org/simple/python-gflags/
Reading http://code.google.com/p/python-gflags
Best match: python-gflags 2.0
Downloading https://pypi.python.org/packages/source/p/python-gflags/python-gflags-2.0.tar.gz#md5=23c9a793959a54971b1f094b0c6d03b1
Processing python-gflags-2.0.tar.gz
Writing /tmp/easy_install-SlgYwJ/python-gflags-2.0/setup.cfg
Running python-gflags-2.0/setup.py -q bdist_egg --dist-dir /tmp/easy_install-SlgYwJ/python-gflags-2.0/egg-dist-tmp-kTyloa
zip_safe flag not set; analyzing archive contents...
Adding python-gflags 2.0 to easy-install.pth file

Installed /usr/local/lib/python2.7/dist-packages/python_gflags-2.0-py2.7.egg
Finished processing dependencies for closure-linter==2.3.11
</blockquote>


Once finished you can use closure linter as following :

Analyse one js script file :

    
    gjslint path/to/my/file.js


Analyse entire directory :

    
    gjslint -r path/to/my/directory


more details here : [https://developers.google.com/closure/utilities/docs/linter_howto](https://developers.google.com/closure/utilities/docs/linter_howto)


