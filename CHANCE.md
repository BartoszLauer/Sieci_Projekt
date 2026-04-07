
### 1. Naprawa R2 zrobienie Router-on-a-Stick 
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

### 2. Trunk na SW3
```
Switch(config)#interface Gig0/1
Switch(config-if)#switchport mode trunk
```
## Polecenie 4 (Pełen config (tak mi sie wydaje)
### 3. Na wszytkich routerach i przelacznikach (r1, r2, r3, sw1, sw2, sw3 wyłaczam cdp i zalaczam lldp)

```
NazwaUrzadniea(config)# no cdp run
NazwaUrzadniea(config)# lldp  run
```

**teraz trzeba powyłaczać porty które ida do uzytkowników**

SW1:
```
SW1(config)#interface range fa0/1-4
SW1(config-if-range)#no lldp transmit 
SW1(config-if-range)#no lldp receive
```

SW2:
```
SW2(config)#interface range fa0/1-3
SW2(config-if-range)#no lldp transmit 
SW2(config-if-range)#no lldp receive
```
R3:
```
R3(config)#interface gig0/1
R3(config-if)#no lldp transmit 
R3(config-if)#no lldp receive 
```


## Polecenie 5 Uruchom w istniejącej sieci RSTP. W miejscach gdzie jest to konieczne uruchom PortFast.


