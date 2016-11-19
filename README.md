# Linux-Server-Project


# The IP address and SSH port

    ```
    35.162.71.70 -p 2200
    ```

# The complete URL to hosted web application.
    ```
    http://ec2-35-162-71-70.us-west-2.compute.amazonaws.com/
    ```


# A summary of software installed

*  postgresql

*  libapache2-mod-wsgi

*  apache2

*  psycopg2

*  Flask

*  oauth2client

*  sqlalchemy


# A summary of configuration changes made.

- Moved the app code to /var/www directory

- Configured the virtual host and make the domain name as ServerName.
  Details in __/etc/apache2/sites-available/FlaskApp.conf__

- Giving new user 'catalog' access rights:
  Added catalog in __/etc/postgresql/9.3/main/pg_hba.conf__
    ```
    local   all        catalog       peer
    ```

- Changed SSH port:
__/etc/ssh/sshd_config__
    ```
    Port 22
    ```

-  Disable remote root SSH Login:
__/etc/ssh/sshd_config__  
    ```
    PermitRootLogin no
    ```

- Enable grader to sudo in
__/etc/sudoers__

    ```
    grader    ALL=(ALL:ALL) ALL
    ```

- Configure postgresql,
  1. create role catalog and db catalog_application
  2. Specify in the catalog app to use
      ```
      postgresql+psycopg2://catalog:123@localhost/catalog_application
      ```
  3. GRANT ALL PRIVILEGES to 3 tables.
     GRANT USAGE, SELECT ON SEQUENCE to 3 sequences.

- In google credentials for sign in, give the domain name
to Authorized JavaScript origins and Authorized redirect URIs

- For ufw use command line to specify port and protocol and enable ufw.

-  To update packages
    ```
    sudo apt-get update
    sudo apt-get upgrade
    ```
- Give public key to github to be able to git clone the catalog project

- Give write access to static file for image upload.

- Put public key to .ssh/authorized_keys for RSA authentication

# A list of any third-party resources you made use of to complete this project.

https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

Mostly resources compilation here from Udacity forum:

https://discussions.udacity.com/t/markedly-underwhelming-and-potentially-wrong-resource-list-for-p5/8587
