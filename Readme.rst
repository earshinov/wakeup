License
~~~~~~~

Public domain. I wish you do anything you want with this script.

Requirements
~~~~~~~~~~~~

* ALSA sound system installed and configured;
* alsa-utils;
* mpg123;
* zenity (further referred to as the dialog program).

Some of the requirements may be reviewed in the future (see TODO).

Behaviour
~~~~~~~~~

Script plays music smoothly increasing volume and shows passphrase entry dialog.
It won't stop the music until you enter the correct passphrase.

Currently it only supports MP3 (see also TODO).

Typical Usage
~~~~~~~~~~~~~

1. Put the script anywhere in your filesystem.
2. Modify the script adjusting variables to fit your needs.
3. Modify your favourite task scheduler's config to run the script (example for cron follows).

How to run this script using cron
---------------------------------

Run ``crontab -e`` which will open your favourite text editor with a cron jobs file in it.
Edit and save the file considering the example below.

::

  # m h  dom mon dow   command

  DISPLAY=:0
  LC_ALL=ru_RU.UTF8

  00 06 * * * /path/to/wakeup

This will run the script at 6:00 am everyday.
Replace ``/path/to/wakeup`` with the path where you put the script (it can be relative to your home directory).

``DISPLAY`` setting is there to inform the dialog program on which X display it should show.
In most cases you will be satisfied with ``:0`` value.

``LC_ALL`` settings indicates your locale.
You should specify it if you have non-latin text within the script.
To get your locale, try running ``locale`` in terminal and look for ``LANG`` value.

You may need to modify X server's access control list to allow
a program being run as a cron job to access the X server.
Try running ``xhost local:<username>`` as explained by Marianne Promberger
`in her blog <http://promberger.info/linux/2009/01/02/running-x-apps-like-zenity-from-crontab-solving-cannot-open-display-problem/>`_.

TODO
~~~~

* test in BSD environment;
* support any of kdialog, xdialog, zenity instead of requiring zenity;
* support more music formats;
* support more sound systems instead of requiring ALSA.

Any other suggestions? Maybe you know any programs to replace mpg123?
