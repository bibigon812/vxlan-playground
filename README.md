# VxLAN Sandbox

``` shell
vagrant up
vagrant ssh vxlan-1
ping -c 1 172.16.0.2
sudo vtysh -c 'show interface vxlan100'
sudo vtysh -c 'show evpn mac vni 100'
```

## Environment

- frr (bgp/evpn)
- brctl

## Hosts

- vxlan-1
- vxlan-2
