# Plan d'adressage final

## WAN

| Lien | Réseau | Interface | IP | Masque |
|---|---|---|---|---|
| R2 ↔ R3 | 10.0.0.0/30 | R3 Serial0/3/0 | 10.0.0.1 | 255.255.255.252 |
| R2 ↔ R3 | 10.0.0.0/30 | R2 Serial0/3/0 | 10.0.0.2 | 255.255.255.252 |
| R2 ↔ R1 | 10.0.0.4/30 | R2 Serial0/3/1 | 10.0.0.5 | 255.255.255.252 |
| R2 ↔ R1 | 10.0.0.4/30 | R1 Serial0/3/1 | 10.0.0.6 | 255.255.255.252 |
| R1 ↔ R3 | 10.0.0.8/30 | R1 Serial0/3/0 | 10.0.0.9 | 255.255.255.252 |
| R1 ↔ R3 | 10.0.0.8/30 | R3 Serial0/3/1 | 10.0.0.10 | 255.255.255.252 |

## Entreprise 1

Base : 172.31.192.0/18

| VLAN | Rôle | Réseau | Passerelle routeur | PC | Switch S1 | Switch S2 |
|---|---|---|---|---|---|---|
| 10 | Étudiants | 172.31.192.0/24 | 172.31.192.254 | PC1-1 = 172.31.192.1 | N/A | N/A |
| 40 | Enseignants | 172.31.193.0/24 | 172.31.193.254 | PC2-1 = 172.31.193.1 | N/A | N/A |
| 99 | Administration/Native | 172.31.194.0/24 | 172.31.194.254 | N/A | S1-1 = 172.31.194.253 | S2-1 = 172.31.194.252 |

## Entreprise 2

Base : 192.168.100.0/24

| VLAN | Rôle | Réseau | Passerelle routeur | PC | Switch S1 | Switch S2 |
|---|---|---|---|---|---|---|
| 20 | Étudiants | 192.168.100.0/26 | 192.168.100.62 | PC1-2 = 192.168.100.1 | N/A | N/A |
| 50 | Enseignants | 192.168.100.64/26 | 192.168.100.126 | PC2-2 = 192.168.100.65 | N/A | N/A |
| 99 | Administration/Native | 192.168.100.128/26 | 192.168.100.190 | N/A | S1-2 = 192.168.100.189 | S2-2 = 192.168.100.188 |

## Entreprise 3

Base : 172.18.48.0/20

| VLAN | Rôle | Réseau | Passerelle routeur | PC | Switch S1 | Switch S2 |
|---|---|---|---|---|---|---|
| 30 | Étudiants | 172.18.48.0/24 | 172.18.48.254 | PC1-3 = 172.18.48.1 | N/A | N/A |
| 60 | Enseignants | 172.18.49.0/24 | 172.18.49.254 | PC2-3 = 172.18.49.1 | N/A | N/A |
| 99 | Administration/Native | 172.18.50.0/24 | 172.18.50.254 | N/A | S1-3 = 172.18.50.253 | S2-3 = 172.18.50.252 |

## Règles appliquées

- Première adresse utilisable du sous-réseau : PC.
- Dernière adresse utilisable du sous-réseau : passerelle routeur.
- Deux adresses précédentes : interfaces VLAN 99 des switchs.
- VLAN 99 non annoncé dans OSPF.
