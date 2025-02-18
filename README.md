# Basic-LAN-Setup-with-DHCP-Packet-Tracer-Homelab-
To simulate a small office network with three wired computers, one printer, and a wireless laptop, all connected to the same LAN. The router will provide DHCP to all devices, and you will test connectivity between them.
<h1>Active Directory Home Lab</h1>


 ### [Youtube video for the Project]()

<h2>Description</h2>
This project demonstrates the setup and configuration of a basic Active Directory environment that resembles a small corporate network. This project will be a walkthrough of everything to get the lab running and the clients internal network connected to the internet through the domain controller. I used a Python script to add 100 users and configure them for me. I will be doing more with this lab setup for future projects and will be removing most of the 1000 users and readding more in the future. This showcases efficient automation and a seamless integration of users into the network infrastructure.
<br />


<h2>Languages and Utilities Used</h2>
- <b>Python</b> 
- <b>PowerShell</b> 
- <b>Diskpart</b>

<h2>Environments Used </h2>

- <b>Windows 10</b>
- <b>Virtual Box</b>
- <b>Windows Server 2019</b>

<h2>Program walk-through:</h2>

<p align="center">
Diagram of the project Network: <br/>
<img src="https://imgur.com/0AZG1AM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Install Windows Server 2019, After setting up virtualbox and doing minor configurations for virtualbox: <br/>
<img src="https://imgur.com/nsc6VLS.png](https://imgur.com/Wx2dEPp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/Wx2dEPp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/T5ADoYL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/a9T9ZZz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Set the Admin username and password: <br/>
<img src="https://imgur.com/xBDN4kh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Change the  name for your home IP to Internet and the other IP to Internal for your Network setup: <br/>
<img src="https://imgur.com/3RkpPNr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Rename the PC to DC for "Domain Controller, then restart the VB: <br/>
<img src="https://imgur.com/vVRjZ8H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Set the Internal IP address in ethernet settings to 172.16.0.1 with subnet mask 255.255.255.0. Give it a DNS address of 127.0.0.1: <br/>
<img src="https://imgur.com/Z5zik94.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Sign out and Sign back in as Admin again with your password: <br/>
<img src="https://imgur.com/KOvT5Kc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Create an Organizational Unit for the Domain, And name it _ADMINS: <br/>
<img src="https://imgur.com/zIWlzmN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/49qKnio.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Create a new User for the _ADMINS Organizational Unit, and name it, this will be your first Domain Admin User Account. Set the Password for it as well, then Sign out: <br/>
<img src="https://imgur.com/ERFGAGQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/5bBdjbS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://imgur.com/j8Irfti.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://imgur.com/FD2ZwBM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/> 
<br />
</p>

<p align="center">
In the add roles and features wizard, under server roles tab, select remote access option, then under Role Services select the Routing checkbox and click next : <br/>
<img src="https://imgur.com/mzSQ0Iv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://imgur.com/jvGq4MT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Under Routing and Remote Access, right-click the DC and select "configure and enable routing and remote access, then select network address translation (NAT) option and click next, then select the first option and choose the INTERNET option: <br/>
<img src="https://imgur.com/LEzw6lR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/49Wu0jt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/jxxQdQ9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
</p>

<p align="center">
select add roles and features wizard, then select next, then select Role-based or feature based install, then select a server from server pool, and choose your domain from the list. In server rules select DHCP Server checkbox, and start the install.: <br/>
<img src="https://imgur.com/6XPt6oJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/GoNJsK5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/mLPQVB8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/TCEwT9S.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
</p>

