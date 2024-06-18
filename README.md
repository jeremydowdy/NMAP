# NMAP

### What is Nmap?

Nmap (Network Mapper) is a widely used open-source network scanning tool that was originally developed to discover hosts and services on a computer network, thus creating a "map" of the network topology. It allows users to audit and explore network security, identify open ports, detect security vulnerabilities, and conduct network inventory.

#### History:

- **Creation**: Nmap was created by Gordon Lyon, also known by his pseudonym "Fyodor," in 1997. Lyon developed Nmap as a tool to assist in network security auditing and exploration. Initially, Nmap was released under the GNU General Public License (GPL) as free software.

- **Evolution**: Over the years, Nmap has evolved significantly in functionality and capability. It has become a standard tool used by network administrators, security professionals, penetration testers, and individuals interested in network exploration.

#### Features:

Nmap is known for its powerful features, including:

- **Port scanning**: Ability to scan a range of ports on a target machine to discover open ports and services.
- **Version detection**: Ability to determine the version numbers and details of services running on open ports.
- **OS detection**: Capability to infer the operating system of the target host based on network behaviors and responses.
- **Scriptable interaction**: Nmap supports scripting engine (Nmap Scripting Engine - NSE) that allows users to write and execute scripts to automate tasks, perform advanced network discovery, and detect vulnerabilities.
- **Performance**: Nmap is designed to be fast and efficient, capable of scanning large networks swiftly while providing detailed information about hosts and services.

#### Uses:

- **Network Security**: Nmap is extensively used for network security assessments, vulnerability scanning, and penetration testing. Security professionals use Nmap to identify potential vulnerabilities in systems and networks before malicious actors can exploit them.

- **Network Administration**: Network administrators use Nmap to monitor network health, inventory network resources, and troubleshoot connectivity issues by identifying active hosts and services.

- **Research and Education**: Nmap is also used in academic research, security training programs, and educational courses to teach network security principles, techniques, and methodologies.

#### Legal and Ethical Considerations:

- **Authorization**: It is important to note that using Nmap or any network scanning tool without proper authorization can be illegal and may violate laws related to unauthorized access to computer systems.

- **Ethics**: Ethical considerations are crucial when using Nmap. Users should obtain permission before scanning networks or systems that they do not own or administer. Unauthorized scanning can disrupt services, violate privacy, and lead to legal consequences.


**nmap is a very powerful tool that has a lot of uses and capabilities. These uses and capabilites do not come right out of the terminal, the user must have knowledge and scope to correctly utilize nmap to their advantage.**

Here is a default scan that I find can be used in a lot of cases, but you must utilize techniques that suit the needs of your scan and what you are trying to discover. 
``` 
nmap -sV -sC --scripts vuln -a <target IP>
```
Here's the explanation for each component of that particular command:

- **nmap**: The command-line tool used for network exploration and security auditing.
- **-sV**: Enables version detection. Nmap will attempt to determine versions of the services running on open ports by interrogating them.
- **-sC**: Executes default scripts against the target. These scripts are useful for gathering additional information about the services running on the target.
- **--script vuln**: Specifies that the script named `vuln` (or scripts related to vulnerability detection) should be run. Nmap has built-in scripts that can detect various vulnerabilities in services.
- **-a**: Enables aggressive scanning options. It enables OS detection, version detection, script scanning, and traceroute.
- **<target IP>**: Replace `<target IP>` with the IP address of the target machine you want to scan.

Your nmap scans should be **context dependent** and you should utilize techniques that will best suit your needs. 

**DO NOT SCAN ANY NETWORK WITHOUT WRITTEN EXPLICIT PERMISSION**

_Running an Nmap scan itself is not inherently illegal, but the legality depends on various factors including the jurisdiction you are in, the target you are scanning, and your intent behind the scan._

Here are some key points to consider:

- **Authorization:** Scanning a network or system without proper authorization is generally illegal. If you do not have permission from the owner of the network or system, conducting a scan can be considered unauthorized access, which is a violation of laws such as the Computer Fraud and Abuse Act (CFAA) in the United States.

- **Intent:** The legality also depends on your intent. If you are conducting a scan for legitimate security testing, research, or network administration purposes with explicit permission from the owner, it is generally legal. However, scanning with malicious intent, such as attempting to exploit vulnerabilities or disrupt services, is illegal and can result in severe legal consequences.

- **Privacy and Data Protection Laws:** In many jurisdictions, there are laws governing the protection of personal data and privacy. Conducting scans that collect personally identifiable information without consent may violate these laws.

- **Penetration Testing:** Organizations often conduct authorized penetration tests, including using tools like Nmap, to identify vulnerabilities in their own systems. Such activities are legal when authorized and conducted within the boundaries set by the organization.

- **Federal Crime:** Under certain circumstances, unauthorized scanning could potentially lead to federal charges, especially if it involves critical infrastructure, government systems, or if it causes significant damage or disruption.

With that out of the way lets get into some basic scanning techniques
### Basic Scanning Techniques

