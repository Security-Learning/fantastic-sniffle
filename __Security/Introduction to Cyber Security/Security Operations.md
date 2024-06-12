Security Operations
========================

## Introduction to Security Operations

*Security Operations Center (SOC)* is a team of IT security professionals tasked with monitoring a company's network and systems

Their purpose of monitoring is to
1. Find vulnerabilities on the network
2. Detect unauthorized activity
3. Discover policy violations
4. Detect Intrusions
5. Support with the incident response


## Elements of Security Operations

### Data Sources
SOC uses many data sources to monitor the network for signs of intrusions and to detect any malicious behavior.
- Server logs: logs contain information about various activities such as successful and failed login attempts, among many others
- DNS activity: DNS protocol is responsible for converting a domain name to IP address.
- Firewall logs: logs can reveal much information about what packets passed or tried to pass through the firewall
- DHCP logs: Responsible for assigning IP address to the systems that try to connect to a network. It has automatically provided your device with the network settings whenever you can join a network without manual configuration. By inspecting DHCP transactions, we can learn about the devices that joined the network

SOC might use a *Security Information and Event Management (SIEM)* system. The SIEM aggregates the data from the different sources so that the SOC can efficiently correlate the data and respond to attacks


### SOC Services

SOC services include reactive and proactive services in addition to other services:

Reactive services: refer to tasks initiated after detecting an intrusion or a malicious event
1. Monitor Security posture: monitoring the network and computers for security alerts and notifications responding to them as the need dictates
2. Vulnerability management: finding vulnerabilities in the company systems and patching them. 
3. Malware analysis: SOC might recover malicious programs that reached the network. SOC can do basic analysis by executing it in a controlled environment.
4. Intrusion detection: IDS is used to detect and log intrusions and suspicious packets. 
5. Reporting: Essential to report incidents and alarms. Reporting is necessary to ensure a smooth workflow to support compliance requirements

Proactive services refer to tasks handled by the SOC without any indicator of an intrusion.
1. Network Security Monitoring(NSM): focuses on monitoring the network data and analyzing the traffic to detect signs of intrusions
2. Threat hunting:  with threat hunting, SOC assumes an intrusion has already taken place and begins its hunt to see if they can confirm this assumption
3. Threat Intelligence: focuses on learning about potential adversaries and their tactics and techniques to improve the company's defences. The purpose would be to establish a threat-informed defence

## Hands On
[file](../THM_HandsOn/Security Operations - Hands On.md)