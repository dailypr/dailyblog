---
title: "Timeout issue reported from client"
date: 2020-03-28
tags: [aws,network,troubleshooting]
---

# Issue

```
[error] proxy: pass request body failed to xx.xx.xx.xx:443 (xxxxxxxxx.com) from xx.xx.xx.xx
[Fri Mar 27 04:32:38 2020] [error] (502)Unknown error 502: proxy: pass request body failed to xx.xx.xx.xx:443 (xxxxxxxxx.com)
[Fri Mar 27 04:32:38 2020] [error] [client xx.xx.xx.xx] proxy: Error during SSL Handshake with remote server 
```

# Troubleshooting

1. DNS lookup of ALB produces only 2 current IP addresses  

```
$ dig xxxxx alb dns xxxxx  +short
xx.xx.xx.xx
xx.xx.xx.xx
```

2. Contact AWS Support Center in order to get ALB node addresses, and had the answer below  

```
Issued IP address was removed by the ELB controller from DNS since ...., 
in other words your client is trying to ssl handshake to an IP that is not currently in service. 
```

3. Need to remember  

```
Please note that the 4 IPs you shared: xx,xx,xx,xx , xx.xx.xx.xx , xx.xx.xx.xx  , xx.xx.xx.xx , 
are stable IPs that the ELB can use if it needs to scale, 
this doesn't mean that all 6 IPs are always in use,  <---------------
this just means that if the ELB needs an IP it would pick from that pool of 6 IPs.
```

4. Check with client team  

```
I suspect that your clients either have bad dns behaviour (i.e cahing dns ips for long/not respecting the ttl) or they have hardcoded DNS values (e.g in the /etc/hosts file) or they have hardcoded IP addresses. 
```

a) Get your client to do a dns lookup from the ssl failing maching and see the IP address returned, use the below:   

`$ dig xxx alb dns address xxxxx  +short`  

b) If a) above shows the 2 current running ELB IPs then can you get your client to run a packet capture when trying to do the ssl handshake ? Use the below:  

`sudo  tcpdump host {dns name used to reach alb} and port 443 -w ssl.pcap`  

(Example: sudo  tcpdump host google.com and port 443 -w ssl.pcap)  
