## Le pare-feu 

# Qu'est-ce qu'un pare-feu ?
Un pare-feu (de l'anglais firewall) est un logiciel et/ou un matériel permettant de faire respecter la politique de sécurité du réseau, celle-ci définissant quels sont les types de communications autorisés sur ce réseau informatique. 
# Un pare-feu surveille et contrôle les applications et les flux de données (paquets).
Il peut être comparé à un sas de sécurité : point de passage obligé, nul individu ne peut pénétrer ou sortir de la zone dans laquelle il se situe sans autorisation préalable. Tous les pare-feux du marché, qu'ils soient logiques ou matériels, fonctionnent selon des règles similaires, à savoir:
- Autoriser ou refuser une entrée ou une sortie
- Autoriser certaines demandes entrantes ou sortantes car il s'agit d'un invdividu ou d'un élément connu, sans risque et/ou nécessaire au bon fonctionnement. 

# Architecture réseau 
Il existe plusieurs zones de sécurité commune aux réseaux. Ces zones déterminent un niveau de sécurité. On considère en général trois zones ou réseaux: 
- réseaux externes (extranet): réseau généralement le plus ouvert (Internet par exemple). L'entreprise n'a pas ou très peu de contrôle sur les informations, les systèmes et les équipements qui se trouvent dans ce domaine. 
- réseaux internes (intranet): les éléments de ce réseau doivent être sérieusement protégés.Les mesures de sécurité y sont les plus restrictives et c'est donc le réseau le moins ouvert. 
- réseaux intermédiaires (DMZ): ce réseau est composé de services fournis aux réseaux internes et externes. Les services publiquement accessibles (serveurs de messageries, Web, FTP et DNS le plus souvent) sont destinés aux utilisateurs internes et aux utilisateurs par Intenet. Cette zone, appelée réseau de services ou de zone démilitarisée DMZ (De-Militarized Zone), est considérée comme la zone moins protégée de tout le réseau. 

# Comment fonctionne un pare-feu
Les politiques de sécurité sont au nombre de 2 et peuvent se résumer de la manière suivante: 
- Tout ce qui n'est pas explicitement interdit est autorisé à franchir le sas 
- tout ce qui n'est pas explicetement autorisé est interdit de passage 

Dans un cadre sécuritaire, il est toujours préférable de recourir au second choix (b). Les pare-feux dits "personnels" emploient généralement cette "politique du moindre privilège", c'est-à-dire qu'ils émettent une alerte pour toute tentative de connexion entrante ou sortante non autorisée. Il convient dès lors à l'utilisateur de l'ordinateur de décider de l'action à mener : autoriser ou refuser l'accès et ceci, de manière occasionnelle ou permanente.

le filtrage se fait selon divers critères. Les plus courants sont: l'origine ou la destination des paquets (adresse IP, ports TCP ou UDP, interface réseau, etc.).
- les options contenues dans les données (fragmentation, validité, etc.)
- les données elles-mêmes(taille, correspondance à un motif, etc.)
- les utilisateurs pour les plus récents
Un pare-feu fait souvent office de routeur et permet ainsi d'isoler le réseau en plusieurs zones de sécurité appelées zones démilitarisées ou DMZ. Ces zones sont séparées suivant le niveau de confiance qu'on leur porte. 

# Les différents types de pare-feu
le pare-feu joue le rôle de filtre et peut donc intervenir à plusieurs niveaux du modèle à couches. Il existe 3 types principaux de pare-feu:
- le filtrage simple de paquets (firewall stateless)
- le filtrage de paquets avec état (firewall stateful)
- le proxy applicatif

# Le filtrage simple de paquets (firewall stateless)
C'est la méthode de filtrage la plus simple, elle opère au niveau des couche réseaux et transport du modèle OSI. La plupart des routeurs permettent d'effectuer du filtrage simple de paquet. Cela consiste à accorder ou refuser le passage de paquet d'un réseau à un autre en se basant sur:
- L'adresse IP Source/Destination 
- Le numéro de port Source/Destination 
- Et bien sur le protocole 3 ou 4.
Cela nécessite de configurer le pare-feu ou le routeur par des règles de filtrages, généralement appelées des ACL (Access Control Lists). Les limites de cette technique: 
- défense simple et efficace, mais manque de souplesse: l'administrateur est rapidement contraint à autoriser trop d'accès et le pare-feu perd son efficacité;
- Difficulté pour gérer certains protocoles: FTP (complexité des échanges FTP) ou TCP (protocole de type connecté).

Les ports reconnus (dont le numéro est compris entre 0 et 1023) sont associés à des services courants (les ports 25 et 110 sont par exemple associés au courrier électronique, et le port 80 au Web). La plupart des dispositifs pare-feu sont au minimum configurés de marière à filtrer les communications selon le port utilisé. 

# Le filtrage de paquets avec état (firewall stateful)
L’amélioration par rapport au filtrage simple, est la conservation de la trace des sessions et des connexions dans des tables d’états internes au Firewall. Le Firewall prend alors ses décisions en fonction des états de connexions. Ce filtrage permet aussi de se protéger face à certains types d’attaques DoS. Si les ACL autorisent, par exemple, un paquet UDP caractérisé par un quadruplet (ip_src, port_src, ip_dst, port_dst) à passer, un tel pare-feu autorisera la réponse caractérisée par un quadruplet inversé, sans avoir à écrire une ACL inverse. Ceci est fondamental pour le bon fonctionnement de tous les protocoles fondés sur l'UDP, comme DNS par exemple.

Le pare-feu stateful est cinsidéré comme la technologie minimum pour une sécurisation. 

Pour le protocole FTP (et les protocoles fonctionnant de la même façon), c'est plus délicat puisqu'il va falloir gérer l'état de deux connexions : le canal de contrôle établi par le client, et le canal de données établi par le serveur. Ce qui implique que le pare-feu connaisse le protocole FTP, et tous les protocoles fonctionnant sur le même principe. Cette technique est connue sous le nom de filtrage dynamique (Stateful Inspection).

# Le pare-feu de type proxy (ou passerelle applicative)
Le filtrage applicatif est comme son nom l'indique réalisé au niveau de la couche Application. Les requêtes sont traitées par des processus dédiés, par exemple une requête de type HTTP sera filtrée par un processus proxy HTTP. Le pare-feu rejettera toutes les requêtes qui ne sont pas conformes aux spécifications du protocole. Cela implique que le pare-feu proxy connaisse toutes les règles protocolaires des protocoles qu'il doit filtrer.
Le filtrage applicatif apporte plus de sécurité que le filtrage de paquet avec état, mais cela se paie en performance. Ce qui exclut l’utilisation d’une technologie 100 % proxy pour les réseaux à gros trafic. Néanmoins d’ici quelques années, le problème technologique sera sans doute résolu.

# Autre possibilités du pare-feu: le NAT
La traduction d’adresse réseau NAT (Network Address Translation) est un service proposé par les pare-feux. Le routeur du pare-feu établit et maintient une correspondance entre les adresses internes (généralement privées) et une ou plusieurs adresses publiques. Cette correspondance peut être statique ou bien réalisée dynamiquement par l’équipement. Dans ce cas, le nombre d’hôtes pouvant sortir simultanément est limité par le nombre d’adresses publiques utilisables.

# Le PAT-Port Address Translation 
Pour contourner la limitation qui précède, la correspondance n’est plus établi sur la simple adresse IP mais utilise un couple adresse IP/port (TCP/UDP) ou adresse IP/ID (ICMP). C’est une technique couramment utilisée pour connecter un réseau à l’aide d’une unique machine ayant un compte chez un FAI.
 
# Exemples de pare-feu logiciels
- pfSense est un routeur/pare-feu open source basé sur le système d'exploitation FreeBSD. Il utilise le pare-feu à états Packet Filter (Firewall Stateful), des fonctions de routage et de NAT lui permettant de connecter plusieurs réseaux informatiques.
- OPNSense, fork de pfSense 
- Windows Firewall
- Zone Alarm
- Comodo Firewall Pro

# Les pare-feu matériels
- Firebox de chez Watch Guard
- Appliance Routeurs de chez Netgear 
- Xophos XG Firewall
- Cisco ASA 5500-x
- pfSense firewall appliance 

# Exemples de placement du pare-feu 
- fig 1: pare-feu entre 2 réseaux
- fig 2: pare-feu entre internet et un ordinateur 
- fig 3 : pare-feu entre internet et un réseau local 