# Linux-Server-Project


# The IP address and SSH port

```
35.162.71.70 -p 2200
```

# The complete URL to your hosted web application.
```
http://ec2-35-162-71-70.us-west-2.compute.amazonaws.com/
```


# A summary of software you installed
```
postgresql

libapache2-mod-wsgi

apache2

psycopg2

Flask

oauth2client

sqlalchemy
```

# A summary of configuration changes made.

1. Moved the app code to www/var/ directory

2. Configured the virtual host and make the domain name as ServerName.
Details in __/etc/apache2/sites-available/FlaskApp.conf__

3. Giving new user 'catalog' access rights:
Added catalog in

__/etc/postgresql/9.3/main/pg_hba.conf__

```
local   all        catalog       peer
```

4. Changed SSH port:
__/etc/ssh/sshd_config__
```
Port 22
```

5. Disable remote root SSH Login:
__/etc/ssh/sshd_config__  
```
PermitRootLogin no
```

6. Enable grader to sudo in
__/etc/sudoers__

```
grader    ALL=(ALL:ALL) ALL
```

7. Configure postgresql,
  1. create role catalog and db catalog_application
  2. Specify in the catalog app to use
  ```
  SQLALCHEMY_DATABASE_URI = 'postgresql+psycopg2://catalog:123@localhost/catalog_application'
  ```
  3. GRANT ALL PRIVILEGES to 3 tables.
     GRANT USAGE, SELECT ON SEQUENCE to 3 sequences.

8. In google credentials for sign in, give the domain name
to Authorized JavaScript origins and Authorized redirect URIs

9. For ufw use command line to specify port and protocol and enable ufw.

10. To update packages
    ```
    sudo apt-get update
    sudo apt-get upgrade
    ```
11. Give public key to github to be able to git clone the catalog project

12. Give write access to static file for image upload.

13. Put public key to .ssh/authorized_keys for RSA authentication

# A list of any third-party resources you made use of to complete this project.

https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

Mostly resources here:

https://discussions.udacity.com/t/markedly-underwhelming-and-potentially-wrong-resource-list-for-p5/8587
