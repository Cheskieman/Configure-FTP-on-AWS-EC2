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

**Part1**
Launch EC2 instance → 

![Launch EC2 Instance](resources/EC2LAUNCHINSTANCE.png)

Choose Instance Name, Select the AMI for the Instance, and Choose the Instance Type & Key Pair

  
![Name and Select AMI](resources/EC2NAMEINSTANCEANDSELECTAMI.png)  
![Choose Instance Type and Key Pair](resources/EC2NEWINSTANCETYPEANDKEYPAIR.png) 

 Select the Edit button next to the Security Group 

![Edit Security Group](resources/EC2EDITBUTTONFORSECURITYGROUP.png)  

Set up the initial Security Group rules

![Initial Security Group Rules](resources/EC2INTIALSECURITYGROUPRULES.png)  

Click Launch at the bottom of the page

![Launch Setup (Bottom of Page)](resources/EC2ENDINGLAUNCHINSTANCEBUTTONSELECT.png) 

Select the instance created and press Connect


![Connect to Instance](resources/EC2CONNECTBUTTON.png) 

 Select the SSH Client Tab

![SSH Client Tab](resources/EC2SSH CLIENTSELECT.png) 

Copy the SSH code in the SSH tab > Open Command Prompt (Admin) > paste code & press Enter.

![SSH via Command Prompt](resources/EC2RELATEDPASTESSSHINSTANCEINTOCOMMANDPROMPT.png) 

In Linux terminal: type the following 3 commands.
1) sudo -i, yum
 
 ![Run `sudo -i`](resources/LINUXTERMINALsudo-icommand.png)  
2) update -y, yum install vsftpd

![Run `yum update -y`,](resources/LINUXTERMINAL yum update -y command.png)  
 3)vi /etc/vsftpd/vsftpd.conf.

 ![Edit Config with `vi /etc/vsftpd/vsftpd.conf`](resources/LINUXTERMINAL vi etcvsftpdvsftpd.conf command.png) 

In Vim: press Shift+I, change anonymous_enable=NO → YES,
Scroll down and uncomment ascii_upload_enable=YES & ascii_download_enable=YES, then Esc :wq Enter.

![Set `anonymous_enable=YES`](resources/VIMEDITORchange anonymous_enableYES.png) 

![Uncomment `ascii_upload_enable=YES` and `ascii_download_enable=YES`](resources/VIM EDITORASCII UPLOAD AND DOWNLOAD REMOVE HASHTAGS COMMENTS.png)  


Back in the Linux terminal: type the following commands

1)systemctl start vsftpd 

![Start vsftpd](resources/BACKLINUXTERMINAL systemctlstartvsftpdcommand.png)  
2)systemctl status vsftpd (check that the status is active) 

![Check vsftpd Status](resources/BACKLINUXTERMINAL systemctlsttatusvsftpdcommand.png) 
3)useradd <type username> & passwd <type password> to create login.

![Create User and Password](resources/BACKLINUXTERMINAL createnewusernameandpasswordcommands.png)  
  
 
 
 
 






**Part2**

* Go back to your EC2 Instance in the AWS Console and select it, Copy the Public IP Address in the Details Section> Open WinSCP from the search tab on Windows (no photo)> In the WinSCP Window, click on New Site, In the Host Name Box, put your EC2 Public IP Address(that you copied over before) as well as put your Username and Password (that you created in Linux earlier) in their respective boxes>  
* Go back again to your EC2 Instance, Select It, Go Down on the Page, and Select Both the Security Tab and the clickable link of the Security Group>Edit the Inbound Rules to be displayed. (as shown in the attached photo.)
*Go back to your Linux Terminal and type both the following 2 commands: 1)sudo -i 2) vi /etc/vsftpd/vsftpd.conf>. Inside your VIM Editor, hit SHIFT + I to enter Insert Mode, scroll down below where it says "listen=NO and paste the following commands (as shown in the attached photo).> Followed by pressing ESC, followed by:wq and ENTER.> type "systemctl restart vsftpd" to restart the terminal.
*Go back to the WinSCP tab and type in both your Username and Password, and the connection will likely be successful. 

![Select PublicIP Address from EC2 Instance](resources/EC2INSTANCESELECTPUBLICIPADDRESS.png)
![Enter Public IP, Linux Created Username & Password into WinSCP](resources/WinSCP Login Screen.png)
![Select in the EC2 Instance Both the Security Tab and the Security Groups Link](resources/EC2INSTANCESECURITYTABAND SECURITYGROUPSELECT.png)
![Select Edit Inbound Rules from Security Groups Page](resources/SECURITYGROUPPAGESELECTEDITINBOUNDRULES.png)
![Actual Editing of the Specific Inbound Rules](resources/SECURITYGROUPPAGEACTUALLYEDITINGREVISING INBOUNDRULES.png)
![Go back into Linux Terminal and type 2 commands 1) sudo-i 2) vi /etc/vsftpd/vsftpd.conf](resources/photo2.png)
![Back inside VIM Editor, paste this command under listen=NO ](resources/BACKINVIMEDITORCOMMANDSTOPASTE.png)
![Write the restart command complete configuration.](resources/BACKINLINUXTERMINALwriterestartcommand.png)
![Try connecting in the WinSCP Window AGAIN](resources/WinSCP Login Screen.png)




##### Contribution Policy

This project is not accepting external contributions, including pull requests or feature requests.

It serves as a personal archive of my learning journey in applying foundational concepts in software development and version control. Active development is not ongoing, and external changes will not be integrated.


![Run `yum install vsftpd`](resources/LINUXTERMINAL yum install vsftpd command.png) 
