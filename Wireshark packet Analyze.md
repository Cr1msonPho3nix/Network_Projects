# Scenario
In this scenario, you’re a security analyst investigating traffic to a website.

You’ll analyze a network packet capture file that contains traffic data related to a user connecting to an internet site. The ability to filter network traffic using packet sniffers to gather relevant information is an essential skill as a security analyst.

You must filter the data in order to:
- Identify the source and destination IP addresses involved in this web browsing session,
- Examine the protocols that are used when the user makes the connection to the website, and
- Analyze some of the data packets to identify the type of information sent and received by the systems that connect to each other when the network data is captured.

## 1. Apply a basic Wireshark filter and inspect a packet
- Search for the specific IP address: 142.250.1.139
![wireshark_1](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/.png)<br><br>
- Double-click on the first packet with "TCP" protocol gives some information about it, which is its destination port?
![wireshark_2](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/.png)<br><br>

## 2. Use filters to select packets
- Search for any packet related to the specific MAC address: 42:01:ac:15:e0:02. Show the first packet protocol and "Time to Live" information.
![wireshark_3](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/.png)<br><br>

## 3. Use filters to explore DNS packets
- Use filters to select and examine DNS traffic (DNS traffic uses UDP port 53)
![wireshark_3](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/.png)<br><br>
