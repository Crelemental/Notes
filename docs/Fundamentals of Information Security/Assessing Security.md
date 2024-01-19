
A vulnerability assessment is a process that uses a specially designed tool to scan for vulnerabilities. Qualys and Nessus. 

Start by mapping your environment so you know what devices are present on your network. Most vuln scanning tools allow you to create such a map, or you can import info from say Nmap. 

Active discovery involves a process similar to the one used to map a network; you go IP by IP and interrogate each to see whether anything responds. You can restrict these updates to portions of the network you know to contain devices. 
You can also use passive scanning techniques to discover devices on the network. You can place a device on network choke points to eavesdrop on the traffic, allowing you to discover the devices that talk on the network.

Unauthenticated Scans dont require any credentials for the host you're scanning or any access other than network connectivity to the host.

Authenticated Scans are one that conduct using a valid set of credentials, generally administrative, for the system being scanned. It allows you to collect internal info, such as what software is installed and the contents of configuration files (and much more). This give you a considerably more thorough view of the device and its potential vulnerabilities than from the outside. 

Agented Scans provide a means to get around the downside of authenticated scans. An agent is a piece of software installed on each host. It runs as though it were a user on the system, authenticated, therefore no need to maintain a separate set of credentials on the device.

Application Scanning is specific to web technologies and vulnerabilities, and can search considerably more deeply in the application for issues than a scanner intended strictly for hosts would be able to. IE Burp Suite

![[Pasted image 20231008163947.png]]

![[Pasted image 20231008164114.png]]

![[Pasted image 20231008164244.png]]

![[Pasted image 20231008164419.png]]

![[Pasted image 20231008164754.png]]
#ITSec