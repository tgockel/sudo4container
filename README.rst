##############
sudo4container
##############

Ever typed ``sudo apt-get install vim`` in a Docker container and been annoyed
when the command wasn't found?
If so, this is the program for you!
Just drop ``bin/sudo`` into someplace in your ``$PATH`` and never be annoyed
with (that specific aspect of) Docker again!

Usage
=====

Use it just like normal ``sudo`` (if you're already running as root or did not
need root user access in the first place)::

    $> sudo vim README.rst

Install
-------

Installation is easy through ``wget``!
It usually looks something like this (example from Ubuntu 18.04)::

    root@d286e3710e1b:/# wget https://raw.githubusercontent.com/tgockel/sudo4container/master/bin/sudo -O /usr/local/bin/sudo
    bash: wget: command not found
    root@d286e3710e1b:/# sudo apt-get install wget
    bash: sudo: command not found
    root@d286e3710e1b:/# apt-get install wget
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    E: Unable to locate package wget
    root@d286e3710e1b:/# apt-get update      
    Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
    Get:2 http://archive.ubuntu.com/ubuntu bionic InRelease [242 kB]                     
    Get:3 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [304 kB]
    Get:4 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [424 kB]
    Get:5 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [4171 B]
    Get:6 http://security.ubuntu.com/ubuntu bionic-security/restricted amd64 Packages [5436 B]
    Get:7 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                               
    Get:8 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
    Get:9 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [11.3 MB]
    Get:10 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [13.5 kB]
    Get:11 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [186 kB]
    Get:12 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1344 kB]
    Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [10.8 kB]
    Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [7238 B]
    Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [776 kB]
    Get:16 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1190 kB]
    Get:17 http://archive.ubuntu.com/ubuntu bionic-backports/main amd64 Packages [942 B]
    Get:18 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [3652 B]
    Fetched 16.1 MB in 4s (3812 kB/s)                         
    Reading package lists... Done
    root@d286e3710e1b:/# apt-get install wget
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following additional packages will be installed:
    ca-certificates libpsl5 libssl1.1 openssl publicsuffix
    The following NEW packages will be installed:
    ca-certificates libpsl5 libssl1.1 openssl publicsuffix wget
    0 upgraded, 6 newly installed, 0 to remove and 16 not upgraded.
    Need to get 2269 kB of archives.
    After this operation, 6341 kB of additional disk space will be used.
    Do you want to continue? [Y/n] 
    Get:1 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 libssl1.1 amd64 1.1.0g-2ubuntu4.3 [1130 kB]
    Get:2 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 openssl amd64 1.1.0g-2ubuntu4.3 [532 kB]
    Get:3 http://archive.ubuntu.com/ubuntu bionic/main amd64 ca-certificates all 20180409 [151 kB]
    Get:4 http://archive.ubuntu.com/ubuntu bionic/main amd64 libpsl5 amd64 0.19.1-5build1 [41.8 kB]
    Get:5 http://archive.ubuntu.com/ubuntu bionic/main amd64 publicsuffix all 20180223.1310-1 [97.6 kB]
    Get:6 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 wget amd64 1.19.4-1ubuntu2.2 [316 kB]
    Fetched 2269 kB in 1s (1691 kB/s)
    debconf: delaying package configuration, since apt-utils is not installed
    Selecting previously unselected package libssl1.1:amd64.
    (Reading database ... 4039 files and directories currently installed.)
    Preparing to unpack .../0-libssl1.1_1.1.0g-2ubuntu4.3_amd64.deb ...
    Unpacking libssl1.1:amd64 (1.1.0g-2ubuntu4.3) ...
    Selecting previously unselected package openssl.
    Preparing to unpack .../1-openssl_1.1.0g-2ubuntu4.3_amd64.deb ...
    Unpacking openssl (1.1.0g-2ubuntu4.3) ...
    Selecting previously unselected package ca-certificates.
    Preparing to unpack .../2-ca-certificates_20180409_all.deb ...
    Unpacking ca-certificates (20180409) ...
    Selecting previously unselected package libpsl5:amd64.
    Preparing to unpack .../3-libpsl5_0.19.1-5build1_amd64.deb ...
    Unpacking libpsl5:amd64 (0.19.1-5build1) ...
    Selecting previously unselected package publicsuffix.
    Preparing to unpack .../4-publicsuffix_20180223.1310-1_all.deb ...
    Unpacking publicsuffix (20180223.1310-1) ...
    Selecting previously unselected package wget.
    Preparing to unpack .../5-wget_1.19.4-1ubuntu2.2_amd64.deb ...
    Unpacking wget (1.19.4-1ubuntu2.2) ...
    Setting up libpsl5:amd64 (0.19.1-5build1) ...
    Processing triggers for libc-bin (2.27-3ubuntu1) ...
    Setting up publicsuffix (20180223.1310-1) ...
    Setting up libssl1.1:amd64 (1.1.0g-2ubuntu4.3) ...
    debconf: unable to initialize frontend: Dialog
    debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
    debconf: falling back to frontend: Readline
    debconf: unable to initialize frontend: Readline
    debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
    debconf: falling back to frontend: Teletype
    Setting up openssl (1.1.0g-2ubuntu4.3) ...
    Setting up wget (1.19.4-1ubuntu2.2) ...
    Setting up ca-certificates (20180409) ...
    debconf: unable to initialize frontend: Dialog
    debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
    debconf: falling back to frontend: Readline
    debconf: unable to initialize frontend: Readline
    debconf: (Can't locate Term/ReadLine.pm in @INC (you may need to install the Term::ReadLine module) (@INC contains: /etc/perl /usr/local/lib/x86_64-linux-gnu/perl/5.26.1 /usr/local/share/perl/5.26.1 /usr/lib/x86_64-linux-gnu/perl5/5.26 /usr/share/perl5 /usr/lib/x86_64-linux-gnu/perl/5.26 /usr/share/perl/5.26 /usr/local/lib/site_perl /usr/lib/x86_64-linux-gnu/perl-base) at /usr/share/perl5/Debconf/FrontEnd/Readline.pm line 7.)
    debconf: falling back to frontend: Teletype
    Updating certificates in /etc/ssl/certs...
    133 added, 0 removed; done.
    Processing triggers for libc-bin (2.27-3ubuntu1) ...
    Processing triggers for ca-certificates (20180409) ...
    Updating certificates in /etc/ssl/certs...
    0 added, 0 removed; done.
    Running hooks in /etc/ca-certificates/update.d...
    done.
    root@d286e3710e1b:/# wget https://raw.githubusercontent.com/tgockel/sudo4container/master/bin/sudo -O /usr/local/bin/sudo
    root@d286e3710e1b:/# chmod +x /usr/local/bin/sudo

Unsupported Features
--------------------

The POSIX program ``sudo`` comes with a number of command-line flags that are
100% not supported by this alternative version of ``sudo``.
The script is just ``exec "$@"``, so really don't expect too much.
