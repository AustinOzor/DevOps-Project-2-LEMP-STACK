### LEMP STACK ##
Is a software stack used for web development and hosting. It is an acronym that stands for Linux, Nginx, MySQL, and PHP/Python/Perl.
The LEMP stack provides a robust and efficient environment for hosting dynamic websites and web applications
Each component of the stack serves a specific purpose:
__________________________________________________________________________________________________________________________________________________________
  #### Linux: ####
  It is the operating system used as the foundation of the stack. Linux provides a stable and secure environment for hosting web applications.
  #### Nginx: ####
   It is a high-performance web server and reverse proxy server. Nginx is known for its efficiency in handling concurrent connections and serving
   static content. It is often used as a front-end server to handle incoming web requests.
#### MySQL: ####
   It is a popular open-source relational database management system (RDBMS). MySQL is widely used for storing and managing structured data.
   It is known for its reliability, scalability, and ease of use.
#### PHP/Python/Perl: ####
   These are scripting languages commonly used for web development. PHP is the most commonly used language in the LEMP stack.
    Python and Perl are alternatives that can be used based on specific project requirements.
_________________________________________________________________________________________________________________________________________________________
#### Requirement ####
To get started with a free-tier AWS account and create an EC2 instance with the specified requirements, follow these steps:

1. Sign up for a free-tier AWS account: Go to the AWS website (aws.amazon.com) and sign up for a new account. During the signup process, you'll need to provide your personal and payment information. Make sure to select the "Free" account type to take advantage of the free-tier offerings.

2. Access the EC2 service: Once your AWS account is set up, you can access the EC2 service by logging into the AWS Management Console. You can find the EC2 service by searching for "EC2" in the search bar or by navigating to the "Compute" section.

3. Launch an EC2 instance: In the EC2 console, click on "Launch Instance" to begin the instance creation process.

4. Choose an Amazon Machine Image (AMI): In the "Choose an Amazon Machine Image" step, search for "Ubuntu Server 22.04 LTS" and select the appropriate image.

5. Choose an instance type: In the "Choose an Instance Type" step, select "t2.micro" from the list. This instance type is eligible for the free-tier usage.

6. Configure instance details: Proceed to the next steps, such as configuring instance details, adding storage, configuring security groups, and so on. You can accept the default settings for most of these steps, but make sure to configure security groups to allow SSH access. Add a rule to allow incoming SSH (port 22) connections from your IP address.

7. Review and launch: Review your instance settings, and then click on "Launch" to initiate the creation of the EC2 instance.

8. Create an SSH key pair: In the "Create a new key pair" dialog, select "Create a new key pair" and provide a name for the key pair. This will generate a new SSH key pair that you can use to connect to the EC2 instance securely.

9. Launch the instance: Click on "Launch Instances" to start the EC2 instance creation process. The instance will be provisioned based on the selected settings.

10. Connect to the EC2 instance: Once the instance is launched, you can connect to it using SSH. To do this, open your preferred terminal application and use the SSH command along with the key pair you created. The command will look like this:
```
ssh -i /path/to/your/key.pem ubuntu@<public-IP-address-of-your-instance>
```
Make sure to replace `/path/to/your/key.pem` with the actual path to your SSH key pair file and `<public-IP-address-of-your-instance>` with the public IP address assigned to your EC2 instance.

Remember to terminate the EC2 instance after you finish using it to avoid incurring additional charges. You can do this by selecting the instance in the EC2 console and clicking on the "Actions" button, then choosing "Instance State" and "Terminate".
__________________________________________________________________________________________________________________________________________________________
