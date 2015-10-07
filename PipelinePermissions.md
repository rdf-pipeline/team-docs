# Setting Pipeline Permissions

This document describe how the RDF pipeline Linux host should be configured
to allow any user to run tests without file permission errors.

1. Add your user to www-data group
    ```
    sudo usermod -a -G www-data <your user>
    ```

2. set the guid permissions for /var/www
    ```
    cd /var
    sudo chmod -R 4775 www 
    ```
    
3. clean up for a fresh directory
    ```
    rm -rf /var/www/* 
    ```
    
4. set the umask for apache 
    ```
    sudo vi /etc/init.d/apache2
    Add this line: 
    umask 002
    save it
    sudo service apache restart
    ```

