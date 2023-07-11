## INTALLING OF MYSQL ##

MySQL is an open-source relational database management system (RDBMS) that is widely used for storing and managing data.
It provides a robust and scalable platform for creating and managing databases, making it a popular choice for web applications 
and other data-driven systems.

### Steps ###
To install MySQL server run the following commands in the terminal.

Update package lists: Run the following command to update the package lists on your system:
```
sudo apt update 
```
Install the MySQL server package:
```
sudo apt install mysql-server -y
```

After the installation is complete, you can start the MySQL service:
```
sudo systemctl start mysql
```

**Note** :By default, MySQL is not secured. You will be prompted to set a password for the MySQL root user.
Make sure to choose a strong password and remember it, as you will need it to access the MySQL server.

```
Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No:
Please set the password for root here.

New password:
```
You can run the following command to secure your MySQL installation.
This command will prompt you to set a new root password, remove anonymous users, disallow remote root login, 
and remove the test database. You can choose 'Y' for yes or 'N' for no, depending on your preferences.
```
sudo mysql_secure_installation
```
To verify that MySQL is running properly, you can check its status:

```
sudo systemctl status mysql
```
### If the service is active and running, you will see a "active (running)" message. ###

![msql](https://github.com/AustinOzor/DevOps-Project-2-LEMP-STACK/assets/99667583/cc365964-c7b1-4346-9ad8-1ba23d8edaa5)


Verify if you are login to MySQL
```
sudo mysql
```

### Remove inscure default setting from MySQL ###

It’s recommended that you run a security script that comes pre-installed with MySQL.
This script will remove some insecure default settings and lock down access to your database system. 
Before running the script you will set a password for the root user, using mysql_native_password as default
authentication method. We’re defining this user’s password as Admin122.

Try to log in to the MySQL shell as the root user:
```
sudo mysql -u root -p
```

Once you are logged in to the MySQL shell, execute the following command to set the password for the root user:
This command sets the password for the 'root' user to 'PassWord.1'. Make sure to replace 'Admin123' with your desired password.
The mysql_native_password authentication method is used here.

```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Admin123';
```

After running the command, exit the MySQL shell by typing:
```
exit
```


👉 👉 **Next**

