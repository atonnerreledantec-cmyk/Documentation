# Stockage 
1) Le stockage: définition
2) La histoire du stockage 
3) Les 4 types de stockage: DAS, NAS, SAN
4) Les 3 formats de stockage: blocs, fichiers, objets 
5) Le data center, cloud computing et big data 
6) Les différents Cloud: IAAS, CAAS, PAAS, FAAS, SAAS
7) La règle des 6V
8) Données structurées et non structurées 
9) BDD vs Dta Mart vs Data Warehouse vs Data Lake 

# Qu'est-ce que le stockage 
Le stockage des données consiste à recueillir et conserver des informations numériques, c'est-à-dire les octets et bits des applications, protocoles réseau, documents, fichiers multimédias, carnets d'adresses, préférences utilisateur, etc. Le stockage des données est un élément essentiel du Big Data.

# Petite histoire du stockage 
1725, un ouvrier du textile parvient  à programmer des métiers à tisser à l'aide de cartes perforées inspirées des cylindres automatisés qui étaient utilisés dans les boîtes à musique. Les cartes perforées programmaient les ordinateurs jusqu'à l'arrivée des bandes magnétiques au début des années 1950. Ensuite, la taille des bandes magnétiques a progressivement diminué jusqu'à ce qu'elles deviennent des cassettes.
Vers 1970, IBM a lancé la disquette, dont l'utilisation s'est quasiment généralisée. Les disques durs sont devenus des CD (Compact Disk) dans les années 1980 et les disques SSD (Solid State Drive) ont remplacé les disques rotatifs par des circuits électroniques et une mémoire flash. Le stockage flash s'est ensuite glissé dans nos poches puisqu'il permet de conserver des copies de toutes sortes de fichiers.

# 4 types de stockage 
DAAS (Direct Attached Storage): Stockage des partitions systèmes 
SAN (Storage Area Network): Mutualisation évolution pour les données applicatives 
NAS (Network Area Storage): Serveur de fichiers mutualisés
Cloud hybride: Externalisation du stockage 
- Cloud privé: contrôle  du stockage 
- Cloud public: Accessibilité de la donnée scalable 

Les fichiers, les blocs et les objets sont des formats de stockage qui permettent de conserver, d'organiser et de présenter les données de différentes façons, chacun d'entre eux présentant ses propres capacités et limites. Les blocs sont plus rapides, les fichiers plus lisibles et les objets mieux adaptés aux charges de travail à évolution rapide.

# 3 formats de stockage des données 
- Le stockage en mode fichier organise et représente les données sous la forme d'une hiérarchie de fichiers contenus dans des dossiers. C’est un stockage hierarchique. 
Exemple : NAS, cloud  

- Le stockage en mode bloc regroupe les données en volumes de tailles égales, organisés arbitrairement liés à des serveurs .Étant donné que le stockage en mode bloc ne recourt pas à un chemin d'accès unique aux données, à la différence du stockage en mode fichier, les données peuvent être récupérées rapidement. 
Exemple : DAS et SAN, cloud

- Le stockage en mode objet gère les données et les lie aux métadonnées associées. Le stockage en mode objet est une structure plate dans laquelle les fichiers sont décomposés en éléments et répartis sur du matériel conservés dans un référentiel unique. Exemple : data lake dans le cloud

Le data center les data center hébergent les clouds et le big data. On y retrouve des serveurs très perfomants, baies de stockage, low balancer, parefeu, switch, routeur, proxy... Google, Facebook, Amazon, Apple en ont un. 

Le cloud computing répond à la croissance considérable des données (augmentation de 100 % par an). Les services y sont payés en fonction de leur consommation. Pour répondre aux problématiques big data, l’architecture de stockage des systèmes doit être repensée et les modèles de stockage se multiplient en conséquence.

# Différents modèles de Cloud 
- IAAS (Infrastructure as a service):
 - Pris en charge par le client:
  - Applications 
  - Runtimes/Middlewares
  - Conteneurs 
  - OS
 - Pris en charge par le fournisseur Cloud:
  - Serveurs 
  - Stockage 
  - Réseau

- CAAS (Containers as a service):
 - Pris en charge par le client: 
  - Applications 
  - Runtimes/Middlewares
 - Pris en charge par le fournisseur cloud:
  - Conteneurs 
  - OS
  - Serveurs 
  - Stockage 
  - Réseau

- PAAS (Platform as a service): 
 - Pris en cahrge par le client:
  - Fonctions 
  - Applications 
 - Pris en charge par le fournisseur Cloud: 
  - Runtimes/Middlewares
  - Conteneurs 
  - OS
  - Serveurs 
  - Stockage
  - Réseau

