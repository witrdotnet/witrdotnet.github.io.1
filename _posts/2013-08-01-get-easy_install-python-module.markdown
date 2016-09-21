---
author: admin
comments: false
date: 2013-08-01 08:02:00+00:00
layout: post
link: https://witr.net/quotation/?p=23
slug: get-easy_install-python-module
title: get easy_install python module
wordpress_id: 23
categories:
- python
---

Install command without root privileges  


<blockquote>wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -O - | python </blockquote>

Output logs of install  


<blockquote>--2013-08-01 10:28:48--  https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py  
Résolution de bitbucket.org (bitbucket.org)... 131.103.20.168, 131.103.20.167  
Connexion vers bitbucket.org (bitbucket.org)|131.103.20.168|:443... connecté.  
requête HTTP transmise, en attente de la réponse... 200 OK  
Longueur: 8815 (8,6K) [text/plain]  
Sauvegarde en : «STDOUT»  
  
100%[==============================>] 8 815       --.-K/s   ds 0,001s   
  
2013-08-01 10:28:50 (10,3 MB/s) - envoi vers sortie standard [8815/8815]  
  
Downloading https://pypi.python.org/packages/source/s/setuptools/setuptools-0.9.8.tar.gz  
Extracting in /tmp/tmpj5lJs_  
Now working in /tmp/tmpj5lJs_/setuptools-0.9.8  
Installing Setuptools  
running install  
error: can't create or remove files in install directory  
  
