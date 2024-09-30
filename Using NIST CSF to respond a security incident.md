# Scenario
You are a cybersecurity analyst working for a multimedia company that offers web design services, graphic design, and social media marketing solutions to small businesses. Your organization recently experienced a DDoS attack, which compromised the internal network for two hours until it was resolved.

During the attack, your organization’s network services suddenly stopped responding due to an incoming flood of ICMP packets. Normal internal network traffic could not access any network resources. The incident management team responded by blocking incoming ICMP packets, stopping all non-critical network services offline, and restoring critical network services.

The company’s cybersecurity team then investigated the security event. They found that a malicious actor had sent a flood of ICMP pings into the company’s network through an unconfigured firewall. This vulnerability allowed the malicious attacker to overwhelm the company’s network through a distributed denial of service (DDoS) attack.

To address this security event, the network security team implemented:
- A new firewall rule to limit the rate of incoming ICMP packets
- Source IP address verification on the firewall to check for spoofed IP addresses on incoming ICMP packets
- Network monitoring software to detect abnormal traffic patterns
- An IDS/IPS system to filter out some ICMP traffic based on suspicious characteristics

As a cybersecurity analyst, you are tasked with using this security event to create a plan to improve your company’s network security, following the National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF). You will use the CSF to help you navigate through the different steps of analyzing this cybersecurity event and integrate your analysis into a general security strategy:

- Identify security risks through regular audits of internal networks, systems, devices, and access privileges to identify potential gaps in security.
- Protect internal assets through the implementation of policies, procedures, training and tools that help mitigate cybersecurity threats.
- Detect potential security incidents and improve monitoring capabilities to increase the speed and efficiency of detections.
- Respond to contain, neutralize, and analyze security incidents; implement improvements to the security process.
- Recover affected systems to normal operation and restore systems data and/or assets that have been affected by an incident.

| Function | Description |
| -- | -- |
| Summary | The organization suffered a DDoS attack, which compromised the internal network for two hours until it was resolved. An incoming flood of ICMP packets made the network to stop responding, what caused that the access to any network resource were unavailable. The incident management team decided to block incoming ICMP packets to restore critical network services to stop the flood of the packets received. |
| Identify | The company's security team investigated the event and found that a malicious actor sent a flood of ICMP pings into the company's network through unconfigured firewall. This vulnerability allowed the malicious attacker to overwhelm the company’s network through a distributed denial of service (DDoS) attack. |
| Protect | The security team implemented the following safeguards to protect the identified items:<br>- A new firewall rule to limit the rate of incoming ICMP packets.<br>- An IDS/IPS system to filter out some ICMP traffic based on suspicious characteristics. |
| Detect | The security team implemented tools needed for detecting threats and attacks:<br>- Source IP address verification on the firewall to check for spoofed IP addresses on incoming ICMP packets.<br>- Network monitoring software to detect abnormal traffic patterns. |
| Respond | The security team has implemented a new firewall rule to limit rate of incoming ICMP packets, so if a flood of packets occurs those will be automatically rejected.<br>An IDS was also implemented to filter out suspicious traffic, so in the future it will be more likely for the packets to not even go through directly to the network.<br>Network Monitoring Software and Source IP verification were implemented to detect in time if ICMP were transfered on an abnormal traffic, so the team has more time in the future to respond an incident in case it happens. |
| Recover | The team recovered by blocking any incoming ICMP packet and shutting down all non-critical network services, while restoring critical networks services. After the attack ended and all the techniques were implemented, the block will be lifted and the traffic and services can resume their function.|
| Reflections/Notes | By applying good hardening techniques in the beginning nothing of this would have happen, so checking the systems and procedures in detail is a key action to do as a security analyst. |