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

Step 6: Obtain API Key from IPgeolocation.com

Step 7: Created ps1 file and entered Geolocation API Key  to log all failed RDP events and send them to a log file. "script authored by joshmakador1" 
WilliRey/Azure-Honeypot-Lab/Custom_Security_Log_Exporter.ps1

Step 8: Creat custom log in Log Analytics workspace to bring in RDP log
(copy the log to local machine from VM)
![Alt text](<Screensho 2024-01-06 200223.png>)

Step 9: Extract fields from Log entries.
![Alt text](<Screenshot 2024-01-06 202114.png>)

Step 10: Setup Sentinel Map with Longitude and Latitude with query: 
FAILED_RDP_WITH_GEO_CL | summarize event_count=count() by sourcehost_CF, latitude_CF, longitude_CF, country_CF, label_CF, destinationhost_CF
| where destinationhost_CF != "samplehost"
| where sourcehost_CF != ""

![Alt text](<Screenshot 2024-01-06 202435.png>)


Step 11: Let the VM run to capture failed RDP logs. These were my results over the span of 24 hrs. 
![Alt text](<Screenshot 2024-01-06 202554.png>)
