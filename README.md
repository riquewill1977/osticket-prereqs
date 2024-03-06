<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This instructional guide delineates the requisite steps and procedures for the installation of osTicket, an open-source help desk ticketing system.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)
- Heidi SQL

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Windows 10 VM
- osTicket

<h2>Installation Steps</h2>
<p>Let's begin with creating a resource group in microsoft azure. This will act as a logical container that will hold related azure resources like network security groups and virtual networks.</p>


<p>Create a resource group via the web portal</p>


- Navigate to service <b>Resource groups</b>.<br />
- Click Add to create a new resource group.<br />
- Configure the values as shown in the screenshot below:<br />
- Name your Resource Group. I'm using "RG-osTicket"<br />
- Select your region. I'm using US West US 3<br />
- Click review + create.<br />


Creating a Resource Group<br />
![creating resource group](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/410f6b8c-b985-4b8b-b8de-593fa24740f1)






<p>Note: you can navigate to any resource by using azure's seach box at the very top of the screen as shown in the image below</p>

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/f0d20a8b-5296-49a7-8f39-ebc56cc13e69)


<p>Create Windows 10 virtual machine</p>

- Click create and select Azure virtual machine<br />
- Select your existing Resource group "RG-osTicket"<br />
- Configure the values as shown in the screenshot below:<br />
- Name your virtual machine. I'm using "vm-osticket"<br />
- Select your region. Preferrably the same as your resource group<br />
- Select size suitable enough for this task. I'm using 4 vcpus, 16GB mem.
- Enter your username and password
- Inbound ports should be set to allow selected ports and select RDP (remote desktop)
- Check the I confirm I have an eligible windows 10/11 license box and click Next<br />

![creating vm](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/916cfb78-f33f-48c5-93d6-be4f5ab09b39)
![creating vm 2](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/95acc8cc-1e3d-4302-8797-fe651feb22c6)


<p>
Skip the Disk section and move onto Networking. Azure will auto create a virtual network, subnet and public ip. Click review + created.
This will take you to the validation screen, if all looks well, click create.
</p>
<p>Give Azure a minute or so to create the vm. Once completed, use the search box and type virtual machine where you should see your newly created virtual machine. In order to remote into this virtual machine we'll need to get the public IP which will be located all the way to the right-hand side as shown in the image below.</p>

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/601632b7-d971-439d-86a0-1df9d7478edd)

You can also achieve this by clicking on the virtual machine name in which the public IP will be displayed on the right (see below image)

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/5b37705b-ba2a-4d13-a9c4-17463f0711b3)



<p>
Copy the VM's public IP address and past it into remote desktop. Use windows search box and type "remote desktop" 
Select remote desktop and paste the IP address and connect. Select the show options section to use your username and password you created in azure for the vm.</p>

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/bbce75b8-3736-484e-a8d9-34a460afafb8)
![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/bcdbfec8-a4aa-4a25-9b88-f8893b24d49a)

<p>Now that we're logged in, go to the windows search box in the vm and type "control" then click on control panel and click programs.</p>

  
<p>Under Programs and Features, click "Turn Windows features on or off" </p>

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/1205f7e1-bad7-4baf-b467-a5de38f48232)

<p>Select Internet Information Services (IIS)</p>

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/03d66df1-05a4-4451-95eb-e2091d521ca8)

Expand the following folder to turn on CGI:


- Internet Information Services<br />
- World Wide Web Services<br />
- Application Development Features<br />
- Check the box for "CGI"<br />

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/a859db42-33c8-4039-9621-977c4504c394)

Collaps "Application Development Features", then expand "Common HTTP Features" and be sure all boxes are checked. Click "OK" once you've checked all boxes to begin installation.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/06f58234-1174-4a05-a372-88d3110ee8cd)

Once installed, run a quick test by entering your loopback IP into a browser 127.0.0.1. You should see a webpage that looks like the image below.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/1cd52bee-2a61-4e76-900a-e4e5dabae521)

Now let's download the <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">installation files</a> needed for osTicket.

Download and install the following files:

- PHPManagerForIIS_V1.5.0
- rewrite_amd64_en-US
- php-7.3.8-nts-Win32-VC15-x86 (create a PHP folder and save it here c:\PHP. Then right click the zip file and extract the contents into the PHP folder)
- VC_redist.x86
- mysql-5.5.62-win32 (when installing choose the "Typical" install and make sure the box is checked for "Launch the MySQL Instance..." and click finish. This will launch the configuration wizard. Select "Standard Configuration" and setup your password. Make sure you save those credentials somewhere safe.)

Next we'll open IIS and run as a Admin

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/12fde96d-9549-4a82-acaf-8be15b43c092)

