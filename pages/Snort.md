## Snort (IDS/IPS)
	- **Snort** is a powerful IDS (Intrusion Detection System) and IPS (Intrusion Prevention System).
- ### Three main operational modes:
	- 1. **Packet Sniffing**:
		- Collects and displays network traffic, similar to Wireshark.
	- 2. **Packet Logging**:
		- Collects and logs network traffic to a file.
	- 3. **Network Intrusion Detection**:  
	   Analyzes packets and matches traffic against signatures to detect intrusions.
- ### Snort Rules
	- Snort rules are very similar to typical firewall rules.
- ### Snort Rule Syntax
	- **Structure**:
	  ```plaintext
	  Action | Protocol | Source Address/Source Port ->/Direction | Destination Address/Destination Port | Rule Options
	  ```
- *Snort has three primary uses: As a packet sniffer like tcpdump, as a packet logger — which is useful for network traffic debugging, or it can be used as a full-blown network intrusion prevention system*
-
- ## Logger Mode:
	- `snort -l` to log and alert to output directory
	- you can target specific packets in the log via the `-n number_here` parameter. this will get all packets up until that one
	- `-X` allows you to see more information (full packet details)
	- snort can use BPF (https://biot.com/capstats/bpf.html) as such ` sudo snort -r snort.log.1640048004  'tcp port 80'` great for filtering specific protocol and port
- ## IDS/IPDS Mode
	- `sudo snort -c /etc/snort/snort.conf -A console`: console mode provides fast style alerts on console screen
	- `sudo snort -c /etc/snort/snort.conf -A cmg`: basic header details with payload in the hex and text format. (has console mode on)
	- `sudo snort -c /etc/snort/snort.conf -A fast`: Fast mode provides alert messages, timestamps, and source and destination IP addresses. (no console)
	- `sudo snort -c /etc/snort/snort.conf -A full`: Full alert mode provides all possible information about the alert (no console output in this mode)
	- `sudo snort -c /etc/snort/snort.conf -A none` disables alerting but creates logs fopr traffic and a log file in binary format, still no console mode
- ## Investigating PCAPS with snort
	-