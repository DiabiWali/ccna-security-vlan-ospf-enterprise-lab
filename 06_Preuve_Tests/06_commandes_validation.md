# Commandes de validation

## Routeurs

À exécuter sur R1, R2 et R3 :

```cisco
show ip interface brief
show ip ospf neighbor
show ip route
show ip route ospf
show ip protocols
show running-config
```

Résultat attendu :
- Interfaces WAN `Serial0/3/0` et `Serial0/3/1` en `up/up`.
- Voisins OSPF en état `FULL`.
- Routes distantes marquées `O`.
- Interfaces LAN et sous-interfaces en passive-interface.
- VLAN 99 non annoncé dans OSPF.

## Switchs

À exécuter sur les switchs :

```cisco
show vlan brief
show interfaces trunk
show port-security
show running-config
```

Résultat attendu :
- VLANs utilisateurs actifs.
- VLAN 99 actif.
- VLAN 999 actif pour les ports inutilisés.
- Trunks actifs avec VLAN natif 99.
- VLANs autorisés limités aux VLANs utiles.

## Tests PC

Depuis PC1-1 :

```text
ping 172.31.192.254
ping 172.31.193.1
ping 192.168.100.1
ping 192.168.100.65
ping 172.18.48.1
ping 172.18.49.1
```

Depuis PC2-3 :

```text
ping 172.31.192.1
```

Résultat attendu :
- `Sent = 4, Received = 4, Lost = 0`.
- Le premier paquet peut parfois être perdu dans Packet Tracer à cause de l'ARP.
