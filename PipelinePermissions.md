# Setting Pipeline Permissions

1. Add your user to www-data group
```
usermod -a -G www-data <your user>
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

5. set the default umask for users
```
sudo vi /etc/login.defs
search for UMASK
change UMASK from 022 to 002
save it
Logout and login so that your umask changes take effect.
```

    Note: You could simply set the umask in your .profile or .bashrc if you wish to restrict this to one user.

