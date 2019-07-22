Add following to you server config file:

```
---
- hosts: fqdn.your.host
  roles:
    - { name: create_hood, tags: create_hood }
  vars_files:
    - vars/all_hosts.yml
  vars:
    - hood_data:
      - hoodname: "YOUR_HOOD_NAME"
        ipv4:
          ip: "10.83.xxx.1"
          net: 24
          sub: "10.83.xxx.0"
        ipv6:
          fff:
            ip: "fd43:5602:28bd:xxxx::1"
            net: 64
            sub: "fd43:5602:28bd:xxxx::"
          pub: ### OPTIONAL
            ip: "2a0c:b642:1030:xxxx::1"
            net: 64
            sub: "2a0c:b642:1030:xxxx::"
          int:
            ip: "fe80::xxxx"
            net: 64
        dhcp:
          start: "10.83.xxx.10"
          end: "10.83.xxx.254"
          mask: "255.255.xxx.0"
        fastd:
          port: 1000X
          secret: Your fastd secret Key
          public: Your fastd public key
        apache2:
          port: 200X
        keyserver: "https://keyserver.freifunk-franken.de/v2/index.php?hoodid=***HOOD_ID***"
      - hoodname: "YOUR_HOOD2_NAME"
        ipv4: ..............
```
