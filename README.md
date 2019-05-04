# CryptoCachedDNS
An Ansible playbook to deploy many DNS Cache server with Bind9 backend and DNSCrypt-Proxy

build status: [![Build Status](https://travis-ci.org/danitfk/CryptoCachedDNS.svg?branch=master)](https://travis-ci.org/danitfk/CryptoCachedDNS)

## DNSCrypt + Bind9
With this playbook you can have a bind9 as you DNS Server with DNSCrypt backend (forwarder) to **secure and protect your DNS queries**.

**Without CryptoCachedDNS**
![alt Unsecure DNS](https://github.com/danitfk/CryptoCachedDNS/blob/master/screenshots/without.jpg?raw=true)


**With CryptoCachedDNS**
![alt Secure DNS](https://github.com/danitfk/CryptoCachedDNS/blob/master/screenshots/with.jpg?raw=true)


## Use Cases:

- Small-Medium Business offices
- Private networks

## How to run it?

You can use this sample inventory file:

```

[dns-server]
192.168.1.20	public_ip=192.168.1.20
192.168.1.21	public_ip=192.168.1.21

```

With this playbook:

```

---
- hosts: dns-server
  roles:
    - { role: CryptoCachedDNS }


```

then run the ansible command:

```

ansible-playbook -i inventory main.yml  --become

```

## Tips and Tricks

Before running the playbook, Change the variables properly:

./CryptoCachedDNS/defaults/main.yml

```
---
trusted_network: 127.0.0.1; 192.168.0.0/16; 172.16.0.0/12;
max_cache: 1800
max_ncache: 1800


```

