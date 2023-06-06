# Installation d’un serveur NFS sous Debian/Ubuntu

* Mettre à jour le serveur :`apt update && apt upgrade`
  

* Installation des paquets :`apt install nfs-kernel-server nfs-common`
  

# Configuration du serveur NFS

* Création du répertoire partagé :`mkdir /srv/partage`
  

* Configuration du partage NFS :`nano /etc/exports`
* C’est ici, qui est indiqué ce qui est partagé sur quel client et avec quel droit :`/srv/proxmox IP_node1(rw,no_subtree_check,sync,no_root_squash) IP_node2(rw,no_subtree_check,sync,no_root_squash)`

* **rw** : les clients ont les droits d’écriture (w) et de lecture (r) sur le partage NFS.
* **sync** : synchronisation des données entre le client et le serveur.
* **no_subtree_check** : Pas de vérification des droits d’accès dans les sous répertoires.
* **no_root_squash** : cette option est seulement nécessaire pour les clients sans disque, ce qui est mon cas avec la configuration de Promxox

* Relance du service _nfs-kernel-server_ pour la prise en compte des modifications :`service nfs-kernel-server restart`

Paramétrage du partage NFS sur le client

Ajout du partage NFS sur ESXi

Allez dans "stockage"

![Legend](https://github.com/baaldees/Serveur_nfs/blob/main/dossier/fournir_les_details.jpeg)



puis "Nouvelle banque de données"

ensuite "Monter la banque de données NFS"

laisser NFS 3

fournissez les details du partage NFS

faite "suivant " puis terminer
