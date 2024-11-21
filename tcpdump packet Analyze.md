# Scenario
You’re a network analyst who needs to use tcpdump to capture and analyze live network traffic from a Linux virtual machine.

Your Linux user's home directory contains a sample packet capture file that you will use at the end of the lab to answer a few questions about the network traffic that it contains.

## 1. Identify network interfaces
- Identify the network interfaces that can be used to capture network packet data, then identify the interface options available for packet capture.<br>
![wireshark_1](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/TCPDUMP%20packet%20Analyzer%201/1.1.Network_interfaces.PNG)<br><br>

## 2. Inspect the network traffic of a network interface with tcpdump
- Filter five live network packet data from the eth0 interface with tcpdump.
![wireshark_1](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/TCPDUMP%20packet%20Analyzer%201/2.1.Filter_5_packets.PNG)<br><br>
- This command will run tcpdump with the following options:
  - i eth0: Capture data specifically from the eth0 interface.
  - v: Display detailed packet data.
  - c5: Capture 5 packets of data.

## 3. Capture network traffic with tcpdump
- Capture packet data into a file called capture.pcap. Generate some HTTP traffic and check if the packet has been captured.
![wireshark_1](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/TCPDUMP%20packet%20Analyzer%201/3.1.stored_packet_capture.PNG)<br><br>
- This command will run tcpdump in the background with the following options:
  - i eth0: Capture data from the eth0 interface.
  - nn: Do not attempt to resolve IP addresses or ports to names.This is best practice from a security perspective, as the lookup data may not be valid. It also prevents malicious actors from being alerted to an investigation.
  - c9: Capture 9 packets of data and then exit.
  - port 80: Filter only port 80 traffic. This is the default HTTP port.
  - w capture.pcap: Save the captured data to the named file.
  - &: This is an instruction to the Bash shell to run the command in the background.

  ## 4. Filter the captured packet data
  - Filter the packet header data from the capture.pcap capture file.
![wireshark_1](https://github.com/Cr1msonPho3nix/Network_Projects/blob/main/img/TCPDUMP%20packet%20Analyzer%201/4.1.Header_filter.PNG)<br><br>
