# Le routage dynamique 
1) Rôle des protocoles de routage dynamique 
2) Routage statique/routage dynamique
3) Fonctionnement du routrage dynamique 
4) Classification 
5) Classful/Classless
6) La convergence d'un réseau 
7) Le Métrique 
8) Vecteur de distance ou états de liens 

# Le routage dynamique 
Les protocoles de routage dynamique sont utilisés par les routeurs pour partager des informations sur l’accessibilité et l’état des réseaux distants. Les protocoles de routage dynamique effectuent plusieurs tâches, notamment :
- détection de réseaux 
- mise à jour et maintenence des tables de routage 

# Rôle des protocoles de routage dynamique 
La figure illustre les structures de données, les messages de protocole de routage et l'algorithme de routage utilisé par le protocole EIGRP. 

- Les protocoles de routage créent et gèrent des structures de données: 
Le protocole EIGRP crée et gère:
 - table de voisinage 
 - table topologique
- les protocoles de routage échangent des messages 
- les protocoles de routage utilisent des algorithmes de routage pour déterminer les meilleures routes 

# Avantages
- approprié pour toutes les topologies ou plusieurs routeurs sont requis.
- généralement indépendant de la taille du réseau 
- adapte automatiquement la topologie pour réacheminer le traffic si possible. 
# Inconvénients 
- peut être plus complexe à mettre en oeuvre 
- moins sécurisé. Des paramètres de configuration supplémentaires sont nécessaires pour la sécurisation 
- la route dépend de la topologie en cours 
- nécessite des capacités supplémentaires en matière de processeur, de mémoire vive et de bande passante

# Fonctionnement du routage dynamique 
D'une manière générale, le fonctionnement d'un protocole de routage dynamique peut être décrit de la manière suivante: 
- le routeur envoie et reçoit des messages de routage sur ses interfaces
- le routeur partage les messages et les informations de routage avec d'autres routeurs qui utilisent le même protocole de routage 
- les routeurs échangent des informations de routage pour découvrir des réseaux distants 
- lorsqu'un routeur détecte une modification de topologie, le protocole de routage peut l'annoncer aux autres routeurs 

# Classification des protocoles de routage 
Un système autonome (SA) ou « domaine de routage » est un ensemble de routeurs au sein d'une administration commune telle qu'une entreprise. Deux types de protocoles de routage sont nécessaires :
- Protocole IGP (Interior Gateway Protocol): Utilisé pour le routage au sein d'un SA => « routage intra-SA ». Les entreprises et même les fournisseurs de services utilisent un protocole IGP sur leurs réseaux internes. Les protocoles IGP incluent les protocoles RIP, EIGRP, OSPF et IS-IS.
- Protocole EGP (Exterior Gateway Protocol): Utilisé pour le routage entre des SA => « routage inter-SA ». Les fournisseurs de services et les grandes entreprises peuvent être interconnectés au moyen d'un protocole EGP. Le protocole BGP (Border Gateway Protocol) est le seul protocole EGP actuellement viable et c'est le protocole de routage officiel utilisé par Internet. Le terme EGP est souvent directement remplacé par BGP. 

protocoles de routage dynamique: 
- protocoles IGP 
 - protocoles de routage à vecteur de distance
  - Ripv1, v2
  - IGRP, EIGRP
 - protocoles de routage à état de liens 
  - OSPF, IS-IS
- protocoles EGP
 - Protocole de routage BGP
  - BGP

# Routage des protocoles de routage dynamique 
- RIP (Routing Information Protocol)
- IGRP (Interior Gateway Routing Protocol)
- EIGRP (Enhanced Interior Gateway Routing Protocol)
- OSPF (Open Shortest Path First)
- IS-IS (Intermediate System-to-Intermediate System)
- BGP (Border Gateway Protocol)

# Protocoles classful et classless
Tout protocole de routage peut être classifié soit comme: 
- Protocole de routage Classful (avec classe)
- Protocole de routage Classless (sans classe)
Remarque: les protocoles de routage pour IPV6 sont toujours classless 

- RIPV1 et IGRP: protocoles par classe classful (ancien)
- RIPV2 et EIGRP, OSPF, IS-IS et BGP: protocoles sans classe classless (récent)

# Protocoles classful 
Les protocoles Classful n'envoient pas le masque lors des mises à jour de l'information de routage:
- C'est le cas des protocoles plus anciens comme RIP (v1) 
- Conçus à l'époque où les adresses réseau étaient classés Classe A, B, ou C (D et E ne sont pas routés d'habitude) 
- Le protocole de routage n'avait pas besoin d'envoyer le masque : le masque était déterminé selon la valeur du premier octet de l'adresse du réseau

# Protocoles classless 
Les protocoles Classless incluent le masque dans les mises à jour. La plupart des réseaux actuels requièrent des protocoles Classless car ils supportent VLSM (Variable-Length Subnet Masking), CIDR(Classless Inter Domain Routing) et Réseaux non-contigus.

