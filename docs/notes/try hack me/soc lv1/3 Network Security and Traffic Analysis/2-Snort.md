>  SNORT is an open-source, rule-based Network Intrusion Detection and Prevention System (NIDS/NIPS) . It was developed and still maintained by Martin Roesch, open-source contributors, and the Cisco Talos team. 
> The official description: "Snort is the foremost Open Source Intrusion Prevention System (IPS) in the world. Snort IPS uses a series of rules that help define malicious network activity and uses those rules to find packets that match against them and generate alerts for users." 


## Introduction to IDS/IPS


### Intrusion Detection System (IDS)

**IDS** is a passive monitoring solution for detecting possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for generating alerts for each suspicious event. 

**IDS** Systems: 
- Network Intrusion Detection System (NIDS) 
    - NIDS monitors the traffic flow from various areas of the network. The aim is to investigate the traffic on the entire subnet. If a signature is identified, an alert is created.
- Host-based Intrusion Detection System (HIDS)
    - HIDS monitors the traffic flow from a single endpoint device. The aim is to investigate the traffic on a particular device. If a signature is identified, an alert is created.



### Intrusion Prevention System (IPS)

IPS is an **active** protecting solution for preventing possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for stopping/preventing/terminating the suspicious event as soon as the detection is performed. 


Types of **IPS**:

- Network Intrusion Prevention System (NIPS) 
    - NIPS monitors the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If a signature is identified, **the connection is terminated**. 
- Behaviour-based Intrusion Prevention System (Network Behaviour Analysis - NBA) 
    - Behaviour-based systems monitor the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If an anomaly is identified, **the connection is terminated.**
- Wireless Intrusion Prevention System (WIPS) 
    - WIPS monitors the traffic flow from of wireless network. The aim is to protect the wireless traffic and stop possible attacks launched from there. If a signature is identified, **the connection is terminated.** 
-  Host-based Intrusion Prevention System (HIPS) 
    - HIPS actively protects the traffic flow from a single endpoint device. The aim is to investigate the traffic on a particular device. If a signature is identified, **the connection is terminated.** 

### Detection/Prevention Techniques

There are three main detection and prevention techniques used in IDS and IPS solutions;
Technique 	Approach

|Signature-Based|This technique relies on rules that identify the specific patterns of the known malicious behaviour. This model helps detect known threats. |
|---------------|--------------------------------------------------------------------------|
|Behaviour-Based|This technique identifies new threats with new patterns that pass through signatures. The model compares the known/normal with unknown/abnormal behaviours. This model helps detect previously unknown or new threats.|
|Policy-Based|This technique compares detected activities with system configuration and security policies. This model helps detect policy violations.|


## First Interaction with Snort

``` sudo snort -c /etc/snort/snort.conf ```


## Operation Mode 1: Sniffer Mode



## Operation Mode 2: Packet Logger Mode
## Operation Mode 3: IDS/IPS
## Operation Mode 4: PCAP Investigation
## Snort Rule Structure
## Snort2 Operation Logic: Points to Remember


> [Snort-TryHackme](https://tryhackme.com/room/snort)