# Disponiblité d'un service informatique 
1) Risques et sources des problèmes
2) La haute disponibilité
3) Le SLA
4) Comment améliorer la HD ?
5) Le clustering
6) La répartition de charge
7) La redondance
8) La sauvegarde

# Quels sont les risques ? 
Amazon : une interruption de service de 40 mn le 19 août 2013 aurait fait perdre à Amazon près de 5 millions de dollars : http://www.zdnet.fr/actualites/comme-google-amazon-a-subi-une-panne-informatique-39793254.htm

La bourse New York : une panne a immobilisé la Bourse de New York pendant quatre heures en 2015 :
https://www.datacenterdynamics.com/en/news/new-york-stock-exchange-fails-due-to-configuration-problems/

Panne informatique géante le 8 juin 2021 : Les sites de la Maison Blanche, du gouvernement britannique, ou encore de grands médias ont été temporairement inaccessibles. Le problème provenait d'une entreprise offrant un service Internet : https://www.lci.fr/societe/panne-informatique-geante-amazon-maison-blanche-bbc-le-monde-ce-qu-il-s-est-passe-2188166.html

Crowdstrike: panne mondiale provoquée le 19 juillet 2024 par une mise à jour défectueuse de CrowdStrike sur des postes Windows. Elle a entraîné des indisponibilités ou fortes perturbations dans des secteurs dépendants de l’informatique : transport aérien, services clients, médias, établissements de santé et services financiers ; en France, des vols Air France ont été retardés et des services de Bouygues Telecom ont été affectés.

L’interruption d’un service informatique peut entraîner :
● Un risque pour la santé (panne des numéros d’urgence en France en juin 2021)
● Un risque pour la sécurité (panne d’un service de police par ex)
● Des pertes financières importantes
● Un réseau d’information à l’arrêt (panne des médias)
● Un arrêt des chaînes de production
● Une crédibilité en baisse
● Etc.

# Les origines des menaces sur la disponibilité
- Catastrophes naturelles 
- erreurs humaines 
- Pannes de matériel 
- Sabotage 
- Attaques de logiciel 
- Erreurs logiciels 
- Vol
- Interruption de services 

# L'analyse des risques 
L'analyse des risques est un processus qui consiste à analyser les dangers que représentent les événements d'origine humaine et naturelle pour les ressources d'une entreprise. L’analyse peut se faire de façon quantitative ou qualitative.
Exemple d'analyse quantitative: 
- Ressource Serveur de fichiers 
- Menace: Echec
- Estimation de perte unique: 15k€
- Taux annualisé d'occurence (ARO): Probabilité de 15%
- Estimation des pertes annuelles (ALE): 2250$

Exemple d'analyse qualitative:
- Catégorie: Catastrophique, Critique, Acceptable, Négligeable
- Fréquent: 20, 15, 10, 5
- Probable: 16, 12, 8, 4
- Occasionnel: 12, 9, 6, 3
- Rare: 8, 6, 4, 2
- Improbable: 4, 3, 2, 1

On priorise les protections à partir de l’impact métier et de la vraisemblance d’un incident (voir méthode E-BIOS, plus tard)

# Les solutions 
La disponibilité (mesure du temps accessible)
La haute disponibilité (limiter l’interruption)
La continuité d’activité (maintenir les activités prioritaires)
La reprise d’activité (restaurer après sinistre)

Disponibilité: 
- question centrale: Le service est-il accessible lorsqu'il doit l'être? 
- Exemple: Portail accessible 99,9% du temps prévu 

Haute disponibilité: 
- question centrale: Comment réduire ou éviter une interruption ?
- Exemple: 2 serveurs web derrière un répartiteur 

Continuité d'activité (PCA):
- Question centrale: Comment l'activitéb essentielle continue-t-elle pendant une crise ? 
- Exemple: Accueil des usagers maintenu avec une procédure papier temporaire ?

Reprise d'activité (PRA): 
- question centrale: Comment revenir à une situation normale après un sinistre majeur
- Exemple: Restaurer l'application et les données sur une infrastructure de secours 

# La haute disponiblité d'un service 
La « haute disponibilité » (en anglais « high availability ») regroupe de nombreuses techniques et processus visant à atteindre un certain pourcentage de disponibilité d'un service.
Par exemple, un taux de 99 % de disponibilité assure une disponibilité d'environ 361 jours sur 365 alors qu'un taux de 99,5 % assure une disponibilité de plus de 363 jours sur 365.
La réalité économique fait que les organisations tendent de plus en plus vers des taux encore plus grands comme 99,9 % ou 99,99 % et même 99,999%, notamment sur certains services critiques.

# Mesures du taux de disponibilité