Double click to open "PHP Manager. Click on "Register new PHP version" and navigate to the PHP folder we created previously and select the php-cgi.ext file

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/13fb0bda-251c-4b5d-8edb-89dc3a271632)

Be sure to restart the server after updating.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/7c2d35aa-f7c5-4cd5-a4d2-21b548da5571)

Download osTicket from the <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">installation files</a>

Once downloaded, extract and copy the “upload” folder from the osTicket-v1.15.8 zip file to c:\inetpub\wwwroot

![osTicket_upload into root](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/67c66ff2-b30e-4789-b1e7-a79ec10465a7)

Rename the "upload" folder to "osTicket"

![Screenshot 2024-03-05 154226](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/9c619353-3d8a-40e4-8337-b83939d203cb)

Go back into IIS and restart the server. Then from the navigation pane click on "osTicket" by going to Sites > Default Web Site > osTicket.

Once selected click on "Browse *:80 (http).

![Screenshot 2024-03-05 155908](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/91518706-bb2f-41be-b0dc-4ecb57cbe4a0)

You should now be able to see the osTicket Installer page as shown below. 

![Screenshot 2024-03-05 163653](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/bf1baffb-ea83-4c7b-a2e9-fab4cfbf90b8)

There are several extensions not installed, so we'll need to go back IIS and under the osTicket folder double click "PHP Manager".

Under PHP Extensions click "Enable or disable an extension.

Select the following extensions and enable them.

- php_imap.dll
- php_intl.dll
- php_opcache.dll
  

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/c05558ed-d2e0-47bd-865d-a7b56a52b6e6)

Go back to your browser with the osTicket Installer and refresh the page. Some of the extensions should now have a green check as shown below.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/73269c30-007b-45f2-a0c9-9ed8813ef08e)

We now need to rename the ost-sampleconfig.php to ost-config.php removing "sample" from the name.

We will undertake this action to ensure universal access and prevent conflicts arising from user manipulation of the file.

Navigate to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/3af9820a-2d78-403e-adaa-1d84961d68c7)

Assign Permissions to ost-config.php:

- right click and go to properties
- click the security tab
- click on Advanced
- Disable inheritance
- remove all inherited permissions from this object
- click add
- click "select a principal" and type the word "Everyone" then click Check Names and "OK"


![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/58fb27f7-b2c2-4f29-a981-4148640c38a3)

Next check the "Full control" box and click "OK".

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/6a40e4fa-679a-438f-a370-7f8566aa9056)

Click Apply, then OK and OK again to close out.
![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/8723316a-8ad5-4bbd-8624-f9383066272c)

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/3dea0c5c-af18-4689-bb68-dee6b005f8b0)

We'll now download Heidi SQL from the <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">installation files</a>

Heidi SQL is a popular open-source database management tool with a user-friendly interface primarily used for interacting with and managing various database systems. 

In our case we'll use it to manage MySQL. Install Heidi SQL and click finish and make sure "Launch HeidiSQL" is checked.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/66400a2d-eb4b-4b13-9767-9d3d87ff6d8f)

Before we can do anything we need to go back to the browser with osTicket Installer and click continue. 

Enter any credentials you like, just be sure to save the information for later use.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/10fc288f-d187-4ac0-81b4-5767c1433caa)


In order to fill out the last section "Database Settings" we need to go back to Heidi SQL and click on "New" then enter the password we created in MySQL and click "Open"

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/244bd68f-00da-458d-9801-6206332b17a1)

Right click Unnamed, then Create new > Database

Name it "osTicket" then click "OK".

![Screenshot 2024-03-05 190432](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/007036a6-9dd9-4f5c-8bf9-08f900596b79)

Go back to the browser with osTicket Installer and enter the credentials for "Database Settings" and click "Install Now.

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/b0681746-dbef-4b8d-b198-05d53f86e042)

If done correctly, you should see this on your screen.

![Screenshot 2024-03-05 191526](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/3db47f5c-c656-4c96-97f2-3d18eec4fb67)

Clean up:

- Delete the "setup" folder located in C:\inetpub\wwwroot\osTicket
- Set the permissions back to read only for "ost-config.php" file located in C:\inetpub\wwwroot\osTicket\include by going to properties, then the security tab, click on Advanced, select "Everyone" and click on edit and uncheck Full control, Modify and Write, then apply.

Congratulations!!! 

If done correctly you can now log in via the <a href="http://localhost/osTicket/scp/login.php">Admin</a> link.

- <a href="http://localhost/osTicket/scp/login.php">Admins</a>
- <a href="http://localhost/osTicket/">End Users</a>


