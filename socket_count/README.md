Plugin for Monitoring the TCP/UDP Port counts
==============================================

### PreRequisites

- Plugin Uses "ss -s" command to get the tcp / udp count	
	
- Plugin Uses command line json parser 'jq' to provide the output in json
      To install this utitlity
      For Ubuntu , Debian use the command -> apt-get install jq
      For Redhat , Centos use the comman -> yum install jq


### Plugin installation
---
##### Linux 

- Create a directory "socket_count" under Site24x7 Linux Agent plugin directory - /opt/site24x7/monagent/plugins/socket_count

- Download the file "socket_count.py" and place it under the "socket_count" directory
  
  wget https://raw.githubusercontent.com/site24x7/plugins/master/socket_count/socket_count.sh
	
  The agent will automatically execute the plugin within five minutes and send performance data to the Site24x7 data center.


### Metrics Captured
---

tcp_total - total tcp connections

udp_total - total udp connections

tcp_ip - total tcp connections ( ipv4 )

tcp_ipv6 - total tcp connections ( ipv6 )

udp_ip - total udp connections ( ipv4 )

udp_ipv6 - total udp connections ( ipv6 )