### CONFIGURE NGINX TO USE PHP PROCESSOR ###
When using the Nginx web server, we can create server blocks (similar to virtual hosts in Apache)
to encapsulate configuration details and host more than one domain on a single server. 
In this guide, we’ll use your_domain as an example domain name.
___________________________________________________________________________________________________________________________________________________________
On Ubuntu 22.04, Nginx has one server block enabled by default and is configured to serve documents out of a directory 
at /var/www/html. While this works well for a single site, it can become difficult to manage if you are hosting multiple sites. 
Instead of modifying /var/www/html, we’ll create a directory structure within /var/www for the your_domain website, 
leaving /var/www/html in place as the default directory to be served if a client request doesn’t match any other sites.

Let follow the steps below to complete this part of the project.

1. Create the root web directory for your_domain as follows:
   ```
   sudo mkdir /var/www/html/project2
   ```
2. Assign ownership of the directory with the $USER environment variable, which will reference your current system user:
```
sudo chown -R $USER:$USER /var/www/project2
```
3. Open a new configuration file in Nginx’s sites-available directory using your preferred command-line editor. Let use vim:
 Create a new server block configuration file.
```
sudo vim /etc/nginx/sites-available/project2
```
4. We need to make few changes with our project details. 
```
server {
    listen 80;
    server_name project2 www.project2;
    root /var/www/project2;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```
#### To save the script and exit from the vim editor, press `ecs` then `:wq!`
Let try and understand what the script above.
The server block configuration you provided is an example of hosting a project (project2) with Nginx.

- `listen 80;`: Specifies that this server block should listen on port 80 for incoming HTTP requests.
- `server_name project2 www.project2;`: Defines the server names associated with this block. Requests for "project2"
   and "www.project2" will be handled by this server block.
- `root /var/www/project2;`: Sets the root directory where the web files for "project2" are located.
   Nginx will serve files from this directory for requests to this server block.
- `index index.html index.htm index.php;`: Specifies the order of index files to look for when accessing a directory.
    In this case, Nginx will try to serve "index.html", "index.htm", and "index.php" in that order if available.
- `location / { ... }`: This location block defines the behavior for requests to the root URL ("/"). The `try_files`
   directive attempts to serve the requested file or directory, and if it doesn't exist, it returns a 404 error.
- `location ~ \.php$ { ... }`: This location block handles requests for PHP files. It includes the `snippets/fastcgi-php.conf` file,
    which contains the necessary FastCGI PHP configuration. The `fastcgi_pass` directive specifies the socket path for PHP-FPM
    (in this case, `/var/run/php/php8.1-fpm.sock`).
- `location ~ /\.ht { ... }`: This location block handles requests for hidden files or directories (starting with a dot). In this case,
    it denies access to these files, providing some additional security by denying access to important configuration files.


5. We have to create a symbolic link to enable the server block"
```
sudo ln -s /etc/nginx/sites-available/project2/etc/nginx/sites-enabled/
```
6. Verify the Nginx configuration for any syntax errors:
```
sudo nginx -t
```
You will get a message a show below if everything is ok.
![test nginx](https://github.com/AustinOzor/DevOps-Project-2-LEMP-STACK/assets/99667583/f789554c-811a-4f5c-8f6d-b09dac11561a)

7. Let remove the symbolic link to the default configuration file in the sites-enabled directory of Nginx.
```
sudo unlink /etc/nginx/sites-enabled/default
```
8. Restart Nginx to apply the changes.
```
sudo systemctl restart nginx
```

### Create a simple html script for the new site
The new site you enabled at /var/www/html/project2 is empty. To create a simple HTML website to serve through Nginx, let us follow these steps:

1. Navigate to the web root directory where Nginx serves files. The default location is usually `/var/www/html/project2` on Ubuntu.

   ```
   cd /var/www/html/project2/
   ```

2. Create a new HTML file for your website. You can use a text editor such as vim to create and edit the file.
   Let's create a file named `index.html`.

   ```
   sudo vim index.html
   ```

4. In the text editor, enter the HTML code for your website. Here's a basic example:

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>My Simple Website</title>
   </head>
   <body>
       <h1>Welcome to Project 2</h1>
       <p>This is a basic HTML website served by Nginx.</p>
   </body>
   </html>
   ```

  To save the script and exit from the vim editor, press `ecs` then `:wq!`.

  Verify that the Nginx configuration points to the correct web root directory (`/var/www/html/project2`). 
  This is usually set in the Nginx configuration file located at `/etc/nginx/sites-available/default` on Ubuntu.

   Open the configuration file for editing:
   ```
   sudo vim /etc/nginx/sites-available/project2
   ```

   Locate the `root` directive within the `server` block and ensure it matches the web root directory:
   ```
   root /var/www/html/project2;
   ```

   Save the file and exit the text editor.

   Restart Nginx to apply the changes:
   ```
   sudo systemctl restart nginx
   ```

   Nginx is now configured to serve the HTML file you created.

   Visit your server's public IP address or domain name in a web browser. You should see your simple HTML website displayed.







