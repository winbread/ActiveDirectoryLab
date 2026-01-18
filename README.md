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
     - <b>NIC 2 (NAT): Internet access (updates)</b>>
- <b>DC has RRAS/NAT configured</b>
  - <b>Client gateway: 192.168.0.10</b>
  - <b>DNS: 192.168.0.10</b>


<h2>Lab walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
