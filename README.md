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
![image alt]()


### Wiresharke:
![image alt]()

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
![image alt]()
### Event viewer:
![image alt]()
![image alt]()
### Splunk:
![image alt]()


#### The attack was identified based on:

• High number of failed login attempts

• Repeated attempts within a short time

• Same source IP address


#### Detection Result:
Multiple failed login attempts indicating possible brute force activity.
____________________

#### Servicenow:

### Create incident port scanning:

![image alt]()

### Create incident brute force:

![image alt]()


#### MITRE ATT&CK Mapping:

-Brute Force: T1110

-Port Scanning: T1595

________________________________________

#### Conclusion

The project demonstrates how a SOC analyst can detect brute force attacks, Port scanning by analyzing authentication logs and identifying abnormal login behavior using Splunk.
