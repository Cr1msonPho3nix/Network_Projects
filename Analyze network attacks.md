# Scenario

You work as a security analyst for a travel agency that advertises sales and promotions on the company’s website. The employees of the company regularly access the company’s sales webpage to search for vacation packages their customers might like.

One afternoon, you receive an automated alert from your monitoring system indicating a problem with the web server. You attempt to visit the company’s website, but you receive a connection timeout error message in your browser.

You use a packet sniffer to capture data packets in transit to and from the web server. You notice a large number of TCP SYN requests coming from an unfamiliar IP address. The web server appears to be overwhelmed by the volume of incoming traffic and is losing its ability to respond to the abnormally large number of SYN requests. You suspect the server is under attack by a malicious actor.

You take the server offline temporarily so that the machine can recover and return to a normal operating status. You also configure the company’s firewall to block the IP address that was sending the abnormal number of SYN requests. You know that your IP blocking solution won’t last long, as an attacker can spoof other IP addresses to get around this block. You need to alert your manager about this problem quickly and discuss the next steps to stop this attacker and prevent this problem from happening again. You will need to be prepared to tell your boss about the type of attack you discovered and how it was affecting the web server and employees.

## 1. Identify the type of attack that may have caused this network interruption

One potential explanation for the website's connection timeout error message is:

- DDoS attack by sending a large number of SYN packet requests.

The logs show that:

- A large number of TCP SYN requests coming from unfamiliar IP address.

This event could be:

- SYN flood attack by a threat actor.

## 2. Explain how the attack is causing the website to malfunction

When website visitors try to establish a connection with the web server, a three-way handshake occurs using the TCP protocol. Explain the three steps of the handshake:

1. The client sends a SYN request to the Web server by sending a packet.
2. The Web server responds with another SYN/ACK packet. "ACK" means that the server ACKnowledge and confirms the connection.
3. The client sends back a ACK packet, establishing the connection with the server.

Explain what happens when a malicious actor sends a large number of SYN packets all at once:

- It causes the traffic to get sluggish or even cease it, due to the server to be overwhelmed with those packets.
  Explain what the logs indicate and how that affects the server:
- The logs indicate that a large number ot TCP SYN request are coming from an unfamiliar IP address, surely a threat actor. This overwhelms the server by the volume of incoming traffic and it loses the ability to respond to those request.
