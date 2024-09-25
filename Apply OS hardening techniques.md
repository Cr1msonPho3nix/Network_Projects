# Scenario
You are a cybersecurity analyst for yummyrecipesforme.com, a website that sells recipes and cookbooks. A former employee has decided to lure users to a fake website with malware.

The baker executed a brute force attack to gain access to the web host. They repeatedly entered several known default passwords for the administrative account until they correctly guessed the right one. After they obtained the login credentials, they were able to access the admin panel and change the website’s source code. They embedded a javascript function in the source code that prompted visitors to download and run a file upon visiting the website. After embedding the malware, the baker changed the password to the administrative account. When customers download the file, they are redirected to a fake version of the website that contains the malware.

Several hours after the attack, multiple customers emailed yummyrecipesforme’s helpdesk. They complained that the company’s website had prompted them to download a file to access free recipes. The customers claimed that, after running the file, the address of the website changed and their personal computers began running more slowly.

In response to this incident, the website owner tries to log in to the admin panel but is unable to, so they reach out to the website hosting provider. You and other cybersecurity analysts are tasked with investigating this security event.

To address the incident, you create a sandbox environment to observe the suspicious website behavior. You run the network protocol analyzer tcpdump, then type in the URL for the website, yummyrecipesforme.com. As soon as the website loads, you are prompted to download an executable file to update your browser. You accept the download and allow the file to run. You then observe that your browser redirects you to a different URL, greatrecipesforme.com, which contains the malware.

The logs show the following process:

- The browser initiates a DNS request: It requests the IP address of the yummyrecipesforme.com URL from the DNS server.
- The DNS replies with the correct IP address.
- The browser initiates an HTTP request: It requests the yummyrecipesforme.com webpage using the IP address sent by the DNS server.
- The browser initiates the download of the malware.
- The browser initiates a DNS request for greatrecipesforme.com.
- The DNS server responds with the IP address for greatrecipesforme.com.
- The browser initiates an HTTP request to the IP address for greatrecipesforme.com.

A senior analyst confirms that the website was compromised. The analyst checks the source code for the website. They notice that javascript code had been added to prompt website visitors to download an executable file. Analysis of the downloaded file found a script that redirects the visitors’ browsers from yummyrecipesforme.com to greatrecipesforme.com.

The cybersecurity team reports that the web server was impacted by a brute force attack. The disgruntled baker was able to guess the password easily because the admin password was still set to the default password. Additionally, there were no controls in place to prevent a brute force attack.

Your job is to document the incident in detail, including identifying the network protocols used to establish the connection between the user and the website. You should also recommend a security action to take to prevent brute force attacks in the future.

Traffic Log:
| Traffic Log |
| ----------- |
| 14:18:32.192571 IP your.machine.52444 > dns.google.domain: 35084+ A? yummyrecipesforme.com. (24)
14:18:32.204388 IP dns.google.domain > your.machine.52444: 35084 1/0/0 A 203.0.113.22 (40) |
| 14:18:36.786501 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [S], seq 2873951608, win 65495, options [mss 65495,sackOK,TS val 3302576859 ecr 0,nop,wscale 7], length 0 |
| 14:18:36.786517 IP yummyrecipesforme.com.http > your.machine.36086: Flags [S.], seq 3984334959, ack 2873951609, win 65483, options [mss 65495,sackOK,TS val 3302576859 ecr 3302576859,nop,wscale 7], length 0 |
| 14:18:36.786529 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [.], ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 0 |
| 14:18:36.786589 IP your.machine.36086 > yummyrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 73: HTTP: GET / HTTP/1.1
| 14:18:36.786595 IP yummyrecipesforme.com.http > your.machine.36086: Flags [.], ack 74, win 512, options [nop,nop,TS val 3302576859 ecr 3302576859], length 0 |
| ...<a lot of traffic on the port 80>... |
| 14:20:32.192571 IP your.machine.52444 > dns.google.domain: 21899+ A? greatrecipesforme.com. (24) |
| 14:20:32.204388 IP dns.google.domain > your.machine.52444: 21899 1/0/0 A 192.0.2.17 (40) |
| 14:25:29.576493 IP your.machine.56378 > greatrecipesforme.com.http: Flags [S], seq 1020702883, win 65495, options [mss 65495,sackOK,TS val 3302989649 ecr 0,nop,wscale 7], length 0 |
| 14:25:29.576510 IP greatrecipesforme.com.http > your.machine.56378: Flags [S.], seq 1993648018, ack 1020702884, win 65483, options [mss 65495,sackOK,TS val 3302989649 ecr 3302989649,nop,wscale 7], length 0 |
| 14:25:29.576524 IP your.machine.56378 > greatrecipesforme.com.http: Flags [.], ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 0 |
| 14:25:29.576590 IP your.machine.56378 > greatrecipesforme.com.http: Flags [P.], seq 1:74, ack 1, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 73: HTTP: GET / HTTP/1.1 |
| 14:25:29.576597 IP greatrecipesforme.com.http > your.machine.56378: Flags [.], ack 74, win 512, options [nop,nop,TS val 3302989649 ecr 3302989649], length 0 |
| ...<a lot of traffic on the port 80>... |

## Security Incident Report
### 1: Identify the network protocol involved in the incident
The network protocol involved in the incident is HTTP, because the traffic on port 80 was high. Port 80 has a standarized use for HTTP.

### 2: Document the incident
#### Security Incident Report
- Incident Report Number: IR-2024-001
- Overview
  - Multiple clients emailed helpdesk complaining slow performance on their computers after downloading a file prompted by the Website.
  - The website owner tries to log in to the admin panel but is unable to. The team run a connection to the website while using a protocol analyzer. After loading we were prompted to download an executable file to update our browser, which after been executed the browser was redirected to a different URL, "greatrecipesforme.com", which contains the malware.
  - After checking the packet analyzer log, a senior analyst confirms that the website was compromised, possibly by a brute for attack directed to the owners account.
- Date and time: Incident were first noticed this morning, tests on network connectivity were done at **14:18**.
- Affected systems: We can't asses the systems affected by the malware downloaded by the clients, but we can assure the account of the owner and the website were compromised.
- Summary of actions taken: Modified owner's account password, installed some new strong requirements for it and cleaned the website of any inyected code. Website no longer ask to download a file and works as intended.

### 3: Recommend a remediation for brute force attacks
There are a few techniques that can be implemented to harden security and prevent a brute force attack, such as:
- Implement Strong Password Policies: Minimum password length, policies that require users to regularly change their passwords or enforcing complexity on requirements (such as including a mix of uppercase, lowercase, numbers, and special characters) can strengthen the security.
- Multi-Factor Authentication (MFA): Ask the user to verify itself with not only a password, but a phone message for example.
- Limiting attempts: If the user gets the password wrong a "x" amount of times, access can be blocked temporarily to prevent threat actors to keep trying.
Those are some of the most common techniques uses, but others like IP Blacklisting, configuring the Web Application Firewall or even set a Honeypot to distract attackers and give security teams more time to respond, are used by some security teams.