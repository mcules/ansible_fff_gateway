Add following to you server config file:

```
---
- hosts: fqdn.your.host
  roles:
    - { name: bird, tags: bird }
  vars_files:
    - vars/all_hosts.yml
  vars:
    - bird_peerings_v6:
      - name: Name_for_your_peering
        ix: Internet_Exchange # Just used for File and peer name
        own:
          as: Your_AS_Number
          ipv6: "Your_Peering_IPv6"
        peer:
          as: Peer_AS_Number
          ipv6: "Peer_IPv6"
        filters:
          - name: test
            result: accept
            action: reject
    - bird_function_v6:
      - name: test
        content: "return net ~ [
                1234:1234:1234::/44
        ];"
    - firewall_enabled: false
```
