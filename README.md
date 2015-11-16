# Linux Server Configuration

## IP Address:
- 54.186.93.235

## SSH Port:
- 2200

## Application url:
- http://ec2-54-186-93-235.us-west-2.compute.amazonaws.com/
- http://54.186.93.235/

-![](https://bytebucket.org/sus14/linux-server-configuration-bitbucket/raw/854c3a95aaf1416a948db948929d68c2661eb917/project5_submission.png?token=df1699eaa0601b757e26240bb2d1ef0acc10c3e6)

## Software installed:
- apache2
- python-setuptools
- libapache2-mod-wsgi
- mod-wsgi
- postgresql
- postgresql-contrib
- git
- flask
- python-pip
- python-dev
- python-virtualenv
- httplib2
- oauth2client
- sqlalchemy
- psycopg

## Configuration changes summary:
- Created `grader` linux user
- To login as `grader`, copied the key to the grader `~/.ssh` directory and changed the file permissions, owner, and group
- Gave grader and catalog users sudo access by creating `/etc/sudoers.d/grader` and changed permissions
- Configured timezone to UTC using `sudo dpkg-reconfigure tzdata`
- Changed port from 22 to 2200 in the `sshd_config` file
- Configured UFW to allow ports 2200 (SSH), 80 (HTTP), 123 (NTP)
- Edited the hosts file `/etc/hosts` to stop getting the warning message `unable to resolve host`
- To stop getting the message `Could not reliably determine the server's fully qualified domain name`, updated `apache2.conf` global directive
- Created `catalog` linux user and made updates to be able to login as catalog user and gave sudo access
- Created psql user `catalog` with password and gave user right to create database tables
- Created database `catalog`with owner `catalog` and revoked all rights on schema from public and granted access to only the `catalog` user
- Installed git and setup my name and email for commits
- Installed flask and configured virtual environment
- Created `catalog.conf`file
- Created `catalog.wsgi` file
- After copying project 3, made `.git` directory inaccessible
- Updated database_setup.py and application.py to point to postgresql database rather than sqllite
- Updated `catalog.conf` to have `ServerAlias` of ec2 url
- Disabled old conf files using `sudo a2dissite oldConfFile` and enabled new conf file using `sudo a2ensite newConfFile`
- Modified hosts file to include ec2 url
- Modified location of `client_secrets.json` to use absolute path
- Went to developers console and added host name and IP address to authorized JavaScript origins
- Also updated authorized redirect URIs and added in http://ec2-54-186-93-235.us-west-2.compute.amazonaws.com/oauth2callback
- Locked out root user by editing `sshd_config` to not permit root login
- Configured to only allow ssh to grader and catalog linux users

## Resources used:

### Udacity's courses:
- Configuring Linux Web Servers
- Linux Command Line Basics

### Udacity's discussion forum
Lots of posts that I used as reference but the one I started off with: https://discussions.udacity.com/t/p5-how-i-got-through-it/15342/4

### Digital Ocean
- https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-12-04
- https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server
- https://www.digitalocean.com/community/tutorials/how-to-add-and-delete-users-on-an-ubuntu-14-04-vps
- https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
- https://www.digitalocean.com/community/tutorials/additional-recommended-steps-for-new-ubuntu-14-04-servers
- https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps

### Ask Ubuntu
- http://askubuntu.com/questions/480822/apache-apr-sockaddr-info-get-failed-error
- http://askubuntu.com/questions/30781/see-configured-rules-even-when-inactive

### Trackets Blog
- http://blog.trackets.com/2013/08/19/postgresql-basics-by-example.html

### UFW
- https://help.ubuntu.com/community/UFW#Allow_Access
- http://ubuntuforums.org/showthread.php?t=1893751

### NTP
- http://tecadmin.net/setup-time-synchronisation-ntp-server-on-ubuntu-linuxmint/#

### Apache
- https://httpd.apache.org/docs/2.2/programs/apachectl.html
- http://askubuntu.com/questions/329323/problem-with-restarting-apache2

### Cyberciti
- http://www.cyberciti.biz/faq/what-process-has-open-linux-port/
- http://www.cyberciti.biz/tips/openssh-deny-or-restrict-access-to-users-and-groups.html

### Postgresql
- https://wiki.postgresql.org/wiki/First_steps
- http://dba.stackexchange.com/questions/22362/how-do-i-list-all-columns-for-a-specified-table

### Timezone
- http://unix.stackexchange.com/questions/110522/timezone-setting-in-linux

### Stack Overflow
- http://stackoverflow.com/questions/12201928/python-open-method-ioerror-errno-2-no-such-file-or-directory

### Mediatemple
- https://mediatemple.net/community/products/dv/204643810/how-do-i-disable-ssh-login-for-the-root-user

### pip
- http://pip.readthedocs.org/en/stable/reference/pip_freeze/#examples
