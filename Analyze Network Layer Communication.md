# Scenario

You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website "yummyrecipesforme.com", and saw the error “destination port unreachable” after waiting for the page to load.

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error “destination port unreachable.” To troubleshoot the issue, you load your network analyzer tool, tcpdump, and attempt to load the webpage again. To load the webpage, your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name; this is part of the DNS protocol. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage The analyzer shows that when you send UDP packets to the DNS server, you receive ICMP packets containing the error message: “udp port 53 unreachable.”

![pack_snif_sample_1](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/pack_snif_sample_1.png)

In the log, you find the following information:

- Lines 1-2 show the initial outgoing request from your computer to the DNS server requesting the IP address of "yummyrecipesforme.com". This request is sent in a UDP packet.

- Lines 3-4 show the response to your UDP packet. In this case, the ICMP 203.0.113.2 line is the start of the error message indicating that the UDP packet was undeliverable to port 53 of the DNS server.

- The first sequence of numbers displayed, "13:24:32.192571" and "13:24:36.098564" of lines 1 and 3 are timestamps that indicate when the incident happened, so the times are 1:24 p.m., 32.192571 seconds and 1:24 p.m. and 36.098564 seconds respectively.

- After those sequences, you will find the source and destination IP addresses. In the first line, where the UDP packet travels from your browser to the DNS server, this information is displayed as: 192.51.100.15 > 203.0.113.2.domain, what means the address IP to the left (192.51.100.15) sent a request to the IP on the left (203.0.113.2.domain). For the ICMP error response, the source address is 203.0.113.2 and the destination is your computers IP address 192.51.100.15.

- After the source and destination IP addresses, there can be a number of additional details like the protocol, port number of the source, and flags. In the first line of the error log, the query identification number appears as: 35084. The + sign after the query identification number indicates there are flags associated with the UDP message. The "A?" indicates a flag associated with the DNS request for an A record, where an A record maps a domain name to an IP address. The third line displays the protocol of the response message to the browser: "ICMP," which is followed by an ICMP error message.

- The error message, "udp port 53 unreachable" is mentioned in the last line. Port 53 is a port for DNS service. The word "unreachable" in the message indicates the UDP message requesting an IP address for the domain "www.yummyrecipesforme.com" did not go through to the DNS server because no service was listening on the receiving DNS port.

- The remaining lines in the log indicate that ICMP packets were sent two more times, but the same delivery error was received both times.

Now that you have captured data packets using a network analyzer tool, it is your job to identify which network protocol and service were impacted by this incident. Then, you will need to write a follow-up report.

## 1. Provide a summary of the problem found in the DNS and ICMP traffic log.

The UDP protocol reveals that:

- Connections to the webpage "yummyrecipesforme.com" will return an error message due to not be able to reach the port 53. This could mean that the DNS server is down or not working properly.

This is based on the results of the network analysis, which show that the ICMP echo reply returned the error message:

- udp port 53 unreachable length 254

The port noted in the error message is used for:

- It is the standard port for DNS, used to query and request information from DNS servers while those returns the results to the client using the same port.

The most likely issue is:

- Server may be down or not working properly. Bad configuration or even a DOS attack could be some of the issues causing this malfunction.

## 2. Explain your analysis of the data and provide at least one cause of the incident.

Time incident occurred:

- First trying was at 13:24:32. Connection was tried 2 more times until 13:28:50, when last response was received with the same outcome.

Explain how the IT team became aware of the incident:

- Some clients were trying to access the website without any success, so they reported the situation to the team telling them a message on the web, "port unreachable", appeared.

Explain the actions taken by the IT department to investigate the incident:

- They used a packet sniffer called tcpdump to get a log with some valuable information. The message "port 53 unreachable" was an invaluable information due to that port be standarized for DNS connections.

Note key findings of the IT department's investigation (i.e., details related to the port affected, DNS server, etc.):

- "Port 53 unreachable" means that the DNS connection was involved. Also, some extra information like the port and flags were discovered in the log provided by the connection attempt.

Note a likely cause of the incident:

- A DOS attack could have disable the DNS server by flooding packets until it shutted down.
- Misconfiguration could be a possible cause, included firewall port blocking.
- If its working, just restart it (incredibly, works most of the time).
