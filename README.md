CherryMusic Init Script (Debian)
==================

This script is to be used with the manual install of CherryMusic.

Copy the script to you init directory and name it cherrymusic:

    wget --no-check-certificate https://github.com/Lord-Simon/Scripts/raw/master/cherrymusic/cherrymusic -O /etc/init.d/cherrymusic


After that you might want to grant the executive permission to the file:

    chmod +x /etc/init.d/cherrymusic

Once you've done that, edit the script.

Add the path of your cherrymusic folder to DIR. If the path is wrong and the executable 'cherrymusic' can't be found, the script will automatically exit every time you try to run it.

Add the python executable path to the PYTHON. And set the USER and GROUP under which the service will run.

IF your libraries or DB are on remote filesystems, you might want to add '$remote_fs' to 'Required-Start:' and 'Required-Stop:'.

-----------------

Test the the init script by running:

    service cherrymusic start

When everything went correctly, run:

    update-rc.d /etc/init.d/cherrymusic defaults

This uses the Debian-specific command to add the init script at the right place, automatically.

To remove the script, use:

    update-rc.d -f /etc/init.d/cherrymusic remove

-----------------

The Update function will search for a '.git' directory under cherrymusic, if it's found it will execute a git pull.

IF git executable or the '.git' directory are not available, the script will try to use 'wget' or 'curl' to fetch the up to date tarball of cherrymusic and replace the contents of the cherrymusic folder.
