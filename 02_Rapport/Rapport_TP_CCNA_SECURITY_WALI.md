# Rapport - TP CCNA Security

## Mise en place d'une infrastructure multi-entreprises avec VLAN, OSPFv2 et durcissement sécurité

### 1. Objectif

L'objectif du projet est de construire une infrastructure réseau composée de trois entreprises reliées par un backbone WAN en OSPFv2. Chaque entreprise dispose de VLANs dédiés aux étudiants, aux enseignants et à l'administration. Le projet répond au TP demandé et ajoute une couche sécurité afin de produire une architecture plus professionnelle.

### 2. Périmètre technique

Le projet couvre :
- création des VLANs ;
- configuration des trunks 802.1Q ;
- configuration des sous-interfaces routeur ;
- adressage IPv4 ;
- routage dynamique OSPFv2 ;
- interfaces OSPF passives ;
- sécurisation des accès d'administration ;
- désactivation des ports inutilisés ;
- port-security ;
- authentification OSPF MD5 sur les liens WAN ;
- validation par commandes `show` et tests ping.

### 3. Architecture

L'infrastructure repose sur trois routeurs Cisco 2911, six switchs 2960 et six PC. Les trois routeurs sont reliés en triangle WAN afin d'assurer une redondance de chemin et une propagation dynamique des routes via OSPF area 0.

Chaque entreprise utilise deux VLANs utilisateurs et un VLAN d'administration :
- VLAN Étudiants ;
- VLAN Enseignants ;
- VLAN 99 Administration / Native.

### 4. Choix d'adressage

Les réseaux LAN sont issus des blocs fournis dans le TP. La première adresse utilisable est affectée au PC, la dernière adresse utilisable à la passerelle routeur, et les deux adresses précédentes aux interfaces de management des switchs.

### 5. Routage OSPFv2

OSPFv2 est configuré sur les trois routeurs avec les router-id suivants :
- R1 : 1.1.1.1 ;
- R2 : 2.2.2.2 ;
- R3 : 3.3.3.3.

Les liens WAN participent à OSPF, tandis que les interfaces LAN sont configurées en `passive-interface`. Cette configuration permet d'annoncer les réseaux utilisateurs sans envoyer de paquets Hello OSPF vers les PC.

### 6. Sécurité mise en place

Le projet ne se limite pas à la connectivité. Plusieurs mesures de durcissement ont été ajoutées :
- `enable secret` ;
- chiffrement des mots de passe ;
- bannière d'avertissement ;
- administration SSH ;
- ACL sur les lignes VTY ;
- VLAN natif 99 au lieu du VLAN 1 ;
- VLAN parking 999 pour les ports inutilisés ;
- restrictions des VLANs autorisés sur les trunks ;
- port-security sur les ports d'accès ;
- authentification OSPF MD5 sur les liens WAN ;
- VLAN 99 non annoncé dans OSPF.

### 7. Validation technique

Les tests réalisés confirment que :
- les VLANs sont créés et actifs ;
- les trunks transportent les VLANs attendus ;
- le VLAN natif est bien le VLAN 99 ;
- les sous-interfaces routeur assurent le routage inter-VLAN ;
- les voisins OSPF sont en état `FULL` ;
- les routes distantes sont apprises en OSPF ;
- les PC communiquent entre entreprises ;
- les interfaces LAN sont passives dans OSPF.

### 8. Conclusion

Le projet répond au TP initial tout en allant plus loin grâce à une approche sécurité. L'infrastructure obtenue est segmentée, routée dynamiquement, administrable en SSH et durcie contre plusieurs erreurs de configuration courantes. Cette approche se rapproche davantage d'une démarche professionnelle d'architecture réseau qu'une simple configuration de connectivité.
