## Table of content

### Introduction

- The more knowledge you have about a target system / network, the more options you have available. When you are given an IP, you need to get an idea of the "landscape" that you're attacking. It means that you need to establish which services are running on the targets.

- **Port scanning**. The first stage in establishing the landscape is called port scanning. ```nmap``` can be used to perform many different kinds of port scan.  

- nmap will connect to each port of the target in turn. Depending on how the port responds, it can be determined as being open, closed, or filtered (usually by a firewall). Once we know which ports are open, we can then look at enumerating which services are running on each port – either manually, or more commonly using nmap.

### TCP Connect Scans

- To understand TCP Connect scans (```-sT```), it's important that you're comfortable with the TCP three-way handshake.
  
- A TCP Connect scan works by performing the three-way handshake with each target port in turn. In other words, Nmap tries to connect to each specified TCP port, and determines whether the service is open by the response it receives.

[![handshake](https://github.com/qingqingqingli/TryHackMe/blob/main/images/threeway_handshake.png)](https://github.com/qingqingqingli/TryHackMe/blob/main/beginner%20path/4_nmap.md)

- **CLOSED port**. If Nmap sends a TCP request with the SYN flag set to a closed port, the target server will respond with a TCP packet with the RST (Reset) flag set. By this response, Nmap can establish that the port is closed.

- **OPEN port**. The target will respond with a TCP packet with the SYN/ACK flags set. Nmap then marks this port as being open (and completes the handshake by sending back a TCP packet with ACK set).

- **FILTERED port**. Many firewalls are configured to simply drop incoming packets. Nmap sends a TCP SYN request, and ```receives nothing back```. This indicates that the port is being protected by a firewall and thus the port is considered to be filtered.

- RFC 793 defines defines the appropriate behaviour for the TCP protocol.

### SYN Scans

- As with TCP scans, SYN scans (```-sS```) are used to scan the TCP port-range of a target or targets; however, the two scan types work slightly differently. SYN scans are sometimes referred to as ```Half-open``` scans, or ```Stealth``` scans.

- SYN scans are the default scans used by Nmap if run with sudo permissions. If run without sudo permissions, Nmap defaults to the TCP Connect scan

### UDP Scans

- **Unlike TCP, UDP connections are stateless**. This means that, rather than initiating a connection with a back-and-forth "handshake", UDP connections rely on sending packets to a target port and essentially hoping that they make it. This makes UDP superb for connections which rely on speed over quality (e.g. video sharing), but the lack of acknowledgement makes UDP significantly more difficult (and much slower) to scan. The switch for an Nmap UDP scan is (```-sU```)

- When a packet is sent to an open UDP port, there should be no response. When this happens, Nmap refers to the port as being ```open|filtered```. In other words, it suspects that the port is open, but it could be firewalled. If it gets a UDP response (which is very unusual), then the port is marked as open. More commonly there is no response, in which case the request is sent a second time as a double-check. If there is still no response then the port is marked ```open|filtered``` and Nmap moves on.

- When a packet is sent to a closed UDP port, the target should respond with an ICMP (ping) (Internet Control Message Protocol) packet containing a message that the port is unreachable. This clearly identifies closed ports, which Nmap marks as such and moves on.

- Due to this difficulty in identifying whether a UDP port is actually open, UDP scans tend to be incredibly slow in comparison to the various TCP scans (in the region of 20 minutes to scan the first 1000 ports, with a good connection). For this reason it's usually good practice to run an Nmap scan with ```--top-ports <number>``` enabled. For example, scanning with  nmap -sU ```--top-ports 20 <target>```. Will scan the top 20 most commonly used UDP ports, resulting in a much more acceptable scan time.

### NULL, FIN and Xmas (for firewall evasion)

- All three are interlinked and are used primarily as they tend to be even stealthier, relatively speaking, than a SYN "stealth" scan. 

- It is very similar to that of a UDP scan. If the port is open then there is no response to the malformed packet. Unfortunately (as with open UDP ports), that is also an expected behaviour if the port is protected by a firewall, so NULL, FIN and Xmas scans will only ever identify ports as being open|filtered, closed, or filtered. If a port is identified as filtered with one of these scans then it is usually because the target has responded with an ICMP unreachable packet.

### ICMP Network Scanning

- One way to do this is by using Nmap to perform a so called "ping sweep". This is exactly as the name suggests: Nmap sends an ICMP packet to each possible IP address for the specified network. When it receives a response, it marks the IP address that responded as being alive. For reasons we'll see in a later task, this is not always accurate; however, it can provide something of a baseline and thus is worth covering.

### NSE Scripts

- The Nmap Scripting Engine (NSE) is an incredibly powerful addition to Nmap, extending its functionality quite considerably. NSE Scripts are written in the Lua programming language, and can be used to do a variety of things: from scanning for vulnerabilities, to automating exploits for them. The NSE is particularly useful for reconnaisance, however, it is well worth bearing in mind how extensive the script library is.

- ```--script=xx``` to run with a script. Use ```--script-args```

- We have two options for this, which should ideally be used in conjunction with each other. The first is the page on the Nmap website (mentioned in the previous task) which contains a list of all official scripts. The second is the local storage on your attacking machine. Nmap stores its scripts on Linux at ```/usr/share/nmap/scripts```. All of the NSE scripts are stored in this directory by default -- this is where Nmap looks for scripts when you specify them. 