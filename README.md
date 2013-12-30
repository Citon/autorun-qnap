AutoRun-QNAP Readme
============================================================================

QNap uses a RAMDISK for /, which means you lose /root and /etc changes on
reboot. 

See http://wiki.qnap.com/wiki/Autorun.sh for more information.

All files ending in .auto under this folder will be called by the autorun.sh
added to this QNap's config partition.

To setup, extract this package into a folder under a shared drive location.
On most QNAPs this is under /share/MD0_DATA/SHARENAME.

Then copy autorun.sh.temp to a new file named "autorun.sh":

	cp autorun.sh.temp autorun.sh
	chmod 755 autorun.sh

Edit the new autorun.sh file and change the AUTOBASE variable to
match your environment.  AUTOBASE must be set to the location you have
installed autorun-qnap into.  For example, if you installed into a share
named "backup" in a subfolder named "autorun-qnap", the proper AUTOBASE would
be /share/MD0_DATA/backup/autorun-qnap

Once you have set AUTOHOME in autorun.sh,  use the following commands to copy
autorun.sh into the configuration partition. (For TS509 and other newer Intel
models.)  Run this from the current folder:

	./install.sh

Then, create one or more .auto files in this folder.  These are bourne shell
files, and should look like this:

	#!/bin/sh
	
	# DESCRIPTION OF THE FILE
	
	somecommand
	someothercommand

Each .auto file will be run on bootup.  Reboot and test.

