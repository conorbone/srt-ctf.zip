---
title: Zeek
source: https://tryhackme.com/room/zeekbro
author:
  - "[[TryHackMe]]"
published:
created: 2025-09-04
description: Introduction to hands-on network monitoring and threat detection with Zeek (formerly Bro).
tags:
  - try-hack-me
  - soclv1
aliases:
  - zeek
  - bro
---
![[28e589bb58d154301e8b2f12b1d501d4.png]]

> Zeek (formerly Bro) is an open-source and commercial network monitoring tool (traffic analyser).

## Zeek Architecture

- Event Engine
	- where the packets are processed; it is called the event core and is responsible for describing the event without focusing on event details. It is where the packages are divided into parts such as source and destination addresses, protocol identification, session analysis and file extraction.
- Policy Script Interpreter
	- where the semantic analysis is conducted. It is responsible for describing the event correlations by using Zeek scripts.

| **Parameter** | **Description**                           |
| ------------- | ----------------------------------------- |
| **-r**        | Reading option, read/process a pcap file. |
| **-C**        | Ignoring checksum errors.                 |
| **-v**        | Version information.                      |
| **zeekctl**   | ZeekControl module.                       |
## Zeek Logs


| Category             | Description                                                              | **Log Files**                                                                                                                                                                                                                                                                                                                      |
| -------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Network              | Network protocol logs.                                                   | _conn.log, dce_rpc.log, dhcp.log, dnp3.log, dns.log, ftp.log, http.log, irc.log, kerberos.log, modbus.log, modbus_register_change.log, mysql.log, ntlm.log, ntp.log, radius.log, rdp.log, rfb.log, sip.log, smb_cmd.log, smb_files.log, smb_mapping.log, smtp.log, snmp.log, socks.log, ssh.log, ssl.log, syslog.log, tunnel.log._ |
| Files                | File analysis result logs.                                               | _files.log, ocsp.log, pe.log, x509.log._                                                                                                                                                                                                                                                                                           |
| NetControl           | Network control and flow logs.                                           | _netcontrol.log, netcontrol_drop.log, netcontrol_shunt.log, netcontrol_catch_release.log, openflow.log._                                                                                                                                                                                                                           |
| Detection            | Detection and possible indicator logs.                                   | _intel.log, notice.log, notice_alarm.log, signatures.log, traceroute.log._                                                                                                                                                                                                                                                         |
| Network Observations | Network flow logs.                                                       | _known_certs.log, known_hosts.log, known_modbus.log, known_services.log, software.log._                                                                                                                                                                                                                                            |
| Miscellaneous        | Additional logs cover external alerts, inputs and failures.              | _barnyard2.log, dpd.log, unified2.log, unknown_protocols.log, weird.log, weird_stats.log._                                                                                                                                                                                                                                         |
| Zeek Diagnostic      | Zeek diagnostic logs cover system messages, actions and some statistics. | _broker.log, capture_loss.log, cluster.log, config.log, loaded_scripts.log, packet_filter.log, print.log, prof.log, reporter.log, stats.log, stderr.log, stdout.log._                                                                                                                                                              |

Please refer to [Zeek's official documentation](https://docs.zeek.org/en/current/script-reference/log-files.html) and [Corelight log cheat sheet](https://corelight.com/about-zeek/zeek-data) for more information.

> **Zeek-cut** - Cut specific columns from zeek logs.
## Zeek Signatures

> -s flag loads a signature file 

### structure:

| signature id               | conditions                                                                                                                                                                                      | action                                                                                                                                |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Unique** signature name. | **Header:** Filtering the packet headers for specific source and destination addresses, protocol and port numbers.<br><br>**Content:** Filtering the packet payload for specific value/pattern. | **Default action:** Create the "signatures.log" file in case of a signature match.<br><br>**Additional action:** Trigger a Zeek scrip |

### Conditions 
| Condition Field               | Available Filters                                                                                                                                                                                                                                                                                                                                                |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Header                        | src-ip: Source IP.<br><br>dst-ip: Destination IP.<br><br>src-port: Source port.<br><br>dst-port: Destination port.<br><br>ip-proto: Target protocol. Supported protocols; TCP, UDP, ICMP, ICMP6, IP, IP6                                                                                                                                                         |
| Content                       | **payload:** Packet payload.  <br>**http-request:** Decoded HTTP requests.  <br>**http-request-header:** Client-side HTTP headers.  <br>**http-request-body:** Client-side HTTP request bodys.  <br>**http-reply-header:** Server-side HTTP headers.  <br>**http-reply-body:** Server-side HTTP request bodys.  <br>**ftp:** Command line input of FTP sessions. |
| **Context**                   | **same-ip:** Filtering the source and destination addresses for duplication.                                                                                                                                                                                                                                                                                     |
| Action                        | **event:** Signature match message.                                                                                                                                                                                                                                                                                                                              |
| **Comparison  <br>Operators** | **==**, **!=**, **<**, **<=**, **>**, **>=**                                                                                                                                                                                                                                                                                                                     |
| **NOTE!**                     | Filters accept string, numeric and regex values.                                                                                                                                                                                                                                                                                                                 |
### Example | Cleartext Submission of Password


```zeek signature
signature http-password {
     ip-proto == tcp
     dst-port == 80
     payload /.*password.*/
     event "Cleartext Password Found!"
}

# signature: Signature name.
# ip-proto: Filtering TCP connection.
# dst-port: Filtering destination port 80.
# payload: Filtering the "password" phrase.
# event: Signature match message.
```

Zeek signatures support regex. Regex ".*" matches any character zero or more times. The rule will match when a "password" phrase is detected in the packet payload. Once the match occurs, Zeek will generate an alert and create additional log files (signatures.log and notice.log).


```markdown
ubuntu@ubuntu$ zeek -C -r http.pcap -s http-password.sig 
ubuntu@ubuntu$ ls
clear-logs.sh  conn.log  files.log  http-password.sig  http.log  http.pcap  notice.log  packet_filter.log  signatures.log

ubuntu@ubuntu$ cat notice.log  | zeek-cut id.orig_h id.resp_h msg 
10.10.57.178	44.228.249.3	10.10.57.178: Cleartext Password Found!
10.10.57.178	44.228.249.3	10.10.57.178: Cleartext Password Found!

ubuntu@ubuntu$ cat signatures.log | zeek-cut src_addr dest_addr sig_id event_msg 
10.10.57.178		http-password	10.10.57.178: Cleartext Password Found!
10.10.57.178		http-password	10.10.57.178: Cleartext Password Found!
```
