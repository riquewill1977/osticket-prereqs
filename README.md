<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


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

Now let's download the <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">installation files</a> for osTicket.








