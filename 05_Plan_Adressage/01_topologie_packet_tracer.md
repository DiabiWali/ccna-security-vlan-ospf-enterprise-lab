# Topologie finale Packet Tracer

## Objectif

Construire une infrastructure réseau multi-entreprises avec :
- segmentation VLAN ;
- trunks 802.1Q ;
- routage inter-VLAN via sous-interfaces ;
- routage dynamique OSPFv2 area 0 ;
- durcissement sécurité réseau.

## Équipements utilisés

- 3 routeurs Cisco 2911 : R1, R2, R3.
- 6 switchs Cisco 2960 : S1-1, S2-1, S1-2, S2-2, S1-3, S2-3.
- 6 PC : PC1-1, PC2-1, PC1-2, PC2-2, PC1-3, PC2-3.

## WAN OSPF final

R1, R2 et R3 sont reliés en triangle :

| Lien | Réseau | Interfaces |
|---|---|---|
| R1 ↔ R2 | 10.0.0.4/30 | R1 Serial0/3/1 ↔ R2 Serial0/3/1 |
| R2 ↔ R3 | 10.0.0.0/30 | R2 Serial0/3/0 ↔ R3 Serial0/3/0 |
| R1 ↔ R3 | 10.0.0.8/30 | R1 Serial0/3/0 ↔ R3 Serial0/3/1 |

Interfaces DCE configurées avec `clock rate 64000` lorsque nécessaire.

## Entreprise 1

- R1 GigabitEthernet0/1 ↔ S1-1 GigabitEthernet0/1
- S1-1 GigabitEthernet0/2 ↔ S2-1 GigabitEthernet0/1
- PC1-1 ↔ S1-1 FastEthernet0/1 : VLAN 10 Étudiants
- PC2-1 ↔ S2-1 FastEthernet0/13 : VLAN 40 Enseignants

## Entreprise 2

- R2 GigabitEthernet0/1 ↔ S1-2 GigabitEthernet0/1
- S1-2 GigabitEthernet0/2 ↔ S2-2 GigabitEthernet0/1
- PC1-2 ↔ S1-2 FastEthernet0/1 : VLAN 20 Étudiants
- PC2-2 ↔ S2-2 FastEthernet0/13 : VLAN 50 Enseignants

## Entreprise 3

- R3 GigabitEthernet0/1 ↔ S1-3 GigabitEthernet0/1
- S1-3 GigabitEthernet0/2 ↔ S2-3 GigabitEthernet0/1
- PC1-3 ↔ S1-3 FastEthernet0/1 : VLAN 30 Étudiants
- PC2-3 ↔ S2-3 FastEthernet0/13 : VLAN 60 Enseignants

## Remarque

Le VLAN 99 est utilisé comme VLAN d'administration et VLAN natif sur les trunks.
Le VLAN 999 est utilisé comme VLAN parking pour les ports inutilisés.