- Disponibilité en %: 90% ("1 neuf"), 95%, 98%, 99% ("2 neuf"), 99,5%, 99,8%, 99,9% ("3 neuf") 99,95%, 99,99 ("4 neuf"), 99,999% ("5 neuf"), 99, 9999% ("6 neuf")
- Indisponibilité par année: 36,5j, 18,25j, 7,3j, 3,65j, 1,83j, 17,52h, 8,76h, 4,38h, 52,56min, 5,26min, 31,5s
- Indisponibilité par mois: 72h, 36h, 14,4h, 7,2h, 3,6h, 86,23min, 43,2min, 21,56min, 4,32min, 25,9s, 2,59s 
- Indisponibilité par semaine: 16,8h, 8,4h, 3,36h, 1,68h, 50,4min, 20,16min, 10,1min, 5,04min, 1,01min, 6,05s, 0,605s

# Le SLA
Le SLA (Service Level Agrement), qui peut être traduit par « Accord de Niveau de Service », est un document qui définit la qualité de service. Ce document s’établit entre un fournisseur de service et un client. Le SLA doit comprendre les éléments suivants :
● Le type de service à fournir : il doit spécifier les types de services ainsi que tous les détails de ces derniers : l’utilisation et la maintenance des équipements, la largeur de bande passante, etc.
● Le niveau de performance souhaité des services : sa fiabilité et sa réactivité.
● Les étapes à suivre pour signaler les problèmes du service
● Le temps de réponse et les solutions aux problèmes examinés
● Le suivi des processus et les rapports de niveau de service : comment les niveaux de performance sont supervisés et surveillés.
● Les répercussions pour le fournisseur de services qui ne respecte pas son engagement.

# Préserver une haute disponibilité 
Toutes les entreprises cherchent à améliorer la disponibilité de leur système d'information. Plusieurs facteurs doivent être pris en compte :

● Le matériel
● Le logiciel
● L'environnement et les événements extérieurs
● Les procédures
● L'aspect humain

Préserver une haute disponibilité conformément au standard des cinq neuf peut s'avérer coûteux et consommer de nombreuses ressources : achat de matériel supplémentaire (serveurs, composants, ...). De plus, plus une entreprise ajoute de composants, plus cela augmente la complexité de la configuration et donc les facteurs de risque comme la probabilité de panne.
La haute disponibilité intègre trois principes majeurs pour garantir un accès
ininterrompu aux données et aux services :
● L'élimination ou la réduction des points de défaillance uniques : peut être un commutateur ou un routeur central, un service réseau et même un membre hautement qualifié du personnel informatique
● La résilience du système : capacité à maintenir la disponibilité des données et des processus opérationnels malgré une attaque ou un événement perturbateur
● La tolérance aux pannes : permet à un système de continuer à fonctionner en cas de défaillance d'un ou plusieurs composants.

# Les solutions 
Pour mettre en place de la haute disponibilité, on utilisera en premier lieu la redondance des serveurs et des équipements :
● Le clustering : plusieurs serveurs dans une même grappe
● Le système RAID pour les disques durs
● La redondance des équipements : switchs, routeurs, pare-feu, ...
● La redondance des liens

# Le clustering 
La technologie de clustering permet d'avoir une haute disponibilité des ressources. On utilise cette technologie pour avoir une disponibilité et stabilité des ressources proche de 100% : tolérance zéro pour les pannes matérielles ou logicielles. Il y a également éventuellement une répartition des charges entre les nœuds d'un cluster. Le cluster est une grappe de serveurs, vu comme un seul serveur logique.

# Cluster, noeuds et ressources 
Un serveur dans le cluster est appelé nœud dit node en anglais. Les services sont appelés ressources. Par défaut chaque ressource est attribuée à un nœud ; pour publier un groupe de ressources accessible par les clients externes, il est nécessaire de créer un serveur virtuel en lui adressant une adresse IP virtuelle et un nom d'hôte. Cette IP virtuelle et ce nom d’hôte seront accédés depuis les clients extérieurs au cluster.

