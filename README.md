## Linux Server Configuration - FSND P5
http://ec2-52-34-216-40.us-west-2.compute.amazonaws.com/
### Poject Description:
Deploying web application in Amazon's Elastic Compute Cloud (EC2).

### About Application
- Apache2, WSGI, Python
- IP: 52.34.216.40    Port: 2200  (ssh -i ~/.ssh/udacity_key.rsa grader@52.34.216.40 -p 2200)

### Implementation Detail
1. create new user     
    (1) create new user `grader`:   

        adduser grader        
    (2) grant `grader` sudo privilege: 
        __add `grader   ALL=(ALL:ALL) ALL` in visudo__      
    (3) SSH connection with RSA key: __create `.ssh` directory and copy `authorized_keys` to `.ssh`__
2. update all installed packages:    

        sudo apt-get update     
        sudo apt-get upgrade        
3. configure local timezone to UTC:     

        sudo dpkg-reconfigure tzdata
4. change SSH port to 2200:     

        sudo nano /etc/ssh/sshd_config
5. configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123):   

        sudo ufw default deny incoming
        sudo ufw default allow outgoing
        sudo ufw allow 2200/tcp
        sudo ufw allow 80/tcp
        sudo ufw allow 123/tcp
        sudo ufw enable
6. install and configure Apache to serve a Python mod_wsgi application:

        sudo apt-get update
        sudo apt-get install python-pip apache2 libapache2-mod-wsgi python-dev
7. install and configure PostgreSQL:        
    (1) do not allow remote connection (default setting)        
    (2) create a new user `catalog`:        
    change to PostgreSQL super-user and start PostgreSQL console:

        sudo su - postgres
        psql
    create new user `catalog` and grant limited permition to application database:

        CREATE USER catalog WITH PASSWORD 'passwd';
        GRANT CONNECT ON DATABASE catalogdb TO catalog;
        GRANT SELECT, DELETE, INSERT, UPDATE ON TABLE catagory, catagory_item TO catalog;
8. install git

        sudo apt-get install git
9. deploy application to server:        
    (1) create application root directory in `/var/www/`        
    (2) clone code in root directory        
    (3) write wsgi file in root directory
    (4) add application configuration file in `/etc/apache2/sites-available`
    (5) enalbe site:

        sudo a2ensite CatalogApp
        sudo service apache2 reload

### Extra
1. block defualt user `root` SSH connection
    >ssh -i ~/.ssh/udacity_key.rsa root@52.34.216.40 -p 2200        
    >Permission denied (publickey).
2. protect SSH with fail2ban
3. restrict access to .git file    
    add `.htaccess` file to root directory      

        #.htaccess
        RedirectMatch 404 /\.git
4. server automatic update

        sudo apt-get install unattended-upgrades
        sudo dpkg-reconfigure --priority=low unattended-upgrades

### Creator
WEN GUO