# Qu'est-ce qu'un contrôleur de domaine 
un domaine est un ensemble d'objets (machines, utilisateurs) partageant des informations. Ces objets partagent une base de données d'annuaires, des stratégies de sécurité et éventuellement des relations de sécurité communes avec d'autres domaines. Le domaine permet à l'administrateur système de gérer plus efficacement les utilisateurs des stations déployées au sein de l'entreprise, car toutes ces informations sont centralisées dans une même base de données. Le contrôleur de domaine (DC pour Domain Controller) permet de contrôler l'ensemble des ressources (répertoires, fichiers) et équipements (ordinateurs, utilisateurs) d'une entreprise, et assure une sécurité d'accès pour pouvoir les utiliser. Le contrôleur de domaine est un serveur: AD pour Active Directory sous Windows, Samba sous Linux. 

# Le groupe de travail (Workground)
C'est la configuration par défaut d'un système d'exploitation Microsoft: 
- tous les ordinateurs ont le même rôle et peuvent partager des ressources; 
- chaque ordinateur gère ses propres comptes d'utilisateur; pour ouvrir une session, il faut utiliser un compte créé localement sur l'ordinateur. Les comptes sont stockés au niveau de la base de registre dans la SAM (Security Account Manager ou gestionnaire des comptes de sécurité). Sont également enregistrés les mots de passe locaux. 
- cette organisation est possible pour les réseaux d'au moins plus de vingt ordinateurs. 
- tous les ordinateurs doivent se trouver sur le même réseau local ou le même sous-réseau. 

# Le domaine 
Pour gérer un domaine Microsoft, il faut:
- utiliser les versions Serveur de Windows; 
- configurer un ou plusieurs serveurs comme contrôleur de domaine