- FAAS (function as a service): 
 - Pris en charge par le client:
  - Fonctions
 - Pris en charge par le fournisseur Cloud: 
  - Applications 
  - Runtimes/Middlewares
  - Conteneurs 
  - OS
  - Serveurs 
  - Stockage 
  - Réseau

- SAAS
 - Pris en charge par le fournisseur Cloud: 
  - Fonctions
  - Applications 
  - Runtimes/Middlewares
  - Conteneurs 
  - OS 
  - Serveurs 
  - Stockage 
  - Réseau

- Le IAAS  offre des ressources d’infrastructure hautement scalables
- Le CAAS permet de gérer les applications conteneurisées (déploiement et cycle de vie par dockers (middleware : communication, répartition de charge, cycle de démarrage, sevices...))
- Le PAAS offre un ensemble de composants techniques pour faciliter le développement d’applications (serveur web, sgbd...l’application tourne en continue) 
- Le FAAS permet de gérer d’exécuter des fonctions (serverless, l’application doit être sollicitée) 
- Le SAAS mets à disposition des applications « prêtes à l’emploi » (google doc, office365..)

# La règle des 6V pour stocker les données
Le big data s'accompagne du développement d'applications à visée analytique, qui traitent les données pour en tirer du sens en répondant au 6V:
- volumétrie: Le volume des données stockées est en pleine expansion : les données numériques créées dans le monde seraient passées de 1,2 zettaoctet (10^21 octets) par an en 2010 à 47 zettaoctets en 2020, et 2 142 zettaoctets en 2035
- vélocité:  La vélocité représente la fréquence à laquelle les données sont à la fois engendrées, capturées, partagées, utilisées et mises à jour.
- variété: Il ne s'agit pas uniquement de données relationnelles traditionnelles, mais surtout de données brutes, semi-structurées, voire non structurées (cependant, les données non structurées devront être analysées et structurées ultérieurement si nécessaire pour leur utilisation)
- véracité:  La véracité fait référence à la fiabilité et à la dimension qualitative des données. Traiter et gérer l’incertitude et les erreurs rencontrées dans certaines données, représente un challenge de taille pour fiabiliser et minimiser les biais.
- valeur: Les efforts et les investissements dans l'utilisation et application Big Data n’ont de sens que si elles apportent de la valeur ajoutée.
- visualisation: La mise en forme et mise à disposition des données et des résultats de l'analyse des données, permet de faciliter sa compréhension et son interprétation, afin d'améliorer la prise de décisions.

# Données structurées et non structurées 
On distingue les données structurées qui correspondent aux éléments calibrés saisis dans les différents champs des bases de données, et les données non structurées qui englobent toutes les autres informations enregistrées sous forme numérique ; Parmi les exemples de données non structurées les plus courants figurent les rapports, les fichiers audio, les images, les fichiers vidéo, les fichiers texte, les commentaires et opinions sur les réseaux sociaux, les emaills, etc. 
Les données structurées sont généralement stockées dans des data warehouses et les données non structurées dans des data lakes.

# BDD vs data Warehouse vs data Mart vs data lake
Les bases de données gèrent des données sructurées 
Les data Warehouse entrepôt central de données d'une entreprise permettent le stockage, l'extraction et l'exploitation des données. 

- Un Data Warehouse est une base de données relationnelle hébergée sur un serveur dans un Data Center ou dans le Cloud. Il recueille des données de sources variées et hétérogènes dans le but principal de soutenir l'analyse et faciliter le processus de prise de décision. En matière d’intégration dans le système de données existant, le fonctionnement du Data Warehouse est basé sur le processus ETL (Extract, Tranform, Load) permettant de charger les données issues des différentes applications. Un data mart (magazin de données) transporte des données liées à un département, telles que les RH, le marketing, le financier...

- Un data lake est un type de référentiel de données qui permet de stocker de gros volumes de données brutes et hétérogènes dans leur format natif. Les data lakes vous permettent de conserver une vision brute de vos données. Ils sont de plus en plus utilisés comme stratégie de gestion des données par les entreprises qui souhaitent posséder un référentiel de données plus vaste et global. 
Le Data lake est très puissant mais pose des soucis point de vue développement, durable, RGPD, sécurité..Il doit être bien gouverné pour ne pas finir en marécage de données inutilisables (data swamp). Le data réservoir comprend une fonction de gouvernance (6V)
