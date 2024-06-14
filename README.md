<h1>Metasploit Penetration Test Lab</h1>
<p>In this lab, we utilize the Metasploit framework to exploit a vulnerable virtual machine to simulate a penetration test.</p>
<h2>Resources Used: </h2>
<p>- Kali Linux</p>
<p>- Metasploit</p>
<p>- Windows 10</p>
<p>- VMware Workstation Player</p>

<h2>Please note: this is for demonstration purposes only in a lab environment. Do not conduct these actions on any machines without clear permission.</h2>

<h2>1. Setting up Virtual Machines</h2>
<p>- This lab will require a virtual machine that runs Kali Linux, and another virtual machine that requires Windows 10. </p>
<p>- Head to VMWorksation Player and install it according to your actual physical machine (PICTURE Here)</p>
<p>- Once installed, download a Kali Linux ISO & Windows 10 ISO. We will use these files to let our virtual machine have the necessary operating system. Before you install, double-check the hash of the ISO to verify that it hasn’t been modified by anyone else other than the manufacturer.</p>
<p>- Launch VMWorkstation Player, and select “New”</p>
<p>- You can keep all of the default settings, but make sure to choose the correct OS, ISO file, and to make the Network type be bridged. Selecting “bridged” will allow both virtual machines to be on the same LAN as your physical machine. (PICTURE HERE) </p>
<p>- Once the configuration is complete, select "Launch/Play" on the Windows 10 machine, and complete the setup prompts. </p>
<p>- Once the setup is complete, go to the firewall settings and select off for all. This will be what makes the machine vulnerable in this lab environment. If this was a real penetration test, the firewall would most likely be turned on and it would take much more time and effort to try to find a vulnerability to exploit and gain access to the machine. </p>
<p>- Go to the command prompt and type in “ipconfig /all” and hit enter. Take note of what this VM's IP Address is and make sure it’s on the same subnet as your physical machine. (PICTURE HERE)</p>
<p>Select Start to run the Kali Linux virtual machine. You can select all of the defaults for the setup prompts. </p>

<h2>2. Configuring Metasploit</h2>
<p></p>
