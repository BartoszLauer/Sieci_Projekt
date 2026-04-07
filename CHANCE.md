
# Naprawa R2 zrobienie Router-on-a-Stick 
```
R2(config)interface Gig0/0
R2(config-if)no shutdown

R2(config)interface Gig0/0.10
R2(config-subif) encapsulation dot1Q 10
R2(config-subif)ip address 172.16.10.1 255.255.255.0

R2(config)interface Gig0/0.20
R2(config-subif)encapsulation dot1Q 20
R2(config-subif)ip address 172.16.20.1 255.255.255.0

R2(config)interface Gig0/0.30
R2(config-subif)encapsulation dot1Q 30
R2(config-subif)ip address 172.16.30.1 255.255.255.0
```

Trunk na SW3
```
Switch(config)#interface Gig0/1
Switch(config-if)#switchport mode trunk
```
