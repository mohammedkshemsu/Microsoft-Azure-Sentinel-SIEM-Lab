
<h1>Microsoft Azure Sentinel (SIEM) Honeypot Lab</h1>

 <h2>Project Overview :</h2>
The project aims to set up an Azure-based honeypot to monitor and analyze attacks from different regions. It involves creating an Azure subscription, configuring a virtual machine, setting up logging, and using PowerShell to extract and map attacker data.
<br />


<h2>Step-by-Step Project Guide</h2>

<ul>
  <li>Create Azure Subscription by going to the Azure portal (portal.azure.com).</li>
  <li>Sign in or create an Azure account.</li>
  <li>Create a new Azure subscription (using your provided credit card details).</li>
  <li>Note: You'll receive $200 worth of free credits for the next month.</li>
</ul>
<p align="center">
Create Azure Subscription: <br/>
<img src="https://i.imgur.com/j5SMGY5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create Virtual Machine:  <br/>
 <ul>
  <li>In the Azure portal, navigate to "Virtual Machines.</li>
  <li>Create a new virtual machine in the "honeypot lab" resource group.</li>
  <li>Name it (e.g., honeypot-vm) and choose a suitable geographic region</li>
  <li>Specify a username and password for the VM.</li>
  <li>Configure the Network Security Group to allow all inbound traffic, making the VM easily
discoverable.</li>
 </ul>
<img src="https://i.imgur.com/ejal6GD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

Allow All In Firewall: <br/>

<ul>
 <li>For faster discovery by attackers, disable the Windows Firewall on the VM.</li>
 <li>Go to the Windows Defender Firewall settings and turn off all network profiles (domain,
private, public).</li>

</ul>
<img src="https://i.imgur.com/Lv1hk5A.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/66gWNYQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create Log Analytics Workspace:  <br/>

<ul>
 <li>Go to "Log Analytics Workspaces" in the Azure portal.</li>
 <li>Create a new workspace in the "honeypot lab" resource group</li>
 <li>This workspace will store logs, including custom logs with geographic information.</li>

</ul>
<img src="https://i.imgur.com/AkgYTWo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Connect Log Analytics Workspace to VM:  <br/>

<ul>
 <li>In "Log Analytics," select your workspace.</li>
 <li>Find the virtual machine you created and click "Connect" to establish the connection.</li>

</ul>
<img src="https://i.imgur.com/lcxkVJz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/h7DNClJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/BvETOl4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enable Logging from VM to Log Analytics Workspace:  <br/>

<ul>
 <li>Access "Security Center" in the Azure portal.</li>
 <li>In "Pricing and Settings," select the Log Analytics workspace created earlier.</li>
 <li>Enable Defender for Azure services and disable unnecessary components.</li>
 <li>Go to "Data Collection" and configure the workspace to collect all events.</li>
</ul>
<img src="https://i.imgur.com/ehvpHbR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rs0iReR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Setup Azure Sentinel:  <br/>

<ul>
 <li>In the Azure portal (portal.azure.com), navigate to "Azure Sentinel.</li>
 <li>Create an Azure Sentinel instance. Select the Log Analytics workspace you created earlier
for storing logs.</li>
 <li>This will serve as your Security Information and Event Management (SIEM) solution.</li>
 
</ul>
<img src="https://i.imgur.com/IffNUjG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log Into VM With Remote Desktop:  <br/>

<ul>
 <li>Access the VM using Remote Desktop Protocol (RDP).</li>
 <li>On your own computer, open Remote Desktop and paste the public IP address of the VM.</li>
 <li>Use the username and password you created for the VM.</li>
 <li>Take note of the VM's IP address (to differentiate between your computer and the VM).</li>
 
</ul>
<img src="https://i.imgur.com/tAqRJaq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/vcJ9Eal.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe Event Viewer Logs In VM:  <br/>

<ul>
 <li>Inside the VM, access "Event Viewer" to inspect event logs.</li>
 <li>Focus on Event ID 4625, which represents failed login attempts.</li>
 <li>You should observe details like the username, target machine, and failure reasons.</li>

</ul>
<img src="https://i.imgur.com/pVlHXZ5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Turn Off Windows Firewall On VM:  <br/>
<img src="https://i.imgur.com/yzN2OdV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/SifBFCV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/SuJS0KA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/if5IBSx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Download PowerShell Script:  <br/>
<ul>
 <li>Download or copy the provided PowerShell script for exporting security logs.</li>
 <li>You can obtain this script from the provided GitHub link or copy it manually.</li>
</ul>

<img src="https://i.imgur.com/HlxTQfV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Get Geolocation.io API Key:  <br/>
<ul>
<li>Sign up for an API key on the Geolocation.io website.</li>
<li>The API key is required to convert IP addresses to geographical data.</li>
<li>Paste your API key into the PowerShell script.</li>
 
</ul>


<img src="https://i.imgur.com/v5dlpNp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/XKzQFd6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run PowerShell Script To Get Geo Data From Attackers:  <br/>

<ul>
 <li>Open PowerShell ISE on the VM.</li>
 <li>Paste the PowerShell script into PowerShell ISE.</li>
 <li>Save the script on the VM's desktop (e.g., log-exporter.ps1).</li>
 <li>Execute the script.</li>
 <li>The script continuously scans the event logs for failed login attempts and extracts
geographical data using the Geolocation.io API.</li>
 <li>It creates a log file with attacker IP addresses and associated geographical data.</li>
</ul>
<img src="https://i.imgur.com/JMctSIN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create Custom Log In Log Analytics Workspace To Bring In The Custom Log:  <br/>
<ul>
 <li>The log file will be stored in `C:\ProgramData\`. You can use this log for analysis and
visualization.</li>
 <li>Configure Azure Sentinel to read this custom log and plot attackers on a map based on
geographical data.</li>
 
</ul>
<img src="https://i.imgur.com/CjYMwes.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/BxQNEMa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/bDu0Ib1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/a451vHT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/1D8Xq0I.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/eQkAy1n.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/1Fo7lJK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create Custom Fields/Extract Fields From Raw Custom Log Data:  <br/>
<img src="https://i.imgur.com/s7UWvDZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/HzXJv5g.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jMzIjF9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/HvBn5oX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/JkuEjfs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/iUpDeT8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rUFw2C8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/KEFaUHO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Q1kqHv6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/1tXI6ot.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ZvQP3f0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/CyUSKKO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ummW9L7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/pztvfXB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/ZIrJnMJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/HtO5bEa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Bp6maXC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FQByvsM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/hqZIf0h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Setup Map In Sentinel With Latitude and Longitude:  <br/>

<ul>
 <li>Open Azure Sentinel from the Azure portal.</li>
 <li>Access your workbook and remove default widgets.</li>
 <li>Add a new query to set up the map visualization.</li>
 <li>Modify the query as needed, including selecting the fields you want to display (e.g., latitude,
longitude, label, or country).</li>
 
</ul>
<img src="https://i.imgur.com/ISIYPjT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/AU62wEZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/3ycJ1HH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/rfVPBtw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

Monitor Map Data (Final Check): <br/>
<ul>
 <li>As you've been doing, keep an eye on the map in Azure Sentinel to observe login attempts.</li>
 <li>Notice any patterns or trends in the activity from different regions.</li>
 
</ul>
<img src="https://i.imgur.com/04jKmyv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
