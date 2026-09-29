[Sommaire](Readme.md) · [Chapitre suivant →](02-Internet-reseau-de-reseaux.md)

# Qu'est-ce qu'un réseau ?

Un réseau informatique relie des machines pour qu'elles puissent **échanger des
informations**.

On peut le comparer au réseau routier. Les machines sont les maisons, les câbles
et les ondes radio sont les routes, les équipements réseau sont les carrefours
et les panneaux. Les règles communes, appelées **protocoles**, jouent le rôle du
code de la route : tout le monde doit les respecter pour que les échanges
aboutissent.

---

## 1. Le plus petit des réseaux

Deux ordinateurs reliés par un câble forment déjà un réseau. Dès qu'il y a plus
de deux machines, on les relie toutes à un boîtier central : le
**commutateur** (*switch* en anglais).

```mermaid
flowchart LR
    subgraph deux["Deux machines"]
        A1["Ordinateur"] ---|"un câble"| A2["Ordinateur"]
    end
    subgraph plusieurs["Plusieurs machines"]
        direction TB
        B1["Ordinateur"] --- SW["Commutateur"]
        B2["Ordinateur"] --- SW
        B3["Imprimante"] --- SW
        B4["Serveur"] --- SW
    end
    deux ~~~ plusieurs
```

---

## 2. Le réseau local

Les machines d'un même lieu (une maison, une agence, un étage) forment un
**réseau local**. Elles communiquent directement entre elles : pour imprimer ou
ouvrir un dossier partagé, les données ne sortent pas du réseau local.

```mermaid
flowchart LR
    subgraph lan["Le réseau local"]
        PC["Ordinateurs"] --- SW["Commutateur"]
        IMP["Imprimante"] --- SW
        TEL["Smartphone"] -.-|"Wi-Fi"| AP["Point d'accès<br/>Wi-Fi"]
        AP --- SW
    end
    SW --- RT["Routeur"]
    RT --- BOX["Box"]
    BOX --- NET(("Internet"))
```

Le rôle de chaque équipement :

- le **commutateur** relie les machines du réseau local. Il sait sur quelle prise
  se trouve chaque machine et lui transmet ce qui lui est destiné ;
- le **point d'accès Wi-Fi** fait le même travail pour les appareils sans fil ;
- le **routeur** est la **porte de sortie** du réseau local : tout ce qui part
  vers un autre réseau passe par lui ;
- la **box** raccorde le réseau local à celui de l'opérateur.

> À la maison, la box assure tous ces rôles : commutateur, point d'accès Wi-Fi
> et routeur. En entreprise, chaque rôle est confié à un équipement distinct,
> plus robuste, géré par l'équipe informatique.

---

## 3. De la box à l'opérateur

La box est reliée à l'**opérateur** (Orange, SFR, Free, Bouygues Telecom...)
par une fibre optique. Cette fibre passe sous la rue jusqu'à une armoire de
quartier, puis jusqu'à un **central** de l'opérateur. Depuis ce central, le
réseau de l'opérateur couvre tout le pays.

```mermaid
flowchart LR
    subgraph maison["Chez vous"]
        direction TB
        BOX["Box"] --- PRISE["Prise fibre"]
    end
    subgraph rue["Dans le quartier"]
        direction TB
        ARM["Armoire<br/>de rue"]
    end
    subgraph operateur["Chez l'opérateur"]
        direction TB
        CEN["Central"] --- NAT["Réseau national"]
    end
    maison ---|"fibre optique"| rue
    rue ---|"fibre optique"| operateur
```

À défaut de fibre, la box peut passer par la ligne téléphonique en cuivre
(ADSL), en cours d'abandon, ou par le réseau mobile 4G ou 5G.

L'opérateur attribue à la box une **adresse publique**. C'est sous cette adresse
que toute la maison apparaît sur Internet (chapitre 3).

---

## 4. De l'opérateur à Internet

Le réseau de l'opérateur est relié aux autres réseaux du monde de deux façons :
dans des **points d'échange**, des bâtiments où les réseaux se branchent les uns
aux autres, et par des **câbles sous-marins** qui rejoignent les autres
continents.

```mermaid
flowchart LR
    OP["Réseau de<br/>votre opérateur"] --- IXP(("Point<br/>d'échange"))
    IXP --- AUT["Autres<br/>opérateurs"]
    IXP --- HEB["Hébergeurs<br/>de sites"]
    OP --- CAB["Câbles<br/>sous-marins"]
    CAB --- MONDE["Autres<br/>continents"]
```

Le chapitre 2 détaille cette organisation.

---

## 5. Le chemin complet

En assemblant ces étapes, on obtient le chemin d'une information entre votre
machine et le serveur d'un site Web :

```mermaid
flowchart TB
    subgraph chez["1. Chez vous"]
        direction LR
        M["Votre machine"] --> SW["Commutateur<br/>ou Wi-Fi"] --> RT["Routeur"] --> BOX["Box"]
    end
    subgraph op["2. Chez l'opérateur"]
        direction LR
        CEN["Central<br/>de quartier"] --> NAT["Réseau<br/>national"]
    end
    subgraph inet["3. Sur Internet"]
        direction LR
        IXP["Point<br/>d'échange"] --> HEB["Hébergeur"] --> S["Serveur<br/>du site"]
    end
    chez --> op --> inet
```

L'information passe d'un équipement à l'autre, comme un colis qui transite par
plusieurs centres de tri. Chaque équipement sait seulement à qui la transmettre
ensuite. Le chapitre 7 montre comment observer ce trajet depuis votre machine.

---

## L'essentiel

- Un réseau relie des machines qui suivent des règles communes, les protocoles.
- Le commutateur relie les machines d'un réseau local, le routeur est la porte
  de sortie, la box raccorde à l'opérateur. À la maison, la box regroupe ces
  rôles.
- Depuis la box, le chemin passe par l'opérateur, puis par les points d'échange
  et les câbles sous-marins, jusqu'au serveur.

---

## Exercices

### Exercice 1 - Un câble débranché

Dans une agence, quelqu'un débranche le câble entre le routeur et la box.
Qu'est-ce qui fonctionne encore ?

<details>
<summary>Voir la correction</summary>

Les échanges à l'intérieur du **réseau local** continuent : les postes peuvent
imprimer, ouvrir les dossiers partagés et communiquer entre eux. En revanche,
plus rien ne peut sortir vers Internet, puisque le lien entre le routeur et
l'opérateur est coupé.

</details>

### Exercice 2 - Les rôles de la box

Quels rôles joue la box, à la maison ?

<details>
<summary>Voir la correction</summary>

Elle se raccorde à l'opérateur. Elle sert aussi de **commutateur** (ses prises
Ethernet), de **point d'accès Wi-Fi** et de **routeur**.

</details>

---

[Sommaire](Readme.md) · [Chapitre suivant →](02-Internet-reseau-de-reseaux.md)
