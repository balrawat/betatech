---
layout: post
title: 'CentOS / Redhat : Configure CentOS as a Software Router with two interfaces'
date: '2013-06-18T16:35:00.006+05:30'
author: Balvinder Rawat
tags:
  - gateway
  - router
modified_time: '2014-01-07T12:51:11.878+05:30'
thumbnail: >-
  http://3.bp.blogspot.com/-peke76gt-wo/Uo7pDIYYeII/AAAAAAAAApo/3Teg6vx8BNU/s72-c/router.png
blogger_id: 'tag:blogger.com,1999:blog-6814921223515313000.post-7884711947305370494'
blogger_orig_url: 'https://www.linuxtechtips.com/2013/06/centos-redhat-configure-centos-as.html'
---
[![](http://3.bp.blogspot.com/-peke76gt-wo/Uo7pDIYYeII/AAAAAAAAApo/3Teg6vx8BNU/s1600/router.png)][1]

  

Linux can be easily configured to share an internet connection using iptables. All you need to have is, two network interface cards as follows:

  

a) Your internal (LAN) network connected via eth0 with static ip address 192.168.0.1

  

b) Your external WAN) network is connected via eth1 with static ip address 10.10.10.1  ( public IP provided by ISP )

Please note that interface eth1 may have public IP address or IP assigned by ISP. eth1 may be connected to a dedicated DSL / ADSL / WAN / Cable router:

Step # 1: Enable Packet Forwarding
----------------------------------

Login as the root user. Open /etc/sysctl.conf file

\# vi /etc/sysctl.conf

  

Add the following line to enable packet forwarding for IPv4:

net.ipv4.conf.default.forwarding=1

  

Save and close the file. Restart networking:

\# service network restart

  

Step # 2: Enable IP masquerading
--------------------------------

  

In Linux networking, Network Address Translation (NAT) or Network Masquerading (IP Masquerading) is a technique of transceiving network traffic through a router that involves re-writing the source and/or destination IP addresses and usually also the TCP/UDP port numbers of IP packets as they pass through. In short, IP masquerading is used to share the internet connection.

  

### Share internet connection

To share network connection via eth1, enter the following rule at command prompt (following useful for ppp0 or dial up connection):

  

  

\# service iptables stop

  

\# iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE

\# service iptables save

\# service iptables restart

  

Make sure Iptables runs on boot

  

\# chkconfig iptables on

  

  

Open your Windows / Mac / Linux computer networking GUI tool and point router IP to 192.168.0.1 (eth0 Linux IP). You also need to setup DNS IP such as 8.8.8.8 or to your local DNS server IP. You should now able to ping or browse the internet:

  

\# ping google.com

  

  

[1]: http://3.bp.blogspot.com/-peke76gt-wo/Uo7pDIYYeII/AAAAAAAAApo/3Teg6vx8BNU/s1600/router.png

