# qu'est-ce que le DNS ? 
Sur Internet, une machine est identifiée de manière unique par son adresse IP: il est donc nécessaire d'utiliser un annuaire "Adresse IP/Nom"
- Au début (70-84): l'annuaire complet est dans un fichier texte (/etc/hosts sous UNIX): aujourd'hui ce fichier est encore utilisé pour l'annuaire local
- 1984: mise en place du DNS géré au niveau mondial par Network Information Center (NIC). En France, l'organisation gérante est l'Association Française pour le Nommage Internet en Coopération(AFNIC)

# Particularités du DNS 
- Le DNS est dynamique: les enregistrements doivent pouvoir être ajoutés de façon unique dans le système, et devenir rapidement disponibles pour tous. 
- Le DNS est répliqué: on ne peut se permettre d'un seul serveur, les informations existent en plusieurs exemplaires. 
- Le DNS est hiérarchisé: les informations sont classées en une arborescence qui permet leur organisation. Chaque niveau de la hiérarchie est appelée "zone", et le sommet de cette hiérarchie est la zone "."
- Le DNS est distribué: les informations sont réparties en une multitude de "sous-bases" (les zones DNS), et l'ensemble de ces petites bases d'informations compose l'intégralité des enregistrements DNS. Ce fonctionnement a l'avantage de faciliter l'administration en répartissant la charge sur des milliers de serveurs 
- Le DNS est sécurisé: de plus en plus implémenté sur tous les erveurs DNS. On a désormais la possibilité de sécuriser de bout en bout les opérations du DNS. Les services de sécurité disponibles sont l'authentification., le contrôle d'accès et le contrôle d'intégrité. 

# L'arborescence hiérachique
Le système de noms DNS se présente sous forme d'un arbre inversé avec pour sommet "la racine" et un ensemble de nœuds représentant des domaines identifiés par un label (fr, education.fr, org, com, etc.).Un serveur de noms particulier s'occupe d'un nœud de l'arborescence ou d'un ensemble de nœuds sur lequel il aura autorité. On dit que le serveur gère une zone d'autorité. C'est à dire qu'il gérera l'attribution des noms et résoudra les noms via une base de données (matérialisée par ce qu'on appelle un fichier de zone) distincte pour chaque nœud. Chaque information élémentaire de la base de données DNS est un objet appelé "resource record" (RR).
Un nœud peut contenir aussi bien des domaines que des noms de machines.

Exemple: quel serveur va résoudre le nom d'hôte pleinemengt qualifié "serveurWeb.educnet.education.fr" ? 
le serveur racine où se trouve cet hôte, par contre il possède un enregistrement pour le domaine "fr". 
La zone "fr" est aussi restreinte au nœud correspondant. Son fichier de zone inclut donc des informations sur les délégations de gestion du reste du domaine dont le domaine "education".
Le fichier de zone "education.fr" peut éventuellement posséder un enregistrement pour cet hôte car il est possible qu'une zone d'autorité comprenne un domaine et un sous-domaine. Mais nous supposerons ici que la gestion des noms a été déléguée. Le fichier de zone correspondant contient donc les informations nécessaires pour résoudre des noms dans cette zone (tel que serv1.education.fr) et les informations sur la délégation de la zone "educnet.education.fr".
Le fichier de zone "educnet.education.fr" possède l'information concernant l'hôte "serveurWeb" et pourra ainsi résoudre le nom serveurWeb.educnet.education.fr.

# Les root-servers
13 serveurs appelés root-servers contiennent les références de tous les serveurs de premier niveau (Top Level Domain).

