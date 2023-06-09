# Deployed-a-LAMP-Stack-Application-on-Amazon-Light-sail
You start by deploying a new Lightsail instance that includes Apache, MySQL, and PHP preinstalled. Then, you add the demo application code. When you're done, you will have a solid understanding of how to use Light sail to quickly stand up a multi-tier web application.
Her I can Explain How to do  Deployed-a-LAMP-Stack-Application-on-Amazon-Light-sail
Step 1:
First Create a an AWS Account and Then sign Navigate To Amzon Light-sail Homepage .
Use the Below link :
https://signin.aws.amazon.com/signin?redirect_uri=https%3A%2F%2Flightsail.aws.amazon.com%2Fls%2Fwebapp%2Fhome%2Finstances%3Fstate%3DhashArgs%2523%26isauthcode%3Dtrue&client_id=arn%3Aaws%3Aiam%3A%3A015428540659%3Auser%2Fparksidewebapp&forceMobileApp=0&code_challenge=lntay6x8J6IQIv18JeBeA-fqX9R9UBu465JGDR-Qg6s&code_challenge_method=SHA-256
Copy the URL  and paste It in a browser.
Step 2:
Create an Amazon Lightsail instance:
In this area we can do ,you start the process of creating an instance by choosing the AWS Region where you want your demo application to run. Additionally, you choose the LAMP Blueprint. Blueprints are preconfigured instance templates that include the core services your application needs to run – in this case, Apache, MySQL, and PHP. 
a. Choose Create instance on the Instances tab of the Lightsail homepage.
b. An AWS Region and Availability Zone is selected for you. Choose Change AWS Region and Availability Zone to create your instance in another location.
c. Retain Linux/Unix as the platform and under Select a blueprint choose LAMP (PHP 7).
Step 3: Install the application code
In this area, you use a launch script to install the demo application. Launch scripts run the first time an instance boots up, and are used to do any initial configuration on an instance. 
a. Choose +Add launch script.
b. Paste the script below into the launch script text window.

The script performs the following actions:

Removes the default Apache website
Clones the application code from GitHub into the htdocs directory
Ensures the configuration file is writeable
Uses sed to read the local database password from a file on the disk and insert it into the configuration file
Runs an SQL script to set up the application’s database
# remove default website
#-----------------------
cd /opt/bitnami/apache2/htdocs 
rm -rf *

# clone github repo
#------------------
git clone -b loft https://github.com/mikegcoleman/todo-php .

# set write permissions on the settings file
#-----------------------------------
sudo chown bitnami:daemon connectvalues.php
chmod 666 connectvalues.php

# inject database password into configuration file
#-------------------------------------------------
sed -i.bak "s/<password>/$(cat /home/bitnami/bitnami_application_password)/;" /opt/bitnami/apache2/htdocs/connectvalues.php

# create database
#----------------
cat /home/bitnami/htdocs/data/init.sql | /opt/bitnami/mariadb/bin/mysql -u root -p$(cat /home/bitnami/bitnami_application_password)
  
  c. Choose the free tier instance plan.
  A plan includes a low, predictable-cost, machine configuration (RAM, SSD, vCPU), and data transfer allowance. You can try the $3.50 USD Lightsail plan without charge for three months (up to 750 hours). AWS credits three free months to your account.
  d. Enter a name for your instance and choose Create instance.

Resource name guidelines:

Must be unique within each AWS Region in your Lightsail account.
Must contain 2 to 255 characters.
Must start and end with an alphanumeric character or number.
Can include alphanumeric characters, numbers, periods, dashes, and underscores.
  Step 4: Test the application
  In this section, you access the running application to ensure everything is running properly
  a. It will take 2-3 minutes for your instance to start up. Once the status is listed as Running, move on to the next step.
 
Note: You may need to refresh your web browser to see the updated status.
  b. Make note of your instance’s IP address.
  c. In your web browser, navigate to the instance’s IP address. You should see the application running.
  Step 5: Clean up
  
  It is a best practice to delete resources that you are no longer using so that you don't incur unintended charges. If you don't plan to use the instance you created, follow these instructions to delete it.
  a. On the Instances tab of the Lightsail home page, choose the ellipsis (⋮) icon next to the LAMP instance you just created and choose Delete.
  2. Select Yes, delete from the prompt.
  
  Conclusion
  Congratulations! Finally Completed the ![Screenshot (7)](https://github.com/SrikanthVaddineni/Deployed-a-LAMP-Stack-Application-on-Amazon-Light-sail/assets/92942943/a4d2646f-ddde-43ce-89dc-ef82495e5274)
![Screenshot (10)](https://github.com/SrikanthVaddineni/Deployed-a-LAMP-Stack-Application-on-Amazon-Light-sail/assets/92942943/559d0b22-2bb4-44b2-9a8a-d4f1dd942012)
 Amazon Lightsail to run a LAMP stack application
  
  Additional Informatiom:
  
  Amazon Lightsail is great for developers, web pros, and anyone looking to get started on AWS quickly and cheaply. You can launch instances, databases, and SSD-based storage; transfer data; monitor your resources; and so much more in a managed way.
  