<p align="center">
Select "DHCP" from tools dropdown, then right-click the IPv4 under the domain in DHCP and select new scope, then enter the IP range we used earlier in the config for the name of the scope "172.16.0.100-200" and click next. Re-enter the Ip in both start and end IP but enter 100 for start and 200 for end, and use a length of 24, and use the subnet mask "255.255.255.0". on the next section that says "Router", enter the IP address of "172.16.0.1". in the next section that says "Domain Name and DNS Servers", enter "myDomain.com" under "parent domain", and enter the IP address "172.16.0.1" into the IP address bar and select add and then next. under the "WINS Servers" section, enter nothing and click next. Finally, check "yes, I want to activate this scope now" and click next and finish.: <br/>
<img src="https://imgur.com/va4tFIi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/O7XCL5i.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/CjtRIat.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/oqsL298.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/Eit9wTx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/1p5VIPM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/MeTxXc3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/wtsDd7E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
right-click the Domain and select "Authorize": <br/>
<img src="https://imgur.com/xhr8GBA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
In the "server manager/Localserver", select "IE Enhanced Security Configuration", and then select "off" for both options and select "ok": <br/>
<img src="https://imgur.com/b6lQXIr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
I imported a Python code that I used to add 1000 pre-configured users with the same password for inital setup. : <br/>
<img src="https://imgur.com/0fKfkhd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/QGMaLmh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Next head to the "Virtual Box manager" and select "add". Next, in the "create virtual machine window", under "Name and operating System", enter "CLIENT1" for the name. Next, find your windows install ISO file and select it. Next, select "Windows 10 (64-bit)", and click "finish".: <br/>
<img src="https://imgur.com/tiMtz9j.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
The CLIENT1 should appear below the DC. Go to settings for CLIENT1, and select System. select processor tab, and set the Processors to 4 or whatever suites your needs.: <br/>
<img src="https://imgur.com/gPQb2h5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Navigate to "Network" tab in "settings", and under "adapter 1", find "Attached to" and select "Internal Network", then click "OK".: <br/>
<img src="https://imgur.com/C3mOUU2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Its time to start up the CLIENT1, so start it up and select the Windows ISO file from the drop down. : <br/>
<img src="https://imgur.com/bDMqbAO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

<p align="center">
Time to start the Windows 10 install! For me I skipped activation, but if you need to activate your Windows then do so. Select your Language of choice, and then click next. Next make sure to select "Windows 10 pro" and NOT home edition for this lab. Next, select "Custom install", and then on the next screen, select your Drive. For the next screen I selected "Limited Experience", but if you need to select the other option you can. I named the PC "User" for this lab, and left the password blank. We should be logged into the home screen now.: <br/>
<img src="https://imgur.com/4YB5Mwu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/ZiJlin9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/7SUVVxr.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/9fRaQNc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://imgur.com/2r7Lh8C.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://imgur.com/6eB19sV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/i30LVi4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
</p>

<p align="center">
Now that we are on the home screen, We want to open "CMD" as Admin and run the command "ipconfig /all", and check for a Default Gateway. If it has the right IP for the Default Gateway then we can move on and run "ping www.google.com" to check for connection to the internet. Next we can run the command "ping mydomain.com", This will show you if your connected and everything is set up correct so far. Finally, we can run the command "hostname" To see what comes up.   : <br/>
<img src="https://imgur.com/FAkqEGw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/n0eZx0d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/v3LII26.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://imgur.com/YUoysUl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   
 
<br />
</p>

<p align="center">
We need to rename the PC, so we will open Windows start and find the PC settings menu and rename the PC to "CLIENT1", and also select the domain option and enter "mydomain.com", then apply settings. You will need to enter the Admin login to make the change. Finally, the PC will restart. : <br/>
<img src="https://imgur.com/aZRorrK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/oXyL7Sg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/aNsa896.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://imgur.com/sdYh2eW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
</p>

 
<br />
</p>

<p align="center">
Next we head back over to DHCP tool in the Server manager, and select the "Address Leases" and check if our client IP is in there. Next, select "Computers" inside of the Domain folder and check to see if "CLIENT1" computer has populated. : <br/>
<img src="https://imgur.com/9jy1k9L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/4KnST6t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<br />
</p>

<br />
</p>

<p align="center">
Now that we have verified some things, lets log into a user account from our list of users. Select "other user" and use login credentials from a desired user and login. : <br/>
<img src="https://imgur.com/6bcYD2z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <img src="https://imgur.com/tsvgXpN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

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
