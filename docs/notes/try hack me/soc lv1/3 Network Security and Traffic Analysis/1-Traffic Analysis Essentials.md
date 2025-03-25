## Base Network Security Control Levels:

- Physical: Physical security controls prevent unauthorised physical access to networking devices, cable boards, locks, and all linked components.
- Technical: Data security controls prevent unauthorised access to network data, like installing tunnels and implementing security layers.
- Administrative: Administrative security controls provide consistency in security operations like creating policies, access levels and authentication processes.

### The main approaches:

| Access Control                                                                                              | Threat Control                                                                                                                                |
| :------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------- |
| The starting point of Network Security. It is a set of controls to ensure authentication and authorisation. | Detecting and preventing anomalous/malicious activities on the network. It contains both internal (trusted) and external traffic data probes. |

### The key elements of Access Control:


| Firewall Protection                  | Controls incoming and outgoing network traffic with predetermined security rules. Designed to block suspicious/malicious traffic and application-layer threats while allowing legitimate and expected traffic.        |
| :------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Network Access Control (NAC)         | Controls the devices' suitability before access to the network. Designed to verify device specifications and conditions are compliant with the predetermined profile before connecting to the network.                |
| Identity and Access Management (IAM) | Controls and manages the asset identities and user access to data systems and resources over the network.                                                                                                             |
| Load Balancing                       | Controls the resource usage to distribute (based on metrics) tasks over a set of resources and improve overall data processing flow.                                                                                  |
| Network Segmentation                 | Creates and controls network ranges and segmentation to isolate the users' access levels, group assets with common functionalities, and improve the protection of sensitive/internal devices/data in a safer network. |
| Virtual Private Networks (VPN)       | Creates and controls encrypted communication between devices (typically for secure remote access) over the network (including communications over the internet).                                                      |
| Zero Trust Model                     | Suggests configuring and implementing the access and permissions at a minimum level (providing access required to fulfil the assigned role). The mindset is focused on: "Never trust, always verify".                 |

### The key elements of Threat Control:

- Intrusion Detection and Prevention (IDS/IPS)
    Inspects the traffic and creates alerts (IDS) or resets the connection (IPS) when detecting an anomaly/threat.
- Data Loss Prevention (DLP)
	Inspects the traffic (performs content inspection and contextual analysis of the data on the wire) and blocks the extraction of sensitive data.
- Endpoint Protection
	Protecting all kinds of endpoints and appliances that connect to the network by using a multi-layered approach like encryption, antivirus, antimalware, DLP, and IDS/IPS.
- Cloud Security 
    Protecting cloud/online-based systems resources from threats and data leakage by applying suitable countermeasures like VPN and data encryption.
- Security Information and Event Management (SIEM)
	Technology that helps threat detection, compliance, and security incident management, through available data (logs and traffic statistics) by using event and context analysis to identify anomalies, threats, and vulnerabilities.
- Security Orchestration Automation and Response (SOAR)
	Technology that helps coordinate and automates tasks between various people, tools, and data within a single platform to identify anomalies, threats, and vulnerabilities. It also supports vulnerability management, incident response, and security operations.
- Network Traffic Analysis & Network Detection and Response 
    Inspecting network traffic or traffic capture to identify anomalies and threats.


### Typical Network Security Management Operation is explained in the given table:  

|   |   |   |   |   |
|---|---|---|---|---|
|Deployment|Configuration|Management|Monitoring|Maintenance|
|- Device and software installation<br>- Initial configuration<br>- Automation|- Feature configuration<br>- Initial network access configuration|- Security policy implementation<br>- NAT and VPN implementation<br>- Threat mitigation|- System monitoring<br>- User activity monitoring<br>- Threat monitoring  <br>    <br>- Log and traffic sample capturing|- Upgrades<br>- Security updates<br>- Rule adjustments<br>- Licence management<br>- Configuration updates|


## Traffic Analysis / Network Traffic Analysis

>Traffic Analysis is a method of intercepting, recording/monitoring, and analysing network data and communication patterns to detect and respond to system health issues, network anomalies, and threats. The network is a rich data source, so traffic analysis is useful for security and operational matters. The operational issues cover system availability checks and measuring performance, and the security issues cover anomaly and suspicious activity detection on the network.

Traffic analysis is one of the essential approaches used in network security, and it is part of multiple disciplines of network security operations listed below:

- Network Sniffing and Packet Analysis (Covered in [**Wireshark room**](https://tryhackme.com/room/wiresharkthebasics))
- Network Monitoring (Covered in [**Zeek room**](https://tryhackme.com/room/zeekbro))
- Intrusion Detection and Prevention (Covered in [**Snort room**](https://tryhackme.com/room/snort))  
- Network Forensics (Covered in [**NetworkMiner room**](https://tryhackme.com/room/networkminer))
- Threat Hunting (Covered in [**Brim room**](https://tryhackme.com/room/brim))

There are two main techniques used in Traffic Analysis:

| **Flow Analysis**                                                                                                                                                                                                                                                                                                                            | **Packet Analysis**                                                                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Collecting data/evidence from the networking devices. This type of analysis aims to provide statistical results through the data summary without applying in-depth packet-level investigation.<br><br>- **Advantage:** Easy to collect and analyse.<br>- **Challenge:** Doesn't provide full packet details to get the root cause of a case. | Collecting all available network data. Applying in-depth packet-level investigation (often called Deep Packet Inspection (DPI) ) to detect and block anomalous and malicious packets.<br><br>- **Advantage:** Provides full packet details to get the root cause of a case.<br>- **Challenge:** Requires time and skillset to analyse. |