The following error occurred while trying to add or remove files in the  
installation directory:  
  
    [Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/test-easy-install-4089.write-test'  
  
The installation directory you specified (via --install-dir, --prefix, or  
the distutils default setting) was:  
  
    /usr/local/lib/python2.7/dist-packages/  
  
Perhaps your account does not have write access to this directory?  If the  
installation directory is a system-owned directory, you may need to sign in  
as the administrator or "root" account.  If you do not have administrative  
access to this machine, you may wish to choose a different installation  
directory, preferably one that is listed in your PYTHONPATH environment  
variable.  
  
For information on other options, you may wish to consult the  
documentation at:  
  
  https://pythonhosted.org/setuptools/easy_install.html  
  
Please make the appropriate changes for your system and try again.  
  
Something went wrong during the installation.  
See the error message above.  
</blockquote>


  
  
Install command with root privileges  


<blockquote>sudo wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -O - | sudo python </blockquote>

Output logs of install  


<blockquote>--2013-08-01 10:36:50--  https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py  
Résolution de bitbucket.org (bitbucket.org)... 131.103.20.168, 131.103.20.167  
Connexion vers bitbucket.org (bitbucket.org)|131.103.20.168|:443... connecté.  
requête HTTP transmise, en attente de la réponse... 200 OK  
Longueur: 8815 (8,6K) [text/plain]  
Sauvegarde en : «STDOUT»  
  
100%[============================================================================================================================================================================================================================>] 8 815       --.-K/s   ds 0,001s   
  
2013-08-01 10:36:51 (8,82 MB/s) - envoi vers sortie standard [8815/8815]  
  
Extracting in /tmp/tmpID3jKx  
Now working in /tmp/tmpID3jKx/setuptools-0.9.8  
Installing Setuptools  
running install  
running bdist_egg  
running egg_info  
writing dependency_links to setuptools.egg-info/dependency_links.txt  
writing requirements to setuptools.egg-info/requires.txt  
writing setuptools.egg-info/PKG-INFO  
writing top-level names to setuptools.egg-info/top_level.txt  
writing entry points to setuptools.egg-info/entry_points.txt  
reading manifest file 'setuptools.egg-info/SOURCES.txt'  
reading manifest template 'MANIFEST.in'  
writing manifest file 'setuptools.egg-info/SOURCES.txt'  
installing library code to build/bdist.linux-i686/egg  
running install_lib  
running build_py  
creating build  
creating build/lib.linux-i686-2.7  
copying pkg_resources.py -> build/lib.linux-i686-2.7  
copying easy_install.py -> build/lib.linux-i686-2.7  
creating build/lib.linux-i686-2.7/setuptools  
copying setuptools/py27compat.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/script template.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/py24compat.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/script template (dev).py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/site-patch.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/__init__.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/ssl_support.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/archive_util.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/depends.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/package_index.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/sandbox.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/dist.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/extension.py -> build/lib.linux-i686-2.7/setuptools  
copying setuptools/compat.py -> build/lib.linux-i686-2.7/setuptools  
creating build/lib.linux-i686-2.7/_markerlib  
copying _markerlib/markers.py -> build/lib.linux-i686-2.7/_markerlib  
copying _markerlib/__init__.py -> build/lib.linux-i686-2.7/_markerlib  
creating build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/upload_docs.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/bdist_egg.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/sdist.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/upload.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/egg_info.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/install_scripts.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/rotate.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/easy_install.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/build_py.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/install_lib.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/bdist_rpm.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/saveopts.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/__init__.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/test.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/alias.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/install.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/build_ext.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/register.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/setopt.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/bdist_wininst.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/develop.py -> build/lib.linux-i686-2.7/setuptools/command  
copying setuptools/command/install_egg_info.py -> build/lib.linux-i686-2.7/setuptools/command  
creating build/lib.linux-i686-2.7/setuptools/_backport  
copying setuptools/_backport/__init__.py -> build/lib.linux-i686-2.7/setuptools/_backport  
creating build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_packageindex.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_build_ext.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_dist_info.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_develop.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_easy_install.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_markerlib.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/doctest.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_sandbox.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/__init__.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/py26compat.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_egg_info.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/server.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_upload_docs.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_test.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_resources.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_bdist_egg.py -> build/lib.linux-i686-2.7/setuptools/tests  
copying setuptools/tests/test_sdist.py -> build/lib.linux-i686-2.7/setuptools/tests  
creating build/lib.linux-i686-2.7/setuptools/_backport/hashlib  
copying setuptools/_backport/hashlib/_sha.py -> build/lib.linux-i686-2.7/setuptools/_backport/hashlib  
copying setuptools/_backport/hashlib/_sha512.py -> build/lib.linux-i686-2.7/setuptools/_backport/hashlib  
copying setuptools/_backport/hashlib/__init__.py -> build/lib.linux-i686-2.7/setuptools/_backport/hashlib  
copying setuptools/_backport/hashlib/_sha256.py -> build/lib.linux-i686-2.7/setuptools/_backport/hashlib  
creating build/bdist.linux-i686  
creating build/bdist.linux-i686/egg  
copying build/lib.linux-i686-2.7/easy_install.py -> build/bdist.linux-i686/egg  
creating build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/py27compat.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/script template.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/py24compat.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/script template (dev).py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/site-patch.py -> build/bdist.linux-i686/egg/setuptools  
creating build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/upload_docs.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/bdist_egg.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/sdist.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/upload.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/egg_info.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/install_scripts.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/rotate.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/easy_install.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/build_py.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/install_lib.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/bdist_rpm.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/saveopts.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/__init__.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/test.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/alias.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/install.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/build_ext.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/register.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/setopt.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/bdist_wininst.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/develop.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/command/install_egg_info.py -> build/bdist.linux-i686/egg/setuptools/command  
copying build/lib.linux-i686-2.7/setuptools/__init__.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/ssl_support.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/archive_util.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/depends.py -> build/bdist.linux-i686/egg/setuptools  
creating build/bdist.linux-i686/egg/setuptools/_backport  
creating build/bdist.linux-i686/egg/setuptools/_backport/hashlib  
copying build/lib.linux-i686-2.7/setuptools/_backport/hashlib/_sha.py -> build/bdist.linux-i686/egg/setuptools/_backport/hashlib  
copying build/lib.linux-i686-2.7/setuptools/_backport/hashlib/_sha512.py -> build/bdist.linux-i686/egg/setuptools/_backport/hashlib  
copying build/lib.linux-i686-2.7/setuptools/_backport/hashlib/__init__.py -> build/bdist.linux-i686/egg/setuptools/_backport/hashlib  
copying build/lib.linux-i686-2.7/setuptools/_backport/hashlib/_sha256.py -> build/bdist.linux-i686/egg/setuptools/_backport/hashlib  
copying build/lib.linux-i686-2.7/setuptools/_backport/__init__.py -> build/bdist.linux-i686/egg/setuptools/_backport  
copying build/lib.linux-i686-2.7/setuptools/package_index.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/sandbox.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/dist.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/extension.py -> build/bdist.linux-i686/egg/setuptools  
copying build/lib.linux-i686-2.7/setuptools/compat.py -> build/bdist.linux-i686/egg/setuptools  
creating build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_packageindex.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_build_ext.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_dist_info.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_develop.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_easy_install.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_markerlib.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/doctest.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_sandbox.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/__init__.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/py26compat.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_egg_info.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/server.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_upload_docs.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_test.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_resources.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_bdist_egg.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/setuptools/tests/test_sdist.py -> build/bdist.linux-i686/egg/setuptools/tests  
copying build/lib.linux-i686-2.7/pkg_resources.py -> build/bdist.linux-i686/egg  
creating build/bdist.linux-i686/egg/_markerlib  
copying build/lib.linux-i686-2.7/_markerlib/markers.py -> build/bdist.linux-i686/egg/_markerlib  
copying build/lib.linux-i686-2.7/_markerlib/__init__.py -> build/bdist.linux-i686/egg/_markerlib  
byte-compiling build/bdist.linux-i686/egg/easy_install.py to easy_install.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/py27compat.py to py27compat.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/script template.py to script template.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/py24compat.py to py24compat.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/script template (dev).py to script template (dev).pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/site-patch.py to site-patch.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/upload_docs.py to upload_docs.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/bdist_egg.py to bdist_egg.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/sdist.py to sdist.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/upload.py to upload.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/egg_info.py to egg_info.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install_scripts.py to install_scripts.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/rotate.py to rotate.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/easy_install.py to easy_install.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/build_py.py to build_py.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install_lib.py to install_lib.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/bdist_rpm.py to bdist_rpm.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/saveopts.py to saveopts.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/__init__.py to __init__.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/test.py to test.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/alias.py to alias.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install.py to install.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/build_ext.py to build_ext.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/register.py to register.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/setopt.py to setopt.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/bdist_wininst.py to bdist_wininst.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/develop.py to develop.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/command/install_egg_info.py to install_egg_info.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/__init__.py to __init__.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/ssl_support.py to ssl_support.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/archive_util.py to archive_util.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/depends.py to depends.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/_backport/hashlib/_sha.py to _sha.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/_backport/hashlib/_sha512.py to _sha512.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/_backport/hashlib/__init__.py to __init__.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/_backport/hashlib/_sha256.py to _sha256.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/_backport/__init__.py to __init__.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/package_index.py to package_index.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/sandbox.py to sandbox.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/dist.py to dist.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/extension.py to extension.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/compat.py to compat.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_packageindex.py to test_packageindex.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_build_ext.py to test_build_ext.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_dist_info.py to test_dist_info.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_develop.py to test_develop.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_easy_install.py to test_easy_install.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_markerlib.py to test_markerlib.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/doctest.py to doctest.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_sandbox.py to test_sandbox.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/__init__.py to __init__.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/py26compat.py to py26compat.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_egg_info.py to test_egg_info.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/server.py to server.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_upload_docs.py to test_upload_docs.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_test.py to test_test.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_resources.py to test_resources.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_bdist_egg.py to test_bdist_egg.pyc  
byte-compiling build/bdist.linux-i686/egg/setuptools/tests/test_sdist.py to test_sdist.pyc  
byte-compiling build/bdist.linux-i686/egg/pkg_resources.py to pkg_resources.pyc  
byte-compiling build/bdist.linux-i686/egg/_markerlib/markers.py to markers.pyc  
byte-compiling build/bdist.linux-i686/egg/_markerlib/__init__.py to __init__.pyc  
creating build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/PKG-INFO -> build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/SOURCES.txt -> build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/dependency_links.txt -> build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/entry_points.txt -> build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/entry_points.txt.orig -> build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/requires.txt -> build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/top_level.txt -> build/bdist.linux-i686/egg/EGG-INFO  
copying setuptools.egg-info/zip-safe -> build/bdist.linux-i686/egg/EGG-INFO  
creating dist  
creating 'dist/setuptools-0.9.8-py2.7.egg' and adding 'build/bdist.linux-i686/egg' to it  
removing 'build/bdist.linux-i686/egg' (and everything under it)  
Processing setuptools-0.9.8-py2.7.egg  
Copying setuptools-0.9.8-py2.7.egg to /usr/local/lib/python2.7/dist-packages  
Adding setuptools 0.9.8 to easy-install.pth file  
Installing easy_install script to /usr/local/bin  
Installing easy_install-2.7 script to /usr/local/bin  
  
Installed /usr/local/lib/python2.7/dist-packages/setuptools-0.9.8-py2.7.egg  
Processing dependencies for setuptools==0.9.8  
Finished processing dependencies for setuptools==0.9.8 </blockquote>


  
Now you can use **easy_install** command line  
  
Source : [https://pypi.python.org/pypi/setuptools/0.9.8#installation-instructions](https://pypi.python.org/pypi/setuptools/0.9.8#installation-instructions)

