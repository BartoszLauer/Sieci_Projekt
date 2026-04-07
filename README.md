# Sieci_Projekt

Polecenie 4 - Wyłącz w sieci protokół CDP. Uruchom protokół LLDP i wyłącz go tam gdzie jest to konieczne.

Trzeba to zrobic na urzadzeniach SW1 i SW2 (tego jestem pewien) (wydaje mi sie ze na SW3 NIE TRZEBA) a jezeli chodzi o routery to musze to przemyslec na ktore trzeba 
```
SW1(config)# no cdp run
SW1(config)# lldp run
SW1(config)# interface range f0/1-3
SW1(config-if-range)# no lldp transmit
SW1(config-if-range)# no lldp receive
```
Polecenie 5 - Uruchom w istniejącej sieci RSTP. W miejscach gdzie jest to konieczne uruchom PortFast.

