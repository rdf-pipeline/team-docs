# Setting Pipeline Permissions

# Add your user to www-data group
usermod -a -G www-data <your user>

# set the guid permissions
cd /var
sudo chmod -R 4775 www 

# clean up for a fresh directory
rm -rf /var/www/* 

# set the umask for apache 
sudo vi /etc/init.d/apache2
Add this line: 
umask 002
save it
sudo service apache restart

#set the default umask for users
sudo vi /etc/login.defs
search for UMASK
change UMASK from 022 to 002
save it

Note: If you prefer, you could control the umask from your .profile or .bashrc file

Logout and log back in so tht your umask changes take effect.

