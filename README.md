Udacity Server Configuration Project
====================================

- IP address: 52.36.233.228
- URL: http://ec2-52-36-233-228.us-west-2.compute.amazonaws.com
- SSH port: 2200

Software installed:
-----------------------

- via apt-get:
    - python-flask,
    - python-sqlalchemy
    - apache2
    - libapache2-mod-wsgi
    - python-pip
    - python-virtualenv
    - fail2ban 
    - git 
    - build-dep
    - python-psycopg2
    - postgresql
- via pip:
    - bleach
    - oauth2client
    - requests
    - httplib2
    - redis
    - passlib
    - itsdangerous
    - flask-httpauth
    - WTForms
    - python-psycopg2

Configuration changes
------------------------------

- Created new user: `grader`
- Granted sudo privileges to `grader`
- Configured ssh so that only grader can ssh in
    - `AllowUsers grader`
- Changed SSH port to 2200
- Set up ufw to only let through http, ssh and ntp requests
- Set up postgresql, with user called catalog, and database called catalog
    - Checked that this will not accept external connections
- Cloned Item Catalog app and set it up with apache and mod_wsgi
- Updated Google OAuth credentials so that log-in still works
- Configured `/etc/fail2ban/jail.local` to protect SSH from repeated failed logins
    - `destemail = grader@localhost` to configure email alerts
    - `action = %(action_mwl)s` to configure email alerts
    - changed from `port = ssh` to `port = 2200` in `[ssh]` jail section
    - restarted with `sudo service fail2ban restart`

Resource list
----------------------
- https://github.com/robertavram/Linux-Server-Configuration
- http://www.howtogeek.com/howto/linux/security-tip-disable-root-ssh-login-on-linux/
- http://flask.pocoo.org/docs/0.10/deploying/mod_wsgi/
- https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-django-with-postgres-nginx-and-gunicorn
- https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps
- https://www.digitalocean.com/community/tutorials/how-to-protect-ssh-with-fail2ban-on-ubuntu-14-04