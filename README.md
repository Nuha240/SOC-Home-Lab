### Home SOC Lab – Port Scanning, Brute Force Detection. 

#### Project Overview:

This project simulates common cyber attacks in a SOC environment, including port scanning and brute force attacks. The objective is to detect suspicious behavior using Splunk and generate security incidents.

#### The lab demonstrates:

- Attack simulation

- Log collection

- SIEM detection

- Incident investigation

- Ticket creation in ServiceNow

- MITRE ATT&CK mapping

#### Tools Used:

- Kali Linux (Vms)

- Hydra

- Nmap

- Windows (Vms)

- Splunk Enterprise(SIEM)

- ServiceNow(Ticketing)

#### Port scanning:
Nmap:

`nmap -sS <Windows ip>`

Splunk qurue:

`index=*
| bin _time span=1m
| stats count by host, _time
| where count > 50`

### Kali(Nmap):
![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Klai%20nmap.png)

### Splunk:
![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Splunk1.png)

#### The attack was identified based on:


• Suspicious network activity

• Reconnaissance phase

• Attacker gathering info

#### Detection Result:
Suspicious high number of connection attempts indicating possible reconnaissance activity.

__________________

#### Brute force:
Hydra:

`hydra -l user -P passwords.txt <Windows ip> smb2 -V`

Splunk qurue:

`index=* EventCode=4625 ComputerName="TARGET-PC"
| stats count by Account_Name, Source_Network_Address
| where count > 10`

### Kali(Hydra):
![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Kali%20hydra.png)
### Splunk:
![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Splunk3.png)
![image](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Splunk%20search3.png)
### Event viewer:
![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Event%20viewer1.png)

#### The attack was identified based on:

• High number of failed login attempts

• Repeated attempts within a short time

• Same source IP address


#### Detection Result:
Multiple failed login attempts indicating possible brute force activity.
____________________

#### Servicenow:

### Create incident port scanning:

![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Servicenow%20port%20scanning.png)

### Create incident brute force:

![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/5d44bc4e9b6e939f7cb44d366b64c05ac2d1a51f/Project%20imgs/Servicenow%20brute%20force.png)


#### MITRE ATT&CK Mapping:

-Brute Force: T1110

-Port Scanning: T1595

________________________________________

#### Conclusion

The project demonstrates how a SOC analyst can detect brute force attacks, Port scanning by analyzing authentication logs and identifying abnormal login behavior using Splunk.
