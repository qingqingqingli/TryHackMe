## Table of content

### Introduction

- The more knowledge you have about a target system / network, the more options you have available. When you are given an IP, you need to get an idea of the "landscape" that you're attacking. It means that you need to establish which services are running on the targets.

- **Port scanning**. The first stage in establishing the landscape is called port scanning. ```nmap``` can be used to perform many different kinds of port scan.  

- nmap will connect to each port of the target in turn. Depending on how the port responds, it can be determined as being open, closed, or filtered (usually by a firewall). Once we know which ports are open, we can then look at enumerating which services are running on each port – either manually, or more commonly using nmap.