# La convergence *
La Convergence est obtenue lorsque les tables de routage de tous les routeurs deviennent consistantes. Le réseau a convergé lorsque tous les routeurs ont une vue complète et précise du réseau. Une caractéristique importante d'un protocole de routage est :
- la vitesse de convergence lorsqu'un changement est intervenu sur la topologie 
- le temps de convergence concerne le temps pour que les routeurs: 
 - partagent l'information 
 - claculent les meilleurs routes 
 - mettent à jour leurs tables de routage 
Un réseau n'est pas totalement opérationnel tant que le réseau n'a pas convergé. Le temps de convergence devient un facteur critique. De manière générale, le temps de convergence :
- Lent: RIP
- Rapide: EIGRP, OSPF et IS-IS

# Meilleur chemin et métrique 
Les métriques sont utilisées pour mesurer ou comparer: 
- Quelle route est la meilleure ?
- Attribuer des coûts pour atteindre les réseaux distants
Les protocoles apprennent plusieurs routes vers une destination. Les métriques sont utilisées pour déterminer le chemin préféré. 
Exemples de métriques:
- RIP : Nombres de sauts (Hop count)
- EIGRP (cisco semi-ouvert depuis 2013): débit, latence, fiabilité et charge 
- OSPF (version Cisco): débit

# Vecteur de distance ou état de liens 
Les protocoles intérieurs (IGP) peuvent être de 2 types:
- Protocoles à vecteur de distance
- protocoles à l'état de liens 

# Protocoles à vecteur de distance
Les routes sont annoncées comme vecteurs de distance et direction. La distance est définie selon une métrique 
- Ex : le nombre de sauts (hop count), la bande passante, etc. 
La direction (vecteur) indique simplement:
- L'adresse du prochain routeur ou
- L'interface de sortie. 
Ces protocoles utilisent souvent l'algorithme Bellman-Ford pour la détermination du meilleur chemin.

Le protocole de routage à vecteur de distance : 
- Ne connaît pas la topologie du réseau 
- La seule information qu'il détient est l'information de routage reçue de ses voisins
=>Principe similaire à celui des pancartes sur une route

# Protocoles à états de liens 
Un protocole à état de liens (Link-state) peut créer une “vue complète” ou topologie, du réseau.
- Équivalent à une carte de tout le réseau
- Les protocoles Link-state sont associés à l'algorithme Shortest Path First (SPF) pour l'établissement des routes Un routeur link-state utilise l'information des états des liens pour :
 - Créer une carte topologique ; 
 - Choisir la meilleure route vers toute destination sur la carte 
- Avantage : Contrairement au protocole RIP, les protocoles de routage à état de liens n'utilisent pas de mises à jour régulières. Une fois que le réseau a convergé, une mise à jour d'état de liens est envoyée uniquement en cas de modification de la topologie.

# Vecteur de distance/ états de liens
Les protocoles à vecteur de distance sont indiqués lorsque :
- Le réseau est simple et ne requiert pas une structuration hiérarchique
- L'administrateur n'a pas la connaissance technique pour installer et déboguer un protocole à état des liens ;
- Lorsque la performance de convergence n'est pas un problème. 

Les protocoles à état de liens sont tout particulièrement adaptés dans les situations suivantes :
- Réseau conçu de manière hiérarchique (il s'agit généralement de grands réseaux) 
- Réseau pour lequel une convergence rapide est primordiale 
- Administrateurs ayant une bonne connaissance du protocole de routage à état de liens implémenté

# commandes CISCO 
A(CONFIG)# ROUTER RIP 
A(CONFIG-ROUTER)# VERSION 2 
A(CONFIG-ROUTER)# NETWORK 172.30.1.0 
A(CONFIG-ROUTER)# NETWORK 192.168.0.0 
A(CONFIG-ROUTER)# NO AUTO-SUMMARY 
A#SH IP ROUTE 
C 172.30.1.0 IS DIRECTLY CONNECTED, FA0/0 
R 172.30.2.0 [120/1] VIA 192.168.0.2, FA0/1 
C 192.168.0.0 IS DIRECTLY CONNECTED, FA0/1

B(CONFIG)# ROUTER RIP 
B(CONFIG-ROUTER)# VERSION 2 
B(CONFIG-ROUTER)# NETWORK 172.30.2.0 
B(CONFIG-ROUTER)# NETWORK 192.168.0.0 
B(CONFIG-ROUTER)# NO AUTO-SUMMARY 
B#SH IP ROUTE 
R 172.30.1.0 [120/1] VIA 192.168.0.1, FA0/1
C 172.30.2.0 IS DIRECTLY CONNECTED, FA0/0 
C 192.168.0.0 IS DIRECTLY CONNECTED, FA0/1