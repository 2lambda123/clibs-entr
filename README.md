**WARNING:** This is a (possibly outdated and/or unmaintained) fork of https://bitbucket.org/eradman/entr. If you want to install entr, go to the [the original repository](https://bitbucket.org/eradman/entr) to get the latest release. Likewise, to file an issue or a pull request, head over to the [the original repository](https://bitbucket.org/eradman/entr).

Event Notify Test Runner
========================

A utility for running arbitrary commands when files change. Uses kqueue(2) or
inotify(7) to avoid polling.  `entr` was written to facilitate rapid feedback
on the command line.

Source Installation - BSD, Mac OS, and Linux
--------------------------------------------

    ./configure
    make test
    make install

To see available build options run `./configure -h`

Docker and WSL
--------------

Incomplete inotify support on _Windows Subsystem for Linux_ and _Docker for Mac_
may cause `entr` to respond incorrectly. Setting the environment variable
`ENTR_INOTIFY_WORKAROUND` enables `entr` to operate in these environments.

Linux Features
--------------

Symlinks can be monitored for changes by setting the environment variable
`ENTR_INOTIFY_SYMLINK`.

Man Page Examples
-----------------

Rebuild a project if source files change, limiting output to the first 20 lines:

    $ find src/ | entr -s 'make | head -n 20'

Launch and auto-reload a node.js server:

    $ ls *.js | entr -r node app.js

Clear the screen and run a query after the SQL script is updated:

    $ echo my.sql | entr -cp psql -f /_

Rebuild project if a source file is modified or added to the src/ directory:

    $ while sleep 0.1; do ls src/*.rb | entr -d make; done

Auto-reload a web server, or terminate if the server exits

    $ ls * | entr -rz ./httpd

News
----

A release history as well as features in the upcoming release are covered in the
[NEWS](NEWS) file.