- Scan a single target: `nmap [target]`
- Scan multiple targets: `nmap [target1,target2,etc]`
- Scan a list of targets: `nmap -iL [list.txt]`
- Scan a range of hosts: `nmap [range of IP addresses]`
- Scan an entire subnet: `nmap [IP address/cdir]`
- Scan random hosts: `nmap -iR [number]`
- Excluding targets from a scan: `nmap [targets] –exclude [targets]`
- Excluding targets using a list: `nmap [targets] –excludefile [list.txt]`
- Perform an aggressive scan: `nmap -A [target]`
- Scan an IPv6 target: `nmap -6 [target]`

### Discovery Options

- Perform a ping scan only: `nmap -sP [target]`
- Don’t ping: `nmap -PN [target]`
- TCP SYN Ping: `nmap -PS [target]`
- TCP ACK ping: `nmap -PA [target]`
- UDP ping: `nmap -PU [target]`
- SCTP Init Ping: `nmap -PY [target]`
- ICMP echo ping: `nmap -PE [target]`
- ICMP Timestamp ping: `nmap -PP [target]`
- ICMP address mask ping: `nmap -PM [target]`
- IP protocol ping: `nmap -PO [target]`
- ARP ping: `nmap -PR [target]`
- Traceroute: `nmap –traceroute [target]`
- Force reverse DNS resolution: `nmap -R [target]`
- Disable reverse DNS resolution: `nmap -n [target]`
- Alternative DNS lookup: `nmap –system-dns [target]`
- Manually specify DNS servers: `nmap –dns-servers [servers] [target]`
- Create a host list: `nmap -sL [targets]`

### Firewall Evasion Techniques

- Fragment packets: `nmap -f [target]`
- Specify a specific MTU: `nmap –mtu [MTU] [target]`
- Use a decoy: `nmap -D RND: [number] [target]`
- Idle zombie scan: `nmap -sI [zombie] [target]`
- Manually specify a source port: `nmap –source-port [port] [target]`
- Append random data: `nmap –data-length [size] [target]`
- Randomize target scan order: `nmap –randomize-hosts [target]`
- Spoof MAC Address: `nmap –spoof-mac [MAC|0|vendor] [target]`
- Send bad checksums: `nmap –badsum [target]`

### Version Detection

- Operating system detection: `nmap -O [target]`
- Attempt to guess an unknown: `nmap -O –osscan-guess [target]`
- Service version detection: `nmap -sV [target]`
- Troubleshooting version scans: `nmap -sV –version-trace [target]`
- Perform an RPC scan: `nmap -sR [target]`

### Output Options

- Save output to a text file: `nmap -oN [scan.txt] [target]`
- Save output to an XML file: `nmap -oX [scan.xml] [target]`
- Grepable output: `nmap -oG [scan.txt] [target]`
- Output all supported file types: `nmap -oA [path/filename] [target]`
- Periodically display statistics: `nmap –stats-every [time] [target]`
- 133t output: `nmap -oS [scan.txt] [target]`

### Ndiff

- Comparison using Ndiff: `ndiff [scan1.xml] [scan2.xml]`
- Ndiff verbose mode: `ndiff -v [scan1.xml] [scan2.xml]`
- XML output mode: `ndiff –xml [scan1.xml] [scan2.xml]`

### Nmap Scripting Engine

- Execute individual scripts: `nmap –script [script.nse] [target]`
- Execute multiple scripts: `nmap –script [expression] [target]`
- Execute scripts by category: `nmap –script [cat] [target]`
- Execute multiple scripts categories: `nmap –script [cat1,cat2, etc]`
- Troubleshoot scripts: `nmap –script [script] –script-trace [target]`
- Update the script database: `nmap –script-updatedb`

### Script Categories:
- **all**: This category includes all available scripts, covering a wide range of functionalities.

- **auth**: Scripts in this category are related to authentication mechanisms, such as checking for default or weak credentials.

- **default**: These scripts are included in the default set of scripts that Nmap runs during a scan. They cover general tasks like service enumeration and version detection.

- **discovery**: Scripts in this category are focused on discovering information about hosts, networks, or services. This can include things like detecting hosts on a network or identifying services running on specific ports.

- **external**: Scripts in this category are meant to be executed externally. They may interact with external services or databases to gather additional information.

- **intrusive**: These scripts are more aggressive and may have a higher chance of causing disruption or being detected by intrusion detection systems (IDS). They are designed for thorough testing but should be used with caution.

- **malware**: Scripts in this category are related to detecting or analyzing malware presence or behavior on target systems.

- **safe**: These scripts are considered safe to run and are less likely to cause disruptions or trigger security alerts.

- **vuln**: Scripts in this category focus on vulnerability detection. They check for known vulnerabilities in services or applications running on target systems.

When using Nmap's scripting engine (`--script` option), specifying a script category helps narrow down the selection of scripts to those specifically designed for that category's purpose. For example, `nmap --script vuln [target]` would run only scripts categorized under "vuln," which are designed to detect vulnerabilities in target systems.

