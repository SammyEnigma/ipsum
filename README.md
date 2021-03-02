![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-03-02)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.20|tor-exit0-readme.dfri.se|10
51.77.135.89|ns31066279.ip-51-77-135.eu|9
171.25.193.77|tor-exit1-readme.dfri.se|9
171.25.193.78|tor-exit4-readme.dfri.se|9
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|8
185.220.102.244|185-220-102-244.torservers.net|8
185.220.102.245|185-220-102-245.torservers.net|8
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|8
162.247.74.74|wiebe.tor-exit.calyxinstitute.org|8
185.220.102.4|communityexit.torservers.net|8
198.144.121.93|-|8
64.113.32.29|tor.t-3.net|8
51.75.52.118|ns3130898.ip-51-75-52.eu|8
185.220.101.134|-|7
185.213.155.169|-|7
185.220.102.247|185-220-102-247.torservers.net|7
185.220.102.242|185-220-102-242.torservers.net|7
185.220.102.243|185-220-102-243.torservers.net|7
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|7
23.129.64.232|-|7
54.39.16.73|ns555166.ip-54-39-16.net|7
185.38.175.72|-|7
178.20.55.18|marcuse-2.nos-oignons.net|7
185.220.100.252|tor-exit-1.zbau.f3netze.de|7
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|7
185.130.44.108|tor-exit-se1.privex.cc|7
185.220.101.218|-|7
185.220.101.212|-|7
185.220.101.133|-|7
162.247.74.217|perry.fellwock.tor-exit.calyxinstitute.org|7
45.148.10.54|edc75.howacc.pro|7
23.129.64.227|-|7
23.129.64.228|-|7
51.89.153.65|ns3145235.ip-51-89-153.eu|7
51.75.144.43|ns3129517.ip-51-75-144.eu|7
185.56.80.65|onion.xor.sc|7
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|7
62.102.148.69|-|7
62.102.148.68|-|7
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|7
195.206.105.217|zrh-exit.privateinternetaccess.com|7
51.158.111.157|157-111-158-51.instances.scw.cloud|7
162.247.74.201|-|7
5.196.29.8|exit-node.kagaminesama.xyz|7
84.53.192.243|-|7
158.69.126.135|ns522384.ip-158-69-126.net|7
185.220.101.9|-|7
185.220.101.8|-|7
185.220.101.3|-|7
185.220.101.1|-|7
195.254.135.76|-|7
198.96.155.3|exit.tor.uwaterloo.ca|7
185.165.168.229|-|7
185.220.102.8|185-220-102-8.torservers.net|7
77.247.181.165|politkovskaja.torservers.net|7
77.247.181.163|lumumba.torservers.net|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
93.174.95.106|battery.census.shodan.io|7
185.220.103.7|anatkamm.tor-exit.calyxinstitute.org|7
171.25.193.25|tor-exit5-readme.dfri.se|7
176.10.99.200|accessnow.org|7
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|7
23.129.64.208|-|7
23.129.64.204|-|7
45.129.56.200|-|7
185.220.101.194|-|7
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|7
45.9.13.235|-|7
185.220.101.146|-|7
185.220.101.207|-|7
185.220.101.204|-|7
185.220.101.200|-|7
80.67.172.162|algrothendieck.nos-oignons.net|7
