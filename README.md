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

- Kali Linux (Vms)(Hydra, Nmap)

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
### Nmap:
![image alt]()
### Splunk:
![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/797b17f4bbecb6a27621548b3d38e73b5475f05e/Project%20images/Splunk1.png)

#### Port Scanning Detection
- Multiple connection attempts across different ports.
- Detected using Splunk logs.

__________________

#### Brute force:
Hydra:

`hydra -l user -P passwords.txt <Windows ip> smb2 -V`

Splunk qurue:

`index=* EventCode=4625 ComputerName="TARGET-PC"`
### Hydra:
![image alt]()
### Splunk:
![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/797b17f4bbecb6a27621548b3d38e73b5475f05e/Project%20images/Splunk2.png)


#### Brute Force Detection
- Multiple failed login attempts detected from a single source IP.
- Windows Event ID: 4625
- Splunk used to identify repeated authentication failures.
____________________

#### Servicenow:

### Create incident port scanning:

![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/797b17f4bbecb6a27621548b3d38e73b5475f05e/Project%20images/Servicenow%20port%20scanning.png)

### Create incident brute force:

![image alt](https://github.com/Nuha240/SOC-Home-Lab/blob/797b17f4bbecb6a27621548b3d38e73b5475f05e/Project%20images/Servicenow%20brute%20force.png)


#### MITRE ATT&CK Mapping:

-Brute Force: T1110

-Port Scanning: T1595

________________________________________

#### Conclusion

The project demonstrates how a SOC analyst can detect brute force attacks, Port scanning by analyzing authentication logs and identifying abnormal login behavior using Splunk.