# Les erveurs TLD 
Ces serveurs savent dire quels sont les serveurs qui gèrent un domaine appartenant à ce TLD. C'est à ce niveau que le registar intervient techniquement. Une fois le nom de domaine enregistré, le demandeur doit fournir l'adresse d'au moins un serveur qui saura résoudre les noms dans le domaine en question. 
- TLD par pays: ccTLD (country code TLD), ex: .fr, .ru, .eu, .be, ...
- TLD internationaux: gTLD (generic internationaux TLD) ex: .com (entreprise multinationale), .org (organisation), .edu (université), .net (fournisseur d'accès) , .pro (profession libérale), .aero, .biz, .coop, .info, .museum, .name, .pro
Fin 2013, Internet a connu une nouvelle transformation importante. À l'initiative de l'Icann, l'organisme qui régule l'attribution des noms de domaine, des centaines de nouvelles extensions ont vu le jour, une multitude d'extensions génériques (.cloud, .restaurant, .taxi…), géographiques (.bzh, .alsace, .corsica, .tokyo…) ou relatives à des marques (.apple, .ferrari, .sony…).

L'ICANN: organisme international en charge des noms de domaine génériques et de la racine du système des noms de domaine.
L'ICANN est un organisme qui gère la liste des Top Level Domain (TLD): .com, .net, .org, .fr, .uk, ...
L'ICANN délègue la gestion de chaque TLD à un organisme (appelé registry).

# FQDN (Full Qualified Domaiu Name)
www.education.gouv.fr est un FQDN. En toute rigueur, il serait plus correct d'écrire www.education.gouv.fr. (avec un point final, subtile différence). 
- la partie la plus à gauche représente toujours un hôte (une machine), (ici www).
- la partie la plus à droite représente toujours un domaine générique (ici fr.).
- entre les deux, les éventuels sous-domaines et le domaine déposé de l'entité concernée (ici un sous-domaine education et un domaine gouv). 
Nous avons donc une structure arborescence dont l'origine est le fameux point final qui représente la racine de l'arbre. 
- www: hôte
- education.: sous-domaine du domaine déposé 
- gouv.: domaine déposé
- fr.: domaine générique (TLD)

# Le principe de fonctionnement 
Un client DNS s'appuie sur un composant logiciel appelé "resolver" qui interroge un serveur DNS "de proximité" serveur DNS local à l'entreprise, DNS FAI

# Mode récursif et itératif 
- DNS d'attachement: Rôle: c'est le serveur qui stocke les enregistrements officiels d'un domaine (ex: lechat.ai). Il répond aux requêtes des DNS récursifs en donnant l'adresse IP exacte du site. Exemples: les serveurs DNS de ton hébergeur (OVH, Gandi, cloudflare, etc.). Les serveurs DNS de Google Domains: Amazon Route 53, etc.
- DNS de rattachement: Un DNS de rattachement peut avoir un mode de fonctionnement itératif ou récursif. Dans le mode récursif, le DNS de rattachement interroge les serveurs racine, connus de tous les DNS, pour obtenir l'adresse des DNS de zone, eux-même connus des DNS racines. Puis il interroge le 1er DNS racine interrogé, qui lui donne alors l'adresse du DNS autoritaire.l'interrogation du DNS autoritaire permet de récupérer l'adresse IP et de la remettre au navigateur. Dans le mode itératif, ça fonctionne à peu près semblablement, mais le DNS de rattachement se contente de remettre les résultats intermédiares au navigateur qui assure alors lui-même l'enchaînement des interrogations. 

# DNS récursif 
Rôle: C'est le serveur qui recherche l'adresse IP correspondant à un nom de domaine pour l'utilisateur. Il interagit avec d'autres serveurs DNS (autoritaires) pour obtenir la réponse. 
Exemple de DNS récursifs: Les DNS récursifs grand public les plus connus et utilisés sont généralement proposés par des acteurs majeurs du web et de la sécurité. 

# DNS d'attachement 
Rôle: C'est le serveur qui stocke les enregistrements officiels d'un domaine (ex:lechat.ai). Il répond aux requêtes des DNS récursifs en donnant l'adresse IP exacte du site. 
Exemple: Les serveurs DNS de ton hébergeur (OVH, Gandi, Cloudflare, etc.). Les serveurs DNS de Google Doamins, Amazon Route 53, etc.

# Comment acheter un nom de domaine 
- Vérifier la disponibilité du nom de domaine (site AFNIC)
- Acheter un nom de doamine chez un bureau d'enregistrement accrédité par l'AFNIC 
- Pour savoir si vous êtes réellement propriétaire de votre domaine, faites un whois 
- Méfiance avec les noms de domaine gratuits. Généralement, ils ne peuvent pas être gratuits, il doit y avoir une contrepartie (souscription à un autre service payant, gratuité provisoire, superposition de publicités, blocage d'adresse, ou redircetion)
- Dans les URL visibles dans votre navigateur, le nom de domaine est le mot qui précède immédiatement le TLD (.com, .net, .org, ...) avant le premier slash (/). Ne vous faites pas abuser !
- Les domaines ne sont pas attribuées à vie. Ce ne sont que des locations, à renouveler. Certains louent des noms de domaine à l'année, d'autres pour 10 ans. Si vous avez un nom de domaine, n'oubliez pas de le renouveler !

# Mettre en place son propre nom de domaine 
4 étapes: 
- Acheter un nom de domaine 
- Faire héberger ses DNS: vous devrez fournir à votre registrar l'adresse IP de 2 serveurs DNS qui répondront aux requêtes concernant votre domaine. Plusieurs possibilités: 
 - chez votre registrar: Beaucoup de registrars proposent d'héberger (à titre payant ou gracieux) vos DNS. C'set souvent la solution la plus rapide à mettre en place 
 - chez votre hébergeur HTTP: Certains hébergeurs HTTP proposent également d'héberger aussi vos DNS, mais c'est rarement le cas des hébergeurs gratuits. 
 - chez un hébergeur de DNS: On peut trouver de nombreux hébergeurs spécialisés DNS dont certains sont gratuits, comme http://www.mydomain.com
 - chez vous, à condition d'avoir au minimum 2 serveurs DNS avec adresses IP fixes connectés en permanence. 
- Faire héberger son site web (HTTP)
- Mettre en place la redirection afin que www.votredoamine.com arrive bien 

L’ICANN a alerté sur de potentielles attaques informatiques visant le système des noms de domaine et consistant à modifier des informations importantes dans ce système (adresses de sites internet pour les pirater, serveur de messagerie …).
Les conséquences peuvent être lourdes. D’une part, les sites touchés peuvent être atteints de « détournement », piratage ou de défiguration (« defacing »), c’est-à-dire, avec un contenu originel remplacé par un contenu contrôlé par l’attaquant. D’autre part, les cybercriminels peuvent récupérer des données sensibles de l’organisme responsable du site et/ou sur les utilisateurs de ce dernier.

L’Afnic, association française pour le nommage Internet, rappelle que des outils préventifs existent, en l’occurrence le verrou de registre et le DNSSEC :
- L'AFNIC propose de verrouiller le nom de domaine au niveau du registre, érigeant une barrière de sécurité supplémentaire en ajoutant des étapes nécessaires de validation (intervention humaine) au moment de faire des changements (Le FR-LOCK, ou verrou de registre est d'ailleurs recommandé par l'ANSSI).
- Le DNSSEC  (Domain Name System Security Extensions) est un renforcement de la sécurité du DNS. Le DNSSEC permet de valider l'authenticité de l'origine des données, par le biais de mécanismes cryptographiques, permettant ainsi de s'assurer qu'on accède au bon service numérique, comme par exemple naviguer sur le bon site web ou s'adresser au bon serveur de messagerie. 