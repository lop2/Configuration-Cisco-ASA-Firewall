# Rapport de Configuration – Cisco ASA Firewall

## 1. Introduction
Ce rapport présente la configuration de base d’un pare-feu **Cisco ASA** réalisée dans le cadre d’un laboratoire de formation.  
L’objectif est de mettre en place :  
- La configuration des interfaces  
- Un serveur DHCP interne  
- L’accès sécurisé via SSH  

---

## 2. Contexte du Laboratoire
Le laboratoire est composé d’un pare-feu Cisco ASA connecté à trois zones :  
- **OUTSIDER** : Zone externe (Internet)  
- **INSIDER** : Réseau interne de l’entreprise  
- **DMZ** : Zone démilitarisée pour héberger des services publics  

Le fichier `.pkt` fourni permet de visualiser et simuler cette configuration dans **Cisco Packet Tracer**.

---

## 3. Configuration des Interfaces

| Interface           | Nom (nameif) | Security-Level | Adresse IP     | Masque           |
|---------------------|--------------|---------------|----------------|------------------|
| GigabitEthernet1/1  | OUTSIDER     | 0             | 20.20.20.1     | 255.255.255.0    |
| GigabitEthernet1/2  | INSIDER      | 100           | 192.168.10.1   | 255.255.255.0    |
| GigabitEthernet1/3  | DMZ          | 70            | 10.10.10.1     | 255.255.255.240  |

---

## 4. Configuration du Serveur DHCP interne
- **Plage d’adresses** : `192.168.10.101` à `192.168.10.199` (INSIDER)  
- **DNS** : `8.8.8.8`  
- **Activation** :  
```bash
dhcpd enable INSIDER
