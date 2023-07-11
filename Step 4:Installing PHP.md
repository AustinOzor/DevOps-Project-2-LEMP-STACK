### INSTALLING PHP ###
____________________________________________________________________________________________________________________________________________________
While Apache embeds the PHP interpreter in each request, Nginx requires an external program to 
handle PHP processing and act as a bridge between the PHP interpreter itself and the web server. 
This allows for better overall performance in most PHP-based websites, but it requires additional
configuration. You’ll need to install php8.1-fpm, which stands for “PHP fastCGI process manager” and
uses the current version of PHP (at the time of writing), to tell Nginx to pass PHP requests to this
software for processing. Additionally, you’ll need php-mysql, a PHP module that allows PHP to communicate
with MySQL-based databases. Core PHP packages will automatically be installed as dependencies.

Let use the following commands to install php8.1-fpm and php-mysql packages:

Use the "-y" option with the package manager commands to automatically answer "yes" to any prompts and avoid manual 
confirmation during installation. Here's an updated version of the installation command with the "-y" option:

```
sudo apt install php8.1-fpm php-mysql -y
```

We are all set here. Let us move to the next step and configure nginx to use PHP processor.
