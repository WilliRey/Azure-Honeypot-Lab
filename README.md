# Azure-Honeypot-Lab
In this lab I use Microsoft Sentinel and Azure to log Failed RDP attempts and plot it to a map. 

Step 1: Create a VM and security group to allow all network traffic. 
![Alt text](<Screenshot 2024-01-06 183624.png>)

Step 2: Create a Log Repository 

![Alt text](<Screenshot 2024-01-06 184041.png>)

Step 3: Enable Micorosoft Defender for Logs. 
![Alt text](<Screenshot 2024-01-06 184208.png>)

Step 4: Create a new Sentinel workspace. 
![Alt text](<Screenshot 2024-01-06 184329.png>)

Step 5: Next we RDP to the VM and turn off windows firewall. 

Step 6: Obtain API Key from IPgeolocation.com and 

Step 7: Created ps1 file and entered Geolocation API Key  to log all failed RDP events and send them to a log file. "script authored by joshmakador1" 
WilliRey/Azure-Honeypot-Lab/Custom_Security_Log_Exporter.ps1

Step 8: Failed RDP 