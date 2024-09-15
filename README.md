# Project-1-Full-Nagios-Setup

Setting up Nagios for comprehensive system monitoring is a great project. Here's a step-by-step guide to help you get started:

# 1. Preparation
Ensure you have a server: You’ll need a Linux server to install Nagios. A fresh installation of a RHEL-based distribution is ideal.
Update the system: Run sudo yum update to make sure your system is up-to-date.

# 2. Install Required Packages
Install the EPEL repository (Extra Packages for Enterprise Linux):

sudo yum install epel-release
Install required dependencies:

sudo yum install gcc glibc glibc-common make wget unzip

<img width="453" alt="vs" src="https://github.com/user-attachments/assets/8dc5b5a8-ed41-424d-ba80-eeac6562bb2e">


# 3. Download and Install Nagios Core
Download Nagios Core:

cd /tmp

wget https://github.com/NagiosEnterprises/nagioscore/releases/download/4.4.8/nagios-4.4.8.tar.gz


<img width="455" alt="kl" src="https://github.com/user-attachments/assets/7350c0b8-dd64-4602-ac2f-a89092e2e8ef">


Extract and install Nagios Core:

tar xzf nagios-4.4.8.tar.gz
cd nagios-4.4.8
sudo ./configure --with-httpd-conf=/etc/httpd/conf.d
sudo make all
sudo make install
sudo make install-init
sudo make install-config
sudo make install-commandmode

# 4. Install Nagios Plugins
Download Nagios Plugins:

cd /tmp
wget https://github.com/nagios-plugins/nagios-plugins/releases/download/2.3.3/nagios-plugins-2.3.3.tar.gz
Extract and install plugins:

tar xzf nagios-plugins-2.3.3.tar.gz
cd nagios-plugins-2.3.3
./configure
make
sudo make install

<img width="454" alt="64" src="https://github.com/user-attachments/assets/f8b40053-5649-4cd2-9c4c-95eac0270569">



<img width="457" alt="67" src="https://github.com/user-attachments/assets/65a11bea-fe86-4e2f-8c79-1ad14e24d3aa">



# 5. Configure Nagios

Add a Nagios user and group:

sudo useradd nagios
sudo usermod -a -G nagios apache

Configure Nagios Web Interface:

sudo htpasswd -c /usr/local/nagios/etc/htpasswd.users nagiosadmin

<img width="456" alt="cas" src="https://github.com/user-attachments/assets/b037d0aa-64b5-4d4f-969e-62c20895b8aa">


Configure the Nagios service:

sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl start nagios
sudo systemctl enable nagios
Verify Nagios status:

sudo systemctl status nagios

# 6. Access Nagios Web UI
Open your web browser and go to http://<your-server-ip>/nagios. Log in with the username nagiosadmin and the password you set during the configuration.

# 7. Configure Monitoring

Edit configuration files: Configuration files are located in /usr/local/nagios/etc/.

<img width="363" alt="80" src="https://github.com/user-attachments/assets/d1357d9a-e35c-4ad4-88d8-48144bf1e085">


Define hosts and services: You will need to edit nagios.cfg, objects/contacts.cfg, objects/hostgroups.cfg, and objects/services.cfg to define what you want to monitor.

<img width="454" alt="98" src="https://github.com/user-attachments/assets/cbf6a083-2049-4e0c-b1f2-309f2b839694">


# 8. Set Up Notifications

Configure email settings in nagios.cfg to receive notifications.
Test notifications to ensure they are working correctly.

<img width="355" alt="75" src="https://github.com/user-attachments/assets/aaac6af0-14b5-4490-963f-3ee881899a4a">


# 9. Access UI


![photo_2024-09-15_02-13-38](https://github.com/user-attachments/assets/49491858-f6ef-40ba-bb28-4d2d1fd77402)

System Performance:

Nagios comes with a build in UI to access. 

Check the process:

<img width="553" alt="dsss" src="https://github.com/user-attachments/assets/98e85f24-0ea3-41ad-94eb-9c953fbecc53">


You may need to configure and customize these checks depending on your requirements.

# Conclusion
You now have a basic Nagios setup for monitoring system performance. You can expand and customize your configuration as needed to fit your specific requirements. Let me know if you need more details on any step!