# Pourquoi utiliser un domaine ? 
Cela permet de centraliser pour tous les ordinateurs du domaine: 
- la gestion des comptes et des groupes d'utilisateurs; 
- la gestion de la sécurité (droits d'administration) et de l'environnement utilisateurs grâce notamment aux Stratégies utilisateur et ordinateur (GPO-Group Policies Object); 
- la gestion des autorisations d'accès aux ressources;

Cela permet de réaliser plus facilement des changements, car ils sont automatiquement appliqués sur tous les ordinateurs. Les utilisateurs d'un domaine doivent fournir une seule fois leur identification et leur mot de passe pour accéder à l'ensemble des ressources du domaine. Les utilisateurs d'un domaine peuvent ouvrir une session sur tous les ordinateurs du domaine, sans nécessiter d'avoir de compte local. Il faut obligatoirement faire adhérer un ordianteur au domaine pour bénéficier de la centralisation de cette gestion. Un domaine peut être constitué de milliers d'ordinateurs et ceux-ci peuvent se trouver sur des réseaux locaux différents. 

# Le contrôleur de domaine 
Lorsque l'on crée un domaine, le serveur depuis lequel on effectue cette création est promu au rôle de "contrôleur de domaine" du domaine crée => il sera au coeur des requêtes à destination de ce domaine. De ce fait, il devra: 
- vérifier les identifications des objets (machines et utilisateurs);
- traiter les demandes d'authentification;
- veiller à l'application des stratégies de groupe (GPO); 
- stocker une copie de l'annuaire Active Directory. 

 Un contrôleur de domaine est indispensable au bon fonctionnement du domaine, si l'on éteint le contrôleur de domaine ou qu'il est corrompu, le domaine devient inutilisable.

# La réplication des contrôleurs de domaine 

- il est important d'avoir au minimum 2 contrôleurs de domaine pour assurer la disponibilité et la continuité de service des services d'annuaire. Les contrôleurs de domaine répliquent les informations entre eux à intervalle régulier, afin de disposer d'un annuaire Active Directory identique. 
- les contrôleurs de domaine répliquent aussi le dossier partagé "SYSVOL" qui est utilisé pour distribuer les stratégies de groupe et les scripts de connexion. 

# Symbolisation d'un domaine 
Lorsque vous verrez des schémas d'architecture Active Directory, vous verrez les domaines "it_connect.local" pourrait être schématisé comme ci-contre:
Domaine: it-connect 

Au sein d'un domaine, on retrouve tout un ensemble d'Unités d'Organisation remplies d'objets de différentes classes: utilisateurs, ordinateurs, groupes, contrôleurs de domaine, etc. 

# Arbre 
Lorsqu'un domaine principal contient plusieurs sous-domaines on parle alors d'arbre, où chaque sous-domaine au domaine racine représente une branche de l'arbre. Un arbre est un regroupement hiérarchique de plusieurs domaines 
Arbre: 
domaine: paris.it-connect.local=>domaine: it.connect.local<=domaine: londres.it-connect.local

# Forêt

- Tous les arbres d'une forêt partagent un schéma d'annuaire commun;
- Les domaines d'une forêt fonctionnent de façon indépendante, mais la forêt facilite les communications entre les domaines, c'est-à-dire dans toute l'architecture; 
- Création de relations entre les différents domaines de la forêt;
- Simplification de l'administration et flexibilité. Un utilisateur du domaine "paris.it-connect.local" pourra accéder à des ressources situées dans le domaine "rennes.learn-online.local" ou se connecter sur une machine du doamine "paris.learn-online.local", si les autorisations le permettent. 

# Active Directory 
L'Active directory est un annuaire LDAP (Lightweight Directory Access Protocol) pour les systèmes d'exploitation Windows. Cet annuaire contient différents objets, de différents types (utilisateurs, ordinateurs, etc.), l'objectif étant de centraliser 2 fonctionnalités essentielles: l'identification et l'authentification au sein d'un système d'information. Le service d'annuaire Active Directory peut être mis en oeuvre sur Windows 2000 Server, Windows Server 2003, Windows Server 2008, Windows Server 2012 et Windows Server 2016. 
Un serveur informatique hébergeant l'annuaire Active Directory est applé "contrôleur de domaine". 

# Que contient l'Acive Directory
Au sein de l'annuaire Active Directory, il y différents types d'objets (utilisateurs, ordinateurs, serveurs, unités d'organisation ou encore les groupes). En fait, ces objets correspondent à des classes, c'est-à-dire une définition d'objets disposants des mêmes attributs. De ce fait, un objet ordianteur sera une instance d'un objet de la classe "ordinateur" avec des valeurs spécifiques à l'objet concerné. 
Certains objets peuvent être des containers d'autres objets, ainsi, les groupes permettront de contenir plusieurs objets de types utilisateurs afin de les regrouper et de simplifier l'administration. Par ailleurs, les unités d'oragnisations sont des containers d'objets afin de faciliter l'organisation de l'annuaire et permettre une organisation avec plusieurs niveaux. Les unités d'organisations sont comme des dossiers qui permettent de ranger les objets à l'intérieur. 

- des serveurs: serveurs de fichiers (destinés à stocker des documents), serveurs d'applications (sur lesquels sont installés les applications à exécuter à partir des stations), serveurs d'impressions, etc. 
- des contrôleurs de domaine: ils sont les seuls habilités à authentifier les utilisateurs qui se connectent au domaine. C'est l'installation d'Active Directory qui fait d'un serveur un contrôleur de domaine. 
- des clients: stations, imprimantes, etc. 
- des utilisateurs: chaque utilsateur a un certain nombre d'attributs et son propre UID (User Identity: un numéro de code qui lui permet d'être identifié sur le domaine) Son UPN (User Principal Name) est du type utilsateur@mondomaine.local

- des groupes: ils peuvent contenir des utilisateurs, des ordinateurs et d'autres groupes. Les groupes simplifient la gestion d'un grand nombre d'objets. 
- des stratégies de groupe: elles définissent le comportement du domaine pour tel ou tel utilisateur ou groupe d'utilisateur ou ordinateurs. Vous les utiliserez pour gérer les stations Windows XP et ultérieur. 
- des Unités d'organisation: vous créez des unités d'organisation pour ranger des objets dans une hiérarchie logique et ordonée. Les différents OU contiennent des ordinateurs, des utilisateurs, des groupes d'utilisateurs, des imprimantes, etc... Ce sont donc des conteneurs d'objets destinés à l'administration, pas des groupes d'utilisateurs !

# L'annuaire LDAP
Notre AD est un annuaire LDAP. LDAP est un protocole réseau (couche 7 du modèle OSI, ports TCP 389 et 636  en SSL) pour obtenir des informations sur des objets tels que les utilisateurs de l'entreprise. LDAP fournit à l'utilisateur des méthodes lui permettant de:
- se connecter 
- se déconnecter 
- rechercher des informations 
- comparer des informations 
- insérer des entrées 
- modifier des entrées 
- supprimer des entrées 

Le nommage des éléments constituant l'arbre (racine, branches, feuilles) reflète souvent le modèle politique, géo ou d'organisation de la structure représentée. La tendance actuelle est d'utiliser le nommage DNS pour les éléments de base de l'annuaire (racine et 1ères branches, domain components ou dc=...). Les racines plus profondes de l'annuaire peuvent représenter des unités d'organisation ou des groupes (orgazationnal unitsou ou=...), des personnes (common name ou cn=... ou user identifier uid=...). L'assemblage de tous les composants (du plus précis au plus général) d'un nom forme son distinguished name, l'exemple suivant en présente deux/ 

- cn=ordinateur, ou=machines, dc=EXEMPLE, dc=FR
- cn=Jean, ou=personnes, dc=EXEMPLE, dc=FR

# AD: la gestion des utilisateurs ou ordinateurs 
La console "Utilisateurs et ordinateurs Active Directory" contient les dossiers suivants: 
- le dossier Builtin contient les groupes par défaut avec une étendue de domaine local
- le dossier Computers contient les comptes d'ordinateurs des stations clientes appartenant au doamine 
- le dossier Domain Controllers contient les contrôleurs du domaine 
- le dossier Users est le conteneur par défaut des utilisateurs du doamine 

# AD: les profils d'utilisateurs 
Un profil utilisateur contient toutes les informations qui définissent l'environnement de travail d'un utilisateur:
- le fichier ntuser.dat contenant le profil dans le dossier Documents and settings
- le profil est construit localement la 1ère fois à partir du profil Default user

Le profil errant: il s'agit de retrouver son profil sur n'importe quelle station. Pour cela il faut modifier les propriétés du compte en indiquant dans l'onglet Profil le chemin réseau UNC existant (utilisation de la variable %username% pour la création automatique du dossier \\serveur\profiles\%username%). Il est possible d'imposer un profil errant (obli) en renommant ntuser.dat en ntuser.man. Le répertoire de base (dossier personnel) peut être créé automatiquement en utilisant la variable %username% sur les partitions NTFS (Autorisation Contrôle Total pour l'administrateur et l'utilisateur). 

# Ad: les groupes utilisateurs 
Les groupes d'utilisateurs permettent de rassembler des utilisateurs devant bénéficier des mêmes droits ou autorisations. Il existe 2 types de groupe: 
- les groupes de sécurité pour gérer l'accès aux ressources et que vous allez utiliser; 
- les groupes de distribution (pour envoyer des messages à plusieurs utilisateurs avec le logiciel de messagerie Exchange). 

Les membres d'un groupe possèdent les droits et autorisations accordés au groupe. Un utilisateur peut être membre de plusieurs groupes. 

# Exemple d'utilisation des groupes 
- Comptabilités: étendue "doamine local" sur "paris.it-connect.local"
- Direction: étendue "globale" sur "learn-online.local" qui approuve tous les ss-domaines
- Informatique: étendue "universelle" sur la forêt

# les groupes prédifinis 
- Opérateurs de compte: Les membres de ce groupe peuvent administrer les comptes d'utilisateurs et les groupes (ajouter, supprimer et modifier). Ils ne peuvent cependant pas toucher au compte Administrateur ni aux autres membres du groupe Opérateurs de compte.
- Opérateurs de serveur: Les membres de ce groupe peuvent partager des ressources ainsi qu'effectuer des sauvegardes et des restaurations sur des contrôleurs de domaine. 
- Opérateurs d'impression: Les membres de ce groupe peuvent gérer les imprimantes réseau des contrôleurs de domaine. 
- Opérateurs de sauvegarde: Les membres de ce groupe peuvent effectuer des sauvegardes et restaurations sur tout contrôleur de domaine. 
- Administrateurs: Les membres de ce groupe peuvent administrer les contrôleurs de domaine ainsi que toute station ayant intégré le domaine. Par défaut, le groupe global Administrateurs de domaine ainsi que le compte Administrateur font partie du groupe local Administrateurs. 
- Invités: Le groupe global Invités du domaine ainsi que le compte d'utilisateur Invité sont intégrés dans ce groupe. Les membres de ce dernier disposent de peu de droits. 
- Utilisateurs: Le groupe global du domaine utilisateur est intégré dans ce groupe. Ce groupe peut être utilisé pour affecter des droits et permissions à toute personne disposant d'un compte dans le domaine.
- Invités du domaine: Le compte d'utilisateur Invité est automatiquement intégré à ce groupe. De plus, ce groupe global est lui aussi automatiquement intégré dans le groupe local du domaine Invités. 
- Utilisateurs du domaine: Tous les comptes d'utilisateurs que vous créez font partie de ce groupe. Ils ne peuvent effectuer que des tâches que vous avez spécifiées et n'ont accès qu'aux ressources auxquelles vous avez attribué des permissions. Ce compte est automatiquement intégré au groupe local du domaine Utilisateurs. Tout utilisateur créé dans le domaine est automatiquement inséré dans ce groupe. 
- Administrateurs du domaine: Le compte administrateur fait partie de ce groupe, qui est intégré au groupe local du domaine Administrateurs. En fait, le compte d'utilisateur Administrateur ne possède pas de droit particulier en tant que compte. C'est le fait de l'intégrer dans ce groupe global qui lui-même fait partie du groupe local du domaine Administrateurs qui lui donne ses droits.
- Contrôleurs de domaine: Ce groupe contient les comptes d'ordinateur contrôleurs de domaine du domaine. 

# les groupes spéciaux
- Tout le monde: Comprend tous les utilisateurs, ceux que vous avez créés, le compte Invité ainsi que tous les utilisateurs des autres domaines.Attention, lorsque vous partagez une ressource, ce groupe dispose par défaut de la permission Lecture sur le partage CT pour Windows 2003. 
- Utilisateurs authentifiés: Comprend tout utilisateur possédant un compte d'utilisateur et un mot de passe pour la machine locale ou Active Directory. Affectez des permissions à ce groupe plutôt qu'au groupe Tout le monde.
- Créateur propriétaire: Toute personne ayant créé ou pris possession d'une ressource, fait partie de ce groupe pour la ressource concernée. Le propriétaire d'une ressource dispose des pleins pouvoirs sur cette dernière. 
- Réseau: Comprend toute personne accédant via le réseau à une ressource. 
- Interactif: Comprend tous les utilisateurs qui ont ouvert une session localement (dans le cas où vous utilisez le « bureau à distance » ce groupe comporte tous les utilisateurs ayant ouvert une session sur le serveur de terminal).

# les stratégies de groupe ou GPO 
L'environnement de travail d'un utilisateur est caractérisé par les différents éléments qui apparaissent à l'écran ou dans les menus (couleurs du fonds d'écran, icônes sur le bureau, personnalisation du menu Démarrer, raccourcis, lecteurs réseaux...). Cet environnement de travail peut être personnalisé à l'aide de scripts (fichiers de commandes du SE: .bat, .cmd, .vbs) ou de programmes exécutables et cela de manière auto et personalisée grâce à des stratégies de groupe. Les stratégies de groupe permettent ainsi d'effectuer de nombreuses tâches d'administration:
- attribuer des scripts d'ouverture et/ou de fermeture de session 
- déployer des applications 
- gérer des mises à jour; 
- etc... 
 
Il s'agit de paramètre applicables à des utilisateurs, des groupes d'utilisateurs ou des ordinateurs. Ces stratégies se définissent au niveau d'un site, d'un doamine, d'une OU. Ce sont des objets d'Active Directory constitués de 2 parties: 
- un conteneur ou un GPC (Group policy object) visualisable avec la fonctionnalité Gestion des stratégies de groupe;
- un GPT (group policy Template) situé dans le répertoire sysvol

Les stratégies de groupe correspondent à des clés du registre qui vont être modifiées ou crées pour être appliquées à la configuration de l'ordinateur ou à l'environnement de l'utilisateur à l'ouverture de session. 