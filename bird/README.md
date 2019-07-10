Add following to you server config file:

```
---
- hosts: fqdn.your.host
  roles:
    - { name: bird, tags: bird }
  vars_files:
    - vars/all_hosts.yml
  vars:
    - bird:
        router_id: "Your_IP_Address"
        routes: [ "1234:1234:1234::/44" ]
        peerings:
        - name: Name_for_your_peering
          own: { as: Your_AS_Number,  ipv6: "Your_Peering_IPv6", ipv4: "Your_Peering_IPv4" }
          peer:
            as: Peer_AS_Number
            ipv6: "Peer_IPv6"
            ipv4: "Peer_IPv4"
          filter: my_filter_name # Optional
        function_v6: # Optional
        - name: test
          content: "return net ~ [
                1234:1234:1234::/44
          ];"
        filter_v6: #optional
        - name: net_f3n
          content: "if (net ~ <prefix_to_announce_routes_inside>) then {
                      if (net.len != 48) then {
                        bgp_path.prepend(205100);
                        bgp_path.prepend(205100);
	                    }
                      accept;
                    } else {
                      reject;
                    }
                  }
    - firewall_enabled: false
```
