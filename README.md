# Tutorial on Configuring your EC2 instance as an FTP server. 

## Full Step-by-Step guide with Snapshots to describe and illustrate how to configure an EC2 Instance as an FTP Server.

### **This project will display how to set up and configure an FTP server on an EC2 instance, including user creation, security group adjustments, and WinSCP access verification.**

*Create a new EC2 Instance 
* Log in to Linux Terminal via SSH on the EC2 instance
* Run Neccasary Configuration Files inside Linux and Vim Editor for configuration of the FTP Server to work with the EC2 Instance.
* Create a Username and Password in the Linux Terminal 
* Copy and paste the EC2 Instance Public IP Address in WinSCP, as well as enter the Username and Password created in the Linux Terminal into WinSCP
* Reconfigure both the security group inbound rules as well as the VIM Editor.
* Logging back into WinSCP after both the reconfiguration is complete for the Security Group and the VIM Editor.


#### Step-by-Step Instructions on how to set up and configure an FTP server on an EC2 instance, including user creation, security group adjustments, and WinSCP access verification.

Part 1

Launch EC2 instance

<p align="center"> <img src="resources/EC2LAUNCHINSTANCE.png" alt="Launch EC2 Instance" width="900" /> </p>

Choose instance name, AMI, type, and key pair

<p align="center"> <img src="resources/EC2NAMEINSTANCEANDSELECTAMI.png" alt="Choose Instance Name and AMI" width="900" /> </p> <p align="center"> <img src="resources/EC2NEWINSTANCETYPEANDKEYPAIR.png" alt="Choose Instance Type and Key Pair" width="900" /> </p>

Edit the security group

<p align="center"> <img src="resources/EC2EDITBUTTONFORSECURITYGROUP.png" alt="Edit Security Group" width="900" /> </p>

View initial security group rules

<p align="center"> <img src="resources/EC2INTIALSECURITYGROUPRULES.png" alt="Initial Security Group Rules" width="900" /> </p>

Click launch at the bottom of the page

<p align="center"> <img src="resources/EC2ENDINGLAUNCHINSTANCEBUTTONSELECT.png" alt="Launch Instance Setup Confirmation" width="900" /> </p>

Connect to the instance

<p align="center"> <img src="resources/EC2CONNECTBUTTON.png" alt="Connect to Instance" width="900" /> </p>

Select the SSH client tab

<p align="center"> <img src="resources/EC2SSH CLIENTSELECT.png" alt="SSH Client Tab" width="900" /> </p>

SSH into the instance using Command Prompt

<p align="center"> <img src="resources/EC2RELATEDPASTESSSHINSTANCEINTOCOMMANDPROMPT.png" alt="SSH via Command Prompt" width="900" /> </p>

Run sudo -i in Linux terminal

<p align="center"> <img src="resources/LINUXTERMINALsudo-icommand.png" alt="Linux terminal sudo -i command" width="900" /> </p>

Run yum update -y and install vsftpd

<p align="center"> <img src="resources/LINUXTERMINAL yum update -y command.png" alt="Linux terminal yum update -y command" width="900" /> </p>

Edit the vsftpd config file with Vim

<p align="center"> <img src="resources/LINUXTERMINAL vi etcvsftpdvsftpd.conf command.png" alt="Linux terminal vi config command" width="900" /> </p>

Set anonymous_enable=YES in config

<p align="center"> <img src="resources/VIMEDITORchange anonymous_enableYES.png" alt="VIM set anonymous_enable YES" width="900" /> </p>

Uncomment ascii upload and download options

<p align="center"> <img src="resources/VIM EDITORASCII UPLOAD AND DOWNLOAD REMOVE HASHTAGS COMMENTS.png" alt="VIM ascii upload/download enable" width="900" /> </p>

Start the vsftpd service

<p align="center"> <img src="resources/BACKLINUXTERMINAL systemctlstartvsftpdcommand.png" alt="systemctl start vsftpd" width="900" /> </p>

Check the vsftpd service status

<p align="center"> <img src="resources/BACKLINUXTERMINAL systemctlsttatusvsftpdcommand.png" alt="systemctl status vsftpd" width="900" /> </p>

Create a new user and set a password

<p align="center"> <img src="resources/BACKLINUXTERMINAL createnewusernameandpasswordcommands.png" alt="Linux create new user and password" width="900" /> </p>
Part 2

Copy the public IP from EC2 instance details

<p align="center"> <img src="resources/EC2INSTANCESELECTPUBLICIPADDRESS.png" alt="Copy Public IP from EC2 Instance" width="900" /> </p>

Enter IP, username, and password in WinSCP

<p align="center"> <img src="resources/WinSCP Login Screen.png" alt="WinSCP login screen" width="900" /> </p>

Open the security tab and security group link in EC2 instance

<p align="center"> <img src="resources/EC2INSTANCESECURITYTABAND SECURITYGROUPSELECT.png" alt="EC2 Instance Security Tab and Security Group Select" width="900" /> </p>

Edit inbound rules in the security group

<p align="center"> <img src="resources/SECURITYGROUPPAGESELECTEDITINBOUNDRULES.png" alt="Edit inbound rules in security group" width="900" /> </p> <p align="center"> <img src="resources/SECURITYGROUPPAGEACTUALLYEDITINGREVISING INBOUNDRULES.png" alt="Inbound rules editing screen" width="900" /> </p>

Reopen vsftpd config in Linux terminal

<p align="center"> <img src="resources/photo2.png" alt="Linux terminal reopen vsftpd config" width="900" /> </p>

Paste configuration under listen=NO in Vim

<p align="center"> <img src="resources/BACKINVIMEDITORCOMMANDSTOPASTE.png" alt="Paste config under listen=NO" width="900" /> </p>

Restart the vsftpd service

<p align="center"> <img src="resources/BACKINLINUXTERMINALwriterestartcommand.png" alt="Restart vsftpd service" width="900" /> </p>

Retry WinSCP login with credentials

<p align="center"> <img src="resources/WinSCP Login Screen.png" alt="WinSCP login retry" width="900" /> </p>

##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.



