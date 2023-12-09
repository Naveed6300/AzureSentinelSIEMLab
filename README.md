# AzureSentinelSIEMLab
This lab is inspired by Josh Madakor's Sentinel Lab --> [https://github.com/joshmadakor1/Sentinel-Lab](https://github.com/joshmadakor1/Sentinel-Lab)
Since his lab is over 2 years old, several things have been deprecated on Azure Cloud, this lab works around those changes to achieve the same result as of 12/2023. 


Explore Azure Sentinel, a cloud SIEM, and a vulnerable Azure VM exposed to global cyberattacks. Monitor and map attacks to learn SIEM and honeypot usage, extract attacker data from Windows logs using PowerShell and a third-party API for valuable insights.

# Summary of Lab 
1. Set up Azure Sentinel, a cloud-based SIEM, and a vulnerable virtual machine in Azure, which will be exposed to the internet to attract and log live cyberattacks from different countries around the world. By monitoring and mapping the attacks, users can gain insights into how to use a SIEM and honeypot, and also learn to extract attacker data from Windows logs using PowerShell and a third-party API.

2. Set up a virtual machine in Azure to act as a honeypot for cyber attacks. Create a Log Analytics Workspace to ingest logs from the virtual machine and create a custom log that contains geographic information to help identify the source of the attacks. Next, enable the ability to gather logs from the virtual machine into the Log Analytics Workspace via the Security Center, before connecting it to the virtual machine in the Log Analytics Workspace. Finally, set up Azure Sentinel, a Security Information and Event Management (SIEM) solution, to visualize the attack data in real-time.

3. Log into the virtual machine using remote desktop, check the security event logs, and obtain IP addresses of unsuccessful login attempts. The IP addresses will be used to create a custom log, which has information about the country, state or province, city, and latitude and longitude of the IP. The log will be sent to the log analytics workspace in Azure and visualized on a map using Azure Sentinel. Before creating the custom log, turn off the firewall on the virtual machine so that the machine can respond to ICMP echo requests easily.
   
4. Download and run the PowerShell script that exports a custom security log, which is used to identify failed logins. The script runs perpetually and looks through the event logs, grabbing the IP addresses of failed login attempts and converting them to geographical data using an API key. The resulting data is outputted to a log file in a program data folder that is hidden by default. This log file includes sample data that will be used later to train the log analytics workspace to parse the custom log file.
    
5. Create a custom log in an Azure Sentinel log analytics workspace with geo data from the virtual machine honeypot that logs failed login attempts. The custom log will help bring the honeypot's log data into the workspace for analysis. 

6. Create a query using KQL to extract information from the raw data column in the Azure Sentinel portal to make certain fields, such as latitude, longitude, and country. By doing this, we can plot countries on the map using latitude and longitude and use the country in case the longitude and latitude get too messed up.
   
7. Set up the geo map in Azure Sentinel. Check the parsed out fields of a failed login log if it looks okay. The map displays the location by country or latitude and longitude fields, exclude unnecessary records and label the metrics in the map. 

8. The host device, whether it's a computer or a phone, will be a target for cyber attacks regardless of whether it has anything valuable on it or not. Bots are constantly scouring the internet for vulnerable hosts to exploit, so it's essential to take steps to secure your device. Use strong passwords with multi-factor authentication and avoid common usernames, such as 'administrator'. The lab shows how the host device has already received thousands of login attempts from around the world in just a matter of hours, highlighting the importance of taking cybersecurity seriously.
