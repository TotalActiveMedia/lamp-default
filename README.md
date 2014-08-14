lamp-default
============

A default LAMP stack built on Debian Wheezy (7) running Apache 2.4.

To get started run vagrant up. The provisioner will fail, because python is missing. Install python2.7 on the guest and symlink /usr/bin/python2.7 to /usr/bin/python. Then rerun vagrant provision. It will still fail because of missing dependencies. Clone https://github.com/TotalActiveMedia/apache into ansible/roles/apache and rerun vagrant provision. Apache 2.4 is now running on your Wheezy box.
