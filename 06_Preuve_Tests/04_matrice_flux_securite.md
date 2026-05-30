# Matrice de flux et logique sécurité

| Source | Destination | Service | Décision | Justification |
|---|---|---|---|---|
| VLAN Étudiants local | Passerelle locale | ICMP | Autorisé | Test de connectivité de base |
| VLAN Enseignants local | Passerelle locale | ICMP | Autorisé | Test de connectivité de base |
| VLAN Étudiants | VLAN Enseignants inter-sites | ICMP | Autorisé pour le TP | Validation OSPF bout en bout |
| VLAN Enseignants | VLAN Étudiants inter-sites | ICMP | Autorisé pour le TP | Validation OSPF bout en bout |
| VLAN Administration 99 | Équipements réseau locaux | SSH | Autorisé | Administration sécurisée |
| VLAN utilisateurs | VTY routeurs/switchs | SSH/Telnet | Refusé par ACL VTY | Durcissement sécurité |
| Tout trafic OSPF LAN | Interfaces LAN | OSPF Hello | Refusé via passive-interface | Réduction de surface d'attaque |
| OSPF WAN | Routeurs R1/R2/R3 | OSPF | Autorisé + MD5 | Routage dynamique sécurisé |
| Ports inutilisés | Réseau | Any | Désactivé | Réduction des risques |
