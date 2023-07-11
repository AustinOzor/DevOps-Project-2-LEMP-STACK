## TESTING PHP WITH NGINX ###
To test PHP with Nginx, let us follow these steps:

1. Create a PHP test file in the web root directory of Nginx at `/var/www/html/project2/`.
   ```
   sudo vim /var/www/html/project/test.php
   ```

2. In the text editor, enter the following PHP code:

   ```php
   <?php
   phpinfo();
   ?>
   ```

   This code will output the PHP configuration and information when accessed through the web server.

3. Save the file by pressing `Ctrl + O` (for Nano), then press `Enter` to confirm the filename. Exit the text editor by pressing `Ctrl + X`.

4. Restart Nginx to apply any recent configuration changes:
   ```
   sudo systemctl restart nginx
   ```

5. Open a web browser and visit your server's IP address or domain name followed by `/test.php`.
6. For example, if your server's IP address is `123.45.67.89`, you would enter `http://123.45.67.89/test.php` in the browser's address bar.

   The PHP test file should be executed by the server, and you should see a page displaying PHP configuration information.

If the PHP test file executes correctly and displays the PHP information, it indicates that PHP is properly configured and working with Nginx. If you encounter any issues or the PHP code is displayed as plain text, double-check your Nginx and PHP configuration for any errors or misconfigurations.
