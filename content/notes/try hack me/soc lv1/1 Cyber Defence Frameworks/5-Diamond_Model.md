---
draft: false
title:  "The Diamond Model"
date: 2025-03-11 
categories: 
    - TryHackMe
    - SOC-LV1
---

` SOC Level 1 > Cyber Defence Frameworks > Diamond Model `

 four core features: 

 - adversary 
 - infrastructure
 - capability
 - victim


 ## Adversary

**Adversary Operator** is the “hacker” or person(s) conducting the intrusion activity.

**Adversary Customer** is the entity that stands to benefit from the activity conducted in the intrusion. It may be the same person who stands behind the adversary operator, or it may be a separate person or group.

As an example, an adversary customer could control different operators simultaneously. Each operator might have its capabilities and infrastructure.

## Victim 

**Victim Personae** are the people and organizations being targeted and whose assets are being attacked and exploited. These can be organization names, people’s names, industries, job roles, interests, etc.

**Victim Assets** are the attack surface and include the set of systems, networks, email addresses, hosts, IP addresses, social networking accounts, etc., to which the adversary will direct their capabilities.

## Capability 

**Capability Capacity** is all of the vulnerabilities and exposures that the individual capability can use. 

An **Adversary Arsenal** is a set of capabilities that belong to an adversary. The combined capacities of an adversary's capabilities make it the adversary's arsenal.

## Infrastructure 

**Type 1**:     infrastructure controlled or owned by the adversary


**Type 2**:      controlled by an intermediary, Sometimes unaware, obfuscates the attribution 
    malware staging servers, malicious domain names, compromised email accounts, etc.

**Service Providers**: services considered critical for the adversary availability of Type 1 and Type 2 Infrastructures, for example, Internet Service Providers, domain registrars, and webmail providers.


## Event Meta Features

  - Timestamp 
  - Phase
    1. Reconnaissance
    2. Weaponization
    3. Delivery
    4. Exploitation
    5. Installation
    6. Command & Control
    7. Actions on Objective
  - Result 
  - Direction
    - Victim-to-Infrastructure, Infrastructure-to-Victim, Infrastructure-to-Infrastructure Est.
  - Methodology
  - Resources 

