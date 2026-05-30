# Matrice d'exigences et preuves de validation

| Exigence du TP / du projet | Réalisation | Preuve attendue |
|---|---|---|
| Créer les VLANs | VLAN 10/20/30 Étudiants, VLAN 40/50/60 Enseignants, VLAN 99 Administration, VLAN 999 Parking | `show vlan brief` |
| Configurer les trunks 802.1Q | Trunks routeur-S1 et S1-S2 | `show interfaces trunk` |
| Sécuriser le VLAN natif | VLAN natif 99 au lieu du VLAN 1 | `show interfaces trunk` |
| Limiter les VLANs autorisés | Seuls les VLANs utiles sont autorisés sur chaque trunk | `show interfaces trunk` |
| Configurer le routage inter-VLAN | Sous-interfaces G0/1.x sur R1/R2/R3 | `show ip interface brief` |
| Configurer OSPFv2 | OSPF process 1, area 0, router-id 1.1.1.1 / 2.2.2.2 / 3.3.3.3 | `show ip ospf neighbor` |
| Vérifier les routes distantes | Routes OSPF marquées `O` | `show ip route` |
| Sécuriser OSPF | Authentification MD5 sur les liens WAN | configuration routeur |
| Réduire la surface OSPF | Interfaces LAN en passive-interface | `show ip protocols` |
| Valider la connectivité | Ping inter-sites entre PC | captures ping |
| Sécuriser l'administration | SSH, ACL VTY, mots de passe chiffrés | running-config |
| Réduire les risques sur ports inutilisés | VLAN 999 + shutdown | `show vlan brief` + running-config |
