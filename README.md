## Access

IP: 35.159.37.46  PORT: 2200

URL: http://ec2-35-159-37-46.eu-central-1.compute.amazonaws.com/


## Installed software

* Apache
* wsgi module for Apache
* Postgres
* python-pip
* Python libraries
  * sqlalchemy
  * flask
  * psycopg2
  * httplib2
  * requests
  * oauth2client


## Configurations

* created user 'grader'
  * added public key to /home/grader/.ssh/authorized_keys
  * added sudo permissions to /etc/sudoers.d/grader
* edited ssh config /etc/ssh/sshd_config
  * Port 2200
  * PermitRootLogin no
  * PasswordAuthentication no
* edited Apache config /etc/apache2/sites-enabled/000-default.conf
  * WSGIScriptAlias / /home/grader/nd-fs-item-catalog/catalog.wsgi
  * WSGIPythonPath /home/grader/nd-fs-item-catalog
* created postgres user 'catalog' with rights to the 'itemcatalog' database
* adapted the catalog app to execution as wsgi
  * introduced a catalog.wsgi wrapper
  * modified the catalog app to use postgres instead of sqlite
  * modified the path for reading the secret file


## Additional Reading

While dealing with the varius issues I encountered, I found the following to be useful:
* https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps
* http://docs.sqlalchemy.org/en/latest/core/engines.html
* http://flask.pocoo.org/docs/1.0/deploying/mod_wsgi/
