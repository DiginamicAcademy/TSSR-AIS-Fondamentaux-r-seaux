# Les fondamentaux des réseaux

Mise en jambe commune aux parcours **TSSR** (Technicien supérieur systèmes et
réseaux) et **AIS** (Administrateur d'infrastructures sécurisées).

## 🎯 Objectifs pédagogiques

À la fin de ce module, vous saurez :

1. Expliquer ce qu'est un réseau et décrire le chemin qui mène d'une machine à
   Internet.
2. Expliquer pourquoi Internet est un réseau de réseaux, et ce qui le compose
   physiquement.
3. Distinguer les trois portées d'une adresse IP : la machine, le réseau local,
   Internet.
4. Décrire une adresse IPv4 et une adresse IPv6, et expliquer pourquoi IPv6
   existe.
5. Expliquer le rôle d'un nom de domaine sur Internet, et celui d'un domaine
   local en entreprise.
6. Lire une adresse IPv4 et son masque.
7. Retrouver les adresses IP de sa machine et le chemin suivi par ses paquets,
   sous Windows, Linux et macOS.

## ❔ Pourquoi ce module ?

Les notions de ce module servent dans la plupart des activités des deux
parcours :

- pour **diagnostiquer une panne** : quand un utilisateur n'a plus Internet, la
  cause peut être un câble débranché, une adresse IP absente, une box qui ne
  répond pas ou un nom qui n'est plus traduit en adresse. Pour trouver la bonne
  cause, il faut savoir par où passent les données ;
- pour **concevoir une infrastructure** : un plan d'adressage, un domaine Active
  Directory ou la liaison entre plusieurs sites reposent sur ces notions ;
- pour **sécuriser** : il faut savoir ce qui est visible depuis Internet, ce qui
  ne l'est pas, et par où passent les échanges.

## Prérequis

Aucun, en dehors de l'usage courant d'un ordinateur. Pour les manipulations de
la seconde partie, il faut un poste sous Windows, Linux ou macOS avec un
terminal.

## Le parcours

Le module se déroule en deux parties : **comprendre**, avec les chapitres 1 à 4,
puis **pratiquer** sur sa propre machine, avec les chapitres 5 à 7. Les
chapitres se suivent **dans l'ordre**, chacun s'appuyant sur le précédent.

| # | Étape | Contenu |
| --- | --- | --- |
| [01](01-Qu-est-ce-qu-un-reseau.md) | Qu'est-ce qu'un réseau ? | les équipements, le réseau local, de la box à l'opérateur, de l'opérateur à Internet, le chemin complet |
| [02](02-Internet-reseau-de-reseaux.md) | Internet, un réseau de réseaux | les réseaux qui composent Internet, les points d'échange, les datacenters et les copies de contenus, les câbles sous-marins |
| [03](03-Adresse-IP.md) | L'adresse IP | la machine, le réseau local, Internet ; la traduction par la box ; IPv4 ; IPv6 et ses raisons |
| [04](04-Nom-de-domaine.md) | Le nom de domaine | nom et adresse, l'arbre des noms, les acteurs, le DNS ; le domaine local de l'entreprise |
| [05](05-Adresse-IPv4-et-masque.md) | Une adresse IPv4 à la loupe | les quatre nombres, le masque, même réseau ou non |
| [06](06-Trouver-ses-adresses-IP.md) | Trouver ses adresses IP | les adresses de sa machine, sa passerelle, son adresse publique |
| [07](07-Traceroute.md) | Traceroute | observer le chemin suivi par les données et lire le résultat |
| [08](08-Conclusion.md) | Conclusion | le schéma d'ensemble, les points à retenir, les commandes |

## Conventions

- Les commandes sont données pour **Windows** (invite de commandes ou
  PowerShell), **Linux** et **macOS** (application Terminal). Elles affichent
  des informations et ne modifient pas la configuration du poste.
- Chaque chapitre se termine par des exercices. La correction est masquée :
  cherchez la réponse avant de l'afficher.
- Les adresses des exemples sont prises dans les plages réservées à la
  documentation (`192.0.2.0/24`, `198.51.100.0/24`, `203.0.113.0/24`,
  `2001:db8::/32`) ou dans les plages privées. Elles ne désignent aucune
  machine réelle sur Internet. Il en va de même pour les domaines `example.com`
  et `.example`.
