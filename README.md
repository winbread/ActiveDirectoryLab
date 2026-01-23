<h1>Active Directory using Powershell</h1>

 

<h2>Description</h2>
This project consists of building a Domain Controller (AD DS + DNS.) Joining a Windows client to the domain, and bulk-creating 1000 users with PowerShell.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Active Directory Domain Services (AD DS)</b>
- <b>Active Directory Users and Computers (ADUC)</b>

<h2>Environments Used </h2>

- <b>Windows 2019 Server(DC)</b>
- <b>Windows 10</b>
- <b>Oracle VirtualBox</b>

<h2>Network Plan </h2>

- <b>VirtualBox: 2 NICs on the server</b>

     - <b>NIC 1 (Internal Network): AD lab traffic (domain + client communication)</b>
     
     - <b>IP: 192.168.0.10<b>
     - <b>Mask: 255.255.255.0<b>
     - <b>Gateway: empty<b>
     - <b>DNS: 127.0.0.1 (loopback)<b>
     - <b>NIC 2 (NAT): Internet access (updates)</b>>
- <b>DC has RRAS/NAT configured</b>
  - <b>Client gateway: 192.168.0.10</b>
  - <b>DNS: 192.168.0.10</b>
 - <b>DHCP configured (1 Scope)</b>
   - <b>Range: 192.168.0.100-200</b>
   - <b>Mask: 255.255.255.0</b>
   - <b>DNS: 192.168.0.10</b>
   - <b>Gateway: 192.168.0.10</b>


<h2>Lab walk-through:</h2>

<p align="center">
We need to diferenciate the 2 networks adapters on the controller. One adapter is for the internal and the other is for the outside internet.<br/> I'll rename them like this to stand out more when we go to configure them later.
 <br/> 
 <br/> Tip: The adapter with the autoconfig ipv4 is typically the internal adapter.

<img src="images/SS1.png"/>
<br />
<br />
Assign IP address to the internal network  <br/>We will right click -> properties into the internal adapter. <br/> <br/> According to our network plan this is what our configuration would look like:<br/>
<img src="images/SS2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Installation of AD DS and creating domain. <br/> 
Go through the "Add Roles and Features Wizard" on Server Manager to install AD DS.
<br/>
<img src="images/SS3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Promote the server to a domain controller and add a new forest. For this lab we'll just use "mydomain.com"  <br/>
<img src="images/SS4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Once you pass prequisite check, installation should be good to go. VM will auto-restart afer installation. <br/>
<img src="images/SS5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next on our network plan is to installl RAS/NAT to allow client to access internal network through the DC<br/>On the server manager -> Add Roles and Features -> Enable Remote Access<br/>
<img src="images/SS6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Lets make sure we have routing enabled in the features tab, then we will install:  <br/>
<img src="images/SS7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Installation complete:  <br/>
<img src="images/SS8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We are going to want to enable Routing and Remote access. We will go into tools -> Routing and Remoting access -> Right Click on our DC and configure the settings in the wizard <br/>
Make sure we select the Internet adapter. <br/>
<img src="images/SS9.png"/>
<br />
<br />
When your DC appears with the "green arrow" it has been configured succesfully  <br/>
<img src="images/SS10.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Next we want the client to receive an IP that will let them access and browse the internet.  <br/> Through the Roles and Features Wizard we installed a DHCP server. <br/>
<img src="images/SS11.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure our IP address range according to network plan.  <br/>
<img src="images/SS12.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
The Default Gateway will be the DC's IP.  <br/>
<img src="images/SS13.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Lets make sure we activate the scope  <br/>
<img src="images/SS14.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
We will run our Powershell script to make 1000 users.  <br/>
<img src="images/SS15.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Users made  <br/>
<img src="images/SS16.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
We will now join the client to the domain but lets check if our network plan worked by running ipconfig, we should be getting our internet connection through the DC  <br/>
<img src="images/SS17.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
Join the client to the domain  <br/>
<img src="images/SS18.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
Restart client device and in command prompt to run whoami to confirm client has joined domain.  <br/>
<img src="images/SS19.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
