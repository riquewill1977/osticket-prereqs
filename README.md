<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Windows 10 VM
- osTicket

<h2>Installation Steps</h2>
<p>Let's begin with creating a resource group in microsoft azure. This will act as a logical container that will hold related azure resources like network security groups and virtual networks.</p>


<p>Create a resource group via the web portal</p>


a. Navigate to service <b>Resource groups</b>.<br />
b. Click Add to create a new resource group.<br />
c. Configure the values as shown in the screenshot below:<br />
d.) Name your Resource Group. I'm using "RG-osTicket"<br />
e.) Select your region. I'm using US West US 3<br />
f.) Click review + create.<br />


Creating a Resource Group<br />
![creating resource group](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/410f6b8c-b985-4b8b-b8de-593fa24740f1)






<p>Note: you can navigate to any resource by using azure's seach box at the very top of the screen as shown in the image below</p>

![image](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/f0d20a8b-5296-49a7-8f39-ebc56cc13e69)


<p>Creating the Windows 10 virtual machine</p>

a. Click create and select Azure virtual machine<br />
b. Select your existing Resource group "RG-osTicket"<br />
c. Configure the values as shown in the screenshot below:<br />
d.) Name your virtual machine. I'm using "vm-osticket"<br />
e.) Select your region. Preferrably the same as your resource group<br />
f.) Click review + create.<br />

![creating vm](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/916cfb78-f33f-48c5-93d6-be4f5ab09b39)
![creating vm 2](https://github.com/riquewill1977/osticket-prereqs/assets/139101776/95acc8cc-1e3d-4302-8797-fe651feb22c6)


<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