# Les apports des clusters 
Haute disponibilité (Availability) des ressources sur le cluster. Dans le cas où un des
nœuds ne pourrait plus fournir des réponses aux requêtes des clients, alors les autres nœuds du cluster prennent le relais
Adaptabilité (Adaptability) : capacité d'un système à s'ajuster et à s'adapter à des
changements dans l'environnement, les exigences ou les conditions d'exploitation sans nécessiter de modifications majeures. 
- Flexibilité logicielle : Capacité à modifier ou à configurer des logiciels pour répondre à de nouveaux besoins sans changements fondamentaux.
- Compatibilité : Intégration facile de nouvelles technologies, protocoles ou mises à jour sans affecter les opérations courantes. 
- Résilience : Capacité à continuer à fonctionner correctement même en cas de changements non prévus ou de perturbations.
- Ex : Un service identique installé sur des serveurs avec OS différent
Évolutivité (Scalability) : L'évolutivité désigne la capacité d'un système à gérer une augmentation (ou une diminution) de la charge de travail en ajustant les ressources disponibles (matériels ou les logiciels).
- Évolutivité verticale (Scale-Up) : Augmentation des capacités d'un serveur en ajoutant plus de ressources (CPU, RAM, stockage) à la même machine.
- Évolutivité horizontale (Scale-Out) : Augmentation des capacités en ajoutant plus de serveurs ou de nœuds pour répartir la charge de travail (exemple : ajout de serveurs à un cluster).
- Ex : Une application web qui doit gérer des pics de trafic importants peut évoluer horizontalement en ajoutant des serveurs supplémentaires pour équilibrer la charge et éviter les ralentissements.

# Le failover 
En cas de défaillance d’un nœud du cluster, il y a un basculement automatique de prise en charge de toutes les ressources vers l'autre nœud du cluster, ce processus est appelé failover.

# Le failback
Après les diverses opérations de maintenance et/ou de remise à niveau sur le nœud hors ligne, la remise en production se fait grâce au procédé de failback. Il est possible de paramétrer l'instant où le serveur sera remis en production dans le cluster. Il est préférable dans le cas d'un failback de restaurer le nœud durant les périodes creuses des entrées sorties sur le cluster, la nuit ou le matin avant l'arrivée des utilisateurs.

# Le type de clusters 
● Le cluster actif / passif
Un nœud est actif pendant que le ou les autres, passifs, sont en sommeil. Il n’y a pas de répartition de la charge de travail entre les serveurs.

● Le cluster actif / actif Tous les nœuds sont actifs. La charge de travail est répartie entre les différents serveurs → permet de gérer la montée en charge. Ce type de cluster est plus complexe à mettre en œuvre : par exemple, gérer la concurrence entre les nœuds pour les BDD.

# La répartition de charge 
Le cluster actif / actif permet de mettre en place de la répartition de charge entre les serveurs du cluster. La répartition de charge, ou load balancing, est « un ensemble de techniques permettant de distribuer une charge de travail entre différents ordinateurs d'un groupe. Ces techniques permettent à la fois de répondre à une charge trop importante d'un service en la répartissant sur plusieurs serveurs, et de réduire l'indisponibilité potentielle de ce service que pourrait provoquer la panne logicielle ou matérielle d'un unique serveur ». La répartition de charge est donc une des technologies qui participe à la haute disponibilité.
Elle est utilisée le plus souvent au niveau des serveurs HTTP (par exemple, sites à forte audience devant pouvoir gérer des centaines de milliers de requêtes par secondes), mais le même principe peut s’appliquer sur n’importe quel service aux utilisateurs ou service réseau.

● Répartition de charge statique : suivant l’adresse IP de la requête, le localisation géographique, … Assez courant pour les serveurs web. Les clients sont toujours associés au même serveur, mais cela peut poser un problème de déséquilibre de charge.

● Répartition de charge dynamique : un répartiteur de charge (load balancer) gère la répartition des requêtes entre les serveurs en suivant un algorithme prédéfini (voir les 3 méthodes suivantes).

# Le Round Robin
Le Round Robin est la première méthode de répartition de charge dynamique. Les requêtes sont envoyées par alternance aux différents nœuds du cluster.

- Le round Robin pondéré
Le Round Robin pondéré est adapté à des serveurs qui n’ont pas la même puissance de traitement. On fixe un pourcentage de requêtes prises en charge par chaque serveur.

- Le least connection 
La répartition des requêtes se fait en analysant la charge de chacun des serveurs.

# Solution logicielle 
HAProxy est le logiciel libre de répartition de charge le plus utilisé. C'est une solution très complète au plan fonctionnel, extrêmement robuste et performante. HAProxy est un relais TCP/HTTP (il fonctionne donc aux niveaux 4 et 7). Il est capable: 
- d'effectuer un aiguillage statique défini par des cookies ; 
- d'effectuer une répartition de charge avec création de cookies pour assurer la persistance de session ;
- de fournir une visibilité externe de son état de santé ; 
- de s'arrêter en douceur sans perte brutale de service ;
- de modifier/ajouter/supprimer des en-têtes dans la requête et la réponse ;
- d'interdire des requêtes qui vérifient certaines conditions ; 
- d'utiliser des serveurs de secours lorsque les serveurs principaux sont hors d'usage ;
- de maintenir des clients sur le bon serveur d'application en fonction de cookies applicatifs ;
- de fournir des rapports d'état en HTML à des utilisateurs authentifiés. 
Il requiert peu de ressources et peut gérer facilement plusieurs milliers de connexions simultanées sur plusieurs relais sans effondrer le système.

