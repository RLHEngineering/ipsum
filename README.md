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

Wall of Shame (2021-02-11)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.78|tor-exit4-readme.dfri.se|10
171.25.193.20|tor-exit0-readme.dfri.se|9
185.220.101.194|-|9
162.247.72.199|jaffer.tor-exit.calyxinstitute.org|8
46.148.20.25|druid.vps|8
51.77.135.89|ns31066279.ip-51-77-135.eu|8
195.206.105.217|zrh-exit.privateinternetaccess.com|8
171.25.193.77|tor-exit1-readme.dfri.se|8
185.174.43.6|-|8
185.220.101.22|-|8
171.25.193.25|tor-exit5-readme.dfri.se|8
91.192.103.26|-|8
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|8
80.82.77.33|sky.census.shodan.io|7
185.213.155.169|-|7
185.220.102.244|185-220-102-244.torservers.net|7
185.220.102.241|185-220-102-241.torservers.net|7
185.220.102.243|185-220-102-243.torservers.net|7
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|7
185.220.102.249|tor-exit-relay-3.anonymizing-proxy.digitalcourage.de|7
217.182.192.217|ns3073700.ip-217-182-192.eu|7
178.20.55.18|marcuse-2.nos-oignons.net|7
104.244.77.95|-|7
94.230.208.147|tor3e1.digitale-gesellschaft.ch|7
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|7
192.42.116.13|this-is-a-tor-exit-node-hviv113.hviv.nl|7
185.220.101.215|-|7
141.98.80.69|-|7
162.247.74.27|turing.tor-exit.calyxinstitute.org|7
185.220.102.6|185-220-102-6.torservers.net|7
185.220.102.7|185-220-102-7.torservers.net|7
207.244.70.35|-|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
161.35.40.167|-|7
178.165.72.177|178-165-72-177-kh.maxnet.ua|7
80.67.172.162|algrothendieck.nos-oignons.net|7
62.102.148.68|-|7
185.220.100.247|tor-exit-8.zbau.f3netze.de|7
192.42.116.27|this-is-a-tor-exit-node-hviv127.hviv.nl|7
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|7
217.170.206.146|-|7
5.196.29.8|exit-node.kagaminesama.xyz|7
89.234.157.254|marylou.nos-oignons.net|7
185.191.124.152|-|7
185.191.124.151|-|7
91.192.103.10|-|7
185.220.101.9|-|7
185.220.101.8|-|7
185.220.101.7|-|7
185.220.101.1|-|7
80.82.77.139|dojo.census.shodan.io|7
185.174.43.8|-|7
107.189.10.246|-|7
185.165.168.229|-|7
185.220.101.24|-|7
185.220.102.4|communityexit.torservers.net|7
185.220.102.8|185-220-102-8.torservers.net|7
23.129.64.213|-|7
198.144.121.93|-|7
77.247.181.165|politkovskaja.torservers.net|7
93.174.95.106|battery.census.shodan.io|7
185.220.103.7|anatkamm.tor-exit.calyxinstitute.org|7
95.128.43.164|exit-1.fr.tor.aquaray.com|7
87.118.116.103|ns.tor-exit-4.artikel5ev.de|7
185.220.101.207|-|7
185.220.102.250|tor-exit-relay-4.anonymizing-proxy.digitalcourage.de|7
185.220.101.203|-|7
