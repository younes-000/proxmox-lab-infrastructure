#  Installation et Configuration d'une Infrastructure Virtualisée avec Proxmox, pfSense et Conteneurs

##  Objectif

Ce projet documente la mise en place d'une infrastructure réseau virtualisée basée sur **Proxmox VE**, avec des services de sécurité et de gestion via des conteneurs (LXC) et un pare-feu **pfSense**.

---

##  Infrastructure

- **Hyperviseur** : Proxmox VE installé sur Debian 12 Bookworm
- **Réseaux** :
  - LAN : `192.168.1.0/24`
  - WAN : `10.1.1.0/24`

---

##  Conteneurs déployés

| Nom du Conteneur     | Adresse IP       | Fonction                             |
|----------------------|------------------|--------------------------------------|
| CT-SOL-ADGUARD       | 192.168.1.12     | DNS filtering via AdGuard Home       |
| CT-SOL-WAZUH         | 192.168.1.11     | SIEM & sécurité (Wazuh)              |
| CT-SOL-FIREFLY       | 192.168.1.13     | Gestion financière (Firefly III)     |

---

##  Sécurité & Réseau

###  pfSense
- Déployé comme VM avec deux interfaces :
  - `vmbr0` (WAN)
  - `vmbr1` (LAN)
- Configuration NAT automatique (ANY:ANY)
- Règles de redirection de ports mises en place pour accès depuis le réseau hôte

---

##  Étapes Clés

1. **Installation de Proxmox VE**
   - Ajout des dépôts et clés
   - Suppression du noyau Debian
   - Accès via interface web

2. **Configuration Réseau**
   - IP statique
   - Création de bridge
   - Template Debian 12 téléchargé

3. **Création des Conteneurs**
   - Installation et configuration d’AdGuard, Wazuh, Firefly III
   - Configuration réseau et test de connectivité

4. **Mise en place de pfSense**
   - Configuration des interfaces
   - Accès à l'interface web
   - NAT et pare-feu

5. **Monitoring**
   - Installation des agents Wazuh sur les conteneurs
   - Communication avec le manager centralisé

6. **Redirection de Ports**
   - Accès aux interfaces des services via pfSense (depuis hôte)

---

##  Résultats

- Plateforme fonctionnelle avec services accessibles via redirection NAT
- Communication inter-conteneurs opérationnelle
- Surveillance de la sécurité via Wazuh
- Filtrage DNS avec AdGuard
- Accès aux interfaces utilisateurs Firefly, AdGuard, et Wazuh

---

##  Remarques

- L'infrastructure est extensible pour usage personnel ou professionnel

---

##  Interfaces Capturées (dans le PDF)

- Interfaces Web : Proxmox, pfSense, AdGuard, Firefly, Wazuh
- Règles NAT, captures ping, configuration DNS, etc.
