# Automated-Apache-Webserver

Create a user.
Update the system:
sudo dnf update -y

Install tools:
sudo dnf install net-tools vim wget curl -y

The Bash Script

#!/bin/bash

# Update System
sudo dnf update -y

# Install Apache
sudo dnf install httpd -y

# Enable and Start Apache Service
sudo systemctl enable httpd
sudo systemctl start httpd

# Create a Simple Web Page
echo "<h1>Welcome to RHEL 9.5 Web Server!</h1>" | sudo tee /var/www/html/index.html

# Allow HTTP Service through Firewall
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --reload

# Check Apache Status
sudo systemctl status httpd | grep Active

How to Run:
Save the script inside your VM:
nano apache_setup.sh

Make it executable:
chmod +x apache_setup.sh

Run the script:
./apache_setup.sh

Testing:
Open a browser (from host)
Enter the VM’s IP address:
http://<your_vm_ip>

You should see:
Welcome to RHEL 9.5 Web Server!