# Redondance 
La technologie RAID (Redundant Array of Independent Disks) regroupe plusieurs disques durs physiques au sein d'une seule unité logique afin de fournir une redondance de données et d'améliorer les performances. Si l'un des disques est défaillant, l'utilisateur peut récupérer les données à partir des autres disques sur lesquels elles résident également.
Attention: pas de tolérance aux pannes sur le RAID0. 

# Comparaison des niveaux RAID 
- niveau raid: 0, 1, 5
- Nb min de risques: 2, 2, 3
- Description: Entrelacement des données sans redondance, Mise en miroir de disques, Combinaison de l'entrelacement des données et de la parité
- Avantages: Perfomances maximales, Hautes perfomances, haute protection des données, car toutes les données sont dupliquées, Prend en charge plusieurs requêtes de lecture et d'écriture simultanées, données écrites sur les lecteurs avec parité, possibilité de régénérer des données avec des informations issues des autres disques 
- Inconvénients: Aucune protection des données, une panne d'un disque entraîne la perte de toutes les données, Coût de mise en oeuvre élevé, car un disque supplémentaire d'une capacité équivalente ou supérieure est requis, Les perfomances sont plus lentes qu'en RAID 0 et 1

# Redondance: le doublement des liens 
La redondance des liens améliore la disponibilité de l'infrastructure en supprimant le risque de points de défaillance uniques dans un réseau ; par exemple, une panne d'un commutateur ou d'un câble du réseau. L'établissement d'une redondance physique dans un réseau entraîne l'apparition de boucles et de trames en double. Ceux-ci ont des conséquences désastreuses pour un réseau commuté. Le protocole STP (Spanning Tree Protocol) permet de résoudre ces problèmes. La fonction de base de STP est d'empêcher les boucles dans un réseau lorsque plusieurs chemins connectent les commutateurs entre eux. STP désactive le lien tant qu’il est redondant. 

# Redondance: les routeurs 
La passerelle par défaut est généralement le routeur, qui assure l'accès des appareils au reste du réseau ou à Internet. Si un seul routeur sert de passerelle par défaut, il constitue un point de défaillance unique. L'entreprise peut choisir d'installer un routeur de secours supplémentaire.. Le routeur de transfert et le routeur de secours utilisent un protocole de redondance pour déterminer celui qui doit occuper le rôle actif dans le cadre de la redirection du trafic. Chaque routeur est configuré avec une adresse IP physique et une adresse IP de routeur virtuelle. Les appareils finaux utilisent l'adresse IP virtuelle comme passerelle par défaut.

# Redondance: doubler les emplacements 
Une entreprise peut envisager la mise en œuvre de la redondance d'emplacements, c’est-à-dire la réplication des serveurs sur plusieurs sites. 
- Réplication synchrone : synchronise les deux emplacements en temps réel. Nécessite une bande passante élevée. Les emplacements doivent être proches les uns des autres pour réduire la latence. 
- Réplication asynchrone : la synchronisation ne s'effectue pas en temps réel, mais presque. Nécessite moins de bande passante. Les sites peuvent être plus éloignés, car la latence est un facteur moins important. 
- Réplication ponctuelle : met à jour régulièrement l'emplacement des données de sauvegarde. Option la moins gourmande en termes de bande passante, car elle ne nécessite pas une connexion permanente. 
L'option la mieux adaptée à l'entreprise dépendra du bon compromis entre coût et disponibilité.

# La sauvegarde
La sauvegarde est un élément important de la disponibilité d’un service. Elle permet, en cas de défaillance, de remettre en service le plus rapidement possible ce service, en effectuant une restauration du système et/ou des données.

La sauvegarde permet de respecter le RPO (Recovery Point Objective) ou PDMAen français pour Perte de Données Maximale Admissible. Le RPO quantifie les données que les utilisateurs acceptent de perdre au maximum. Le RTO(Recovery Time Objective) ou DIMA en français pour Délai d’Interruption Maximal Admissible est le délai maximal d’indisponibilité du service, toléré par les utilisateurs de la ressource.

# Sources 
- Chaîne Youtube Cookie connecté : https://www.youtube.com/watch?v=9EoqLdmZCTU  
- Cisco NetAcad cours « Cybersecurity Essentials » 
- Wikipedia : https://fr.wikipedia.org/wiki/Haute_disponibilité