## INSTALLING NGINX WEB-SERVER ##
NGINX is an open-source web server and reverse proxy server known for its performance and scalability.
It serves static content efficiently, acts as a reverse proxy to distribute requests to backend servers, 
and balances the load for better availability. NGINX supports caching, SSL/TLS termination, HTTP/2, and WebSocket,
and can compress and optimize content. It is highly configurable and widely used to improve web application performance, 
scalability, and reliability.

### Steps in Installing Nginx Servive on Ubuntu 22.04 LTS ###
We use the following commands to install the nginx.

1. Update the server packages
 ```
sudo apt update
 ```
2. Install Nginx
```
sudo apt install nginx -y
```
3. Verify the installation and check if the status of Nginx is active.
```
sudo systemctl status ngix
```
If you see the active message as shown below then it means Nginx is has install successful and it it active. 
![ngins statu](https://github.com/AustinOzor/DevOps-Project-2-LEMP-STACK/assets/99667583/7fb2f712-4683-4738-841b-17896a429af5)

To access Nginx on the localhost or on the web, you can follow these steps to edit the security group on your EC2 instance and add a new rule to the inbound rules:

1. Log in to the AWS Management Console.
2. Go to the EC2 Dashboard.
3. Select the EC2 instance where Nginx is installed.
4. Scroll down to the "Description" tab and make a note of the Security Groups associated with your instance.
5. Go to the "Security Groups" section in the EC2 Dashboard.
6. Select the security group associated with your EC2 instance.
7. In the "Inbound" tab, click on the "Edit inbound rules" button.
8. Click on the "Add Rule" button.
9. In the "Type" dropdown, select "HTTP" or "Custom TCP" if "HTTP" is not available.
   - If you select "HTTP", it will automatically use port 80.
   - If you select "Custom TCP", enter "80" as the port number.
10. In the "Source" field, you have a few options:
   - To allow access from any IP address, leave it as the default "0.0.0.0/0" (or "::/0" for IPv6).
   - To restrict access to specific IP addresses or ranges, enter the desired IP or CIDR notation.
   - To allow access from your own IP address, select "My IP" (this option will automatically fill your current IP address).
11. Click on the "Save rules" button to apply the changes.

Now inbound traffic on port 80 (HTTP) will be allowed to reach your EC2 instance. This will enable you to access Nginx on the localhost or on the web using the public IP address or domain name associated with your EC2 instance. 

Let check nginx locally using the following command:
```
curl http://localhost:80
or
curl http://127.0.0.1 :80
```
Let access ngixn on the web browser with the following commands:
```
http://<EC2 instance ip>:80
```
If you request to access nginx is successful you will see a message as show on the image below:

![nginx successful](https://github.com/AustinOzor/DevOps-Project-2-LEMP-STACK/assets/99667583/acea567b-ea52-468d-88ed-104c186d6872)

Let move to the next step and install MYSQL.
