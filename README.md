debian_noip2.sh
===============
my v1.0

This script can be used by admins using debian 7.x wheezy and no-ip if you want noip2 to run automatically when the machine is booted.
Any other script even mentioned in the official README of noip-2.1.9-1 will fail and won't start the client.
For example:
http://www.noip.com/support/knowledgebase/installing-the-linux-dynamic-update-client/
"Read the README file in the no-ip-2.1.9 folder for instructions on how to make the client run at startup. This varies depending on what Linux distribution you are running."


You may have tried (please READ!): http://www.togaware.com/linux/survivor/No_IP_Manual.html

THEN RUN:

update-rc.d noip2 defaults

and then reboot

BUT you will get the message that NO: noip process runs after startup!!!!

noip2 -S


HERE'S THE FIX!
---------------
/etc/init.d/README

Things that have changed in debian 7: All init.d scripts are expected to have a LSB style header documenting
dependencies and default runlevel settings. The header look like this
(not all fields are required):

\### BEGIN INIT INFO

\# Provides:          skeleton

\# Required-Start:    $remote_fs $syslog

\# Required-Stop:     $remote_fs $syslog

\# Should-Start:      $portmap

\# Should-Stop:       $portmap

\# X-Start-Before:    nis

\# X-Stop-After:      nis

\# Default-Start:     2 3 4 5

\# Default-Stop:      0 1 6

\# X-Interactive:     true

\# Short-Description: Example initscript

\# Description:       This file should be used to construct scripts to be

\#                    placed in /etc/init.d.

\### END INIT INFO


Quick start
-----------
CLONE the repo, `https://github.com/jensensen/debian_7.x_wheezy_noip2_STARTUP_script.git`.

PLACE the script in /etc/rc2.d/

RUN update-rc.d noip2 defaults


Note that afterwards the runlevel ID is changed:

cd /etc/rc2.d/

ls -la

for example NOW IT IS:

lrwxrwxrwx   1 root root    15 Aug 22 23:54 S17noip2 -> ../init.d/noip2



cd /etc/rc0.d/

ls -la

now it's:

lrwxrwxrwx   1 root root    15 Aug 22 23:47 K01noip2 -> ../init.d/noip2


Keep in mind
------------
that I have NO experience with runlevels in debian. But THIS script works!


Bug tracker
-----------
Have a bug? Please create an issue here on GitHub.

<https://github.com/jensensen/debian_7.x_wheezy_noip2_STARTUP_script/issues>

Author
------
**jensensen**

Copyright and license
---------------------
Public domain.
This program is free software; you can redistribute it and/or modify it as long as others share alike.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

