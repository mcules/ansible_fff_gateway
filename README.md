# Ansible Freifunk-Franken Gateway

Hier entsteht eine Sammlung von Ansible Playbooks mit denen ein Freifunk-Franken Gateway aufgesetzt und verwaltet werden kann.

#### Von der Nutzung dieses Playbooks wird DRINGEND abgeraten, wenn es nicht komplett verstanden wurde!

Hier die offizielle Anleitung nach der man, zumindest einmal, erfolgreich ein Gateway aufgesetzt haben sollte: https://wiki.freifunk-franken.de/w/Freifunk-Gateway_aufsetzen

## Dienste
- [fastd]()
- [Batman]()
- [DHCP]()
- [Router Advertisements]()
- [Routing]()
- [Babel]()
- [Webserver]()

## Vorbereitung
Zuerst braucht man ein paar IP Adressen:
- [IPv4 Subnetz](https://wiki.freifunk-franken.de/w/Portal:Netz)
- [IPv6 Subnetz](https://wiki.freifunk-franken.de/w/Portal:Netz/IPv6)
- [IPv4 Peering](https://wiki.freifunk-franken.de/w/Portal:Netz#10.83.252.0.2F22_.28Master_IPs.29)
- [IPv6 Peering](https://wiki.freifunk-franken.de/w/Portal:Netz/IPv6#Transfer-IPs)


## Verzeichnis Struktur

    --- inventory/
    |
    |-- roles/
    |    |-- cli_tools/
    |    |-- babeld/
    |    \-- ...
    |             
    |
    |-- server/
    |   |-- vars/
    |   |   |-- all_hosts.yml
    |   |   \-- ...
    |   |-- gw01.yml
    |   |-- gw02.yml
    |   |-- gw03.yml
    |   \-- ...
    |
    \-- ansible.cfg

## Einrichtung

``` shell
cd /etc/ansible
git clone https://github.com/mcules/ansible_fff_gateway.git roles

mkdir inventory server

# ansible.cfg
cat > ansible.cfg <<EOF
[defaults]

inventory = inventory
roles_path = /etc/ansible/roles
EOF

```

## Host einrichten

``` shell
ansible-playbook server/gw01.yml
```
