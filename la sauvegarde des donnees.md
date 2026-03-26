## La sauvegarde des données 
- définitions 
- pourquoi sauvegarder ?
- les diffrents types de sauvegarde
- sauvegarde du client ou du serveur 
- Où sauvegarder 
- le bit d'archive ?
- après le crash: le DIMA, le PRA

# Définitions 
la sauvegarde (backup) est l'operation qui consiste a dupliquer et a mettre en sécurité les donnees contenues dans un systeme informatique 

Ce terme est proche de 2 notions:

- l'enregistrement des données: opération d'écriture des donnees sur un support d'enregistrement durable, tel qu'un disque magnetique ou SSD, disque optique, une cle USB, des bandes magnetiques, etc. a des fins de sécurite ou d'hebergement de la donnee vivante, on parle de stockage. 

-l'archivage: consiste enregistrer des donnees sur un support a des fins legales ou historiques. 

l'operation inverse qui consiste a reutiliser des donnees sauvegardees s'appelle une restauration.

## Pourquoi sauvegarder ?
la sauvegarde des donnees preserve l'activite de l'entreprise, notamment en cas de defaillance du systeme informatique. 
L'entreprise peut faire face a plusieurs types de risques qui mettent en danger ses donnees: 
- Risques humains: la perte ou le vol d'un appareil dont les donnees sont liees a celles de l'entreprise, une mauvaise manipulation entrainant l'effacement des donnees sensibles, piratage des donnees. 
- Risques lies a l'environnement: perte de donnees suite a un incendie dans les locaux de l'entreprise (incendies, inondations...)
Risques lies aux dysfonctionnements materiels: perte d'un serveur par exemple. 

## Les causes des pertes de donnees 
- materiels: 44%
- humain: 32%
- corruption: 14%
- virus: 7%
- catastrophe: 3%

# Les enjeux de la sauvegarde 
En cas de donnees , l'impact financier peut etre notable pour l'entreprise en raison de la disparition de fichiers ou d'applications sensibles (base de donnees clients, rapports financiers, etc.) ou de la perte de temps engendree par la remise  en ligne de ces donnees. 
Quels sont les enjeux d'une sauvegarde des donnees pour l'entreprise ? 
- Sauvegarder son image de marque aupres de ses clients ou de ses partenaires; 
- assurer une productivite constante et son chiffre d'affaires; 
- eviter la perte d'informations sensibles: un fichier client en cas de piratage par exemple 

# Pour cela la regle du 3,2,1
au vu de l'importance de certaines donnes sensibles, il est fortement conseille d'appliquer la regle dites "3-2-1" pour les sauvegerdes. Une methode fiable et tres faciles a suivre: 
- Conserver 3 copies de vos fichiers (les fichiers originaux stockes sur le disque dur de l'ordinateur et 2 sauvegardes), 
- sauvegarder les fichiers suer 2 types de supports differents. Il existe en effet de nombreux supports differents pour la sauvegarde de vos donnees (NAS, disques durs externes, memoires flash, bandes magnetiques, DVD, le cloud... )
- conserver dans 1 lieu different 1 copie de sauvegarde hors-site (autre que la maison ou l'entreprise ) 

# Les criteres de choix de la technique de sauvegarde
le choix d'une technique de sauvegarde se fera en prenant en compte:
- la capacite de stockage de support;
- la vitesse de sauvegarde;
- la fiabilite du support (notamment apres une longue periode de stockage)
- la simplicite de classeement;
- la facilite a restaurer les donnees 
- le cout de l'ensemble 

Intervient egalement la possibilite de selectionner les donnees a sauvegarder. Enfin pour les grands systemes de sauvegarde, il faut tenir compte de criteres physiques: 
- volume physique des supports de stockage 
- poids 
- sensibilite a la temperature, a l'humidite, a la poussiere, a la lumiere 

# Les differentes types de sauvegarde
il exite 3 grandes familles de sauvegarde:
- la sauvegarde complete: on effectue une seule sauvegarde, qui comprend tous les fichiers et dossiers;
- la sauvegarde differentielle: consiste a ne pas sauvegarder que les fichiers modifies ou ajoutes, sur la base de la derniere sauvegarde complete effectuee;
- la sauvegarde incrementielle: meme principe que la differentielle sauf qu'elle se base sur la sauvegarde incrementielle precedente, et non sur la sauvegarde complete. 

Indépendamment de la methode utilisee, les fichiers peuvent etre compresses et chiffres lors de la sauvegarde. 

# La sauvegarde complete=full backup
Consiste a copier toutes les donnees a sauvegarder que celles-ci soient recentes, anciennes, modifiees ou non. 
Cette methode est la plus fiable mais elle est longue et res couteuse en termes d'espaces disque, ce qui empeche de l'utiliser en pratique pour toutes les sauvegardes a effectuer 

# La sauvegarde differentielle 
elle effectue une copie crees ou modifies depuis la derniere sauvegarde complete, quelles que soient les sauvegardes intermediaires. Par exemple, sur une semaine:
- lundi: sauvegarde complete 
- mardi, mercredi, jeudi, vendredi, samedi: sauvegarde uniquement des fichiers crees ou modifies depuis la complete. 
Si on souhaite recuperer l'ensemble de la sauvegarde de la semaine, il faudra restaurer simplement le lundi et le samedi qui correspondent a l'ensemble de la semaine. La restauration prendra donc moins de temps, mais cette methode consomme plus d'espace que l'incrementielle, avec ici, un total de 2950 Mo.
# La sauvegarde incrementielle ou incrementale 
Consiste a sauvegarder les fichiers crees ou modifies depuis la derniere sauvegarde quel que soit son type (complete, differentielle ou incrementielle). Par exemple, sur une semaine: 
- Lundi: sauvegarde complete; 
- Mardi: sauvegarde uniquement des nouveaux fichiers crees ou modifies depuis la sauvegarde du lundi;
- Mercredi sauvegarde uniquement des nouveaux fichiers crees ou modifies depuis la sauvegarde du mardi;
Et ainsi de suite jusqu'a la prochaine sauvegarde complete. Pour recuperer l'ensemble de la sauvegarde complete de la semaine, il faudra restaurer tous les elements du lundi au samedi ce qui prendra un certain temps, mais cela reste la methode qui consomme le moins d'espace avec un total de 1750Mo 

# Diffrentiellle/Incrementielle 

- l'incrementielle se base sur la sauvegarde precedente, la differentielle se base sur sa sauvegarde complete.
- l'incrémentielle necessite moins d'espace de stockage, mais demande un temps de restauration plus long. La differentielle necessite plus d'espace de stockage, mais demande un temps de restauration plus court. 

Les logiciels qui proposent de choisir entre differentielle et incrementielle sont generalement utilises dans le monde professionnel comme par exemple Acronis Backup et Symantec Backup Exec ou scriptable avec Rsync et d'autres. 

Pour de la sauvegarde incrementielle uniquement, il existe des tres nombreux programmes et notamment Duplicati: permet de programmer de la sauvegarde incrementielle chiffree en local ou sur un cloud. En plus, il est libre et gratuit, disponible pour Linux, Windows et Mac OSX.

# Le role du bit d'archive 
Pour pouvoir differencier ces differentes methodes de sauvegarde (completes, incrementielle, differentielle) le mecanisme mis en place est l'utilisation d'un marqueur d'archivage, qui est positionné a "vrai" lorsque l'on cree ou modifie un fichier. On peut comprendre cette position comme "Je viens d'etre modifie ou cree: je suis pret a etre archive donc je positionne mon marqueur a vrai". Ce marqueur est appele aussi attribut d'archivage ou bit d'archivage. Sous Windows, cet attribut est modifiable et peut etre visualise par la commande ATTRIB (attribut A pour archive). 

- La sauvegarde differentielle archive tous les fichiers ayant leur attribut d'archivage positionne a 1. par contre, en fin d'execution, elle ne repositionne pas les attributs a 0.
- La sauvegarde incrementielle (ou incrementale) archive tous les fichiers ayant leur attribut d'archivage positionne a 1. En fin de traitement, les attributs d'archive sont tous remis a 0.

# Sauvegarde du client ou du serveur 
Les donnees sur poste client sont reputees moins importantes que les donnees gerees sur des systemes centraux. 
De fait, la sauvegarde des donnees des postes individuels (clients) reste marginale dans la strategie d'utilisation des ordinateurs. Elle est utilisee principalement par les particuliers. 
De plus, la virtualisation des stations de travail va sans doute rendre obsolete les outils classiquement utilises pour sauvegarder les donnees des utilisateurs. 

# Ou sauvegarder ? Poste client et disque externe 
Si l'entreprise compte seulement quelques PC, il est possible de programmer les sauvegardes directement sur les ordinateurs (notion de points de restauration du systeme). Vous devrez zn parallele sauvegarder regulierement vos donnees sur un support amovible (DVD, cle USB, disques durs externes). 

- Avantages: si vous etes mobile, vous pouvez sauvegarder vos donnees n'importe ou.
- Inconvenients: Le point de restauration ne garantit pas la sauvegarde de vos donnees personnelles. La copie des donnees sur support externe est souvent "manuelle" et prend du temps. 

# Ou sauvegarder ? sur serveur ou NAS
Le serveur peut etre dote de nombreux disques durs sur lesquels sont effectuees des sauvegardes quotidiennes. Les sauvegardes peuvent egalement etre faites sur des disques reseaux (NAS pour Network Attached Storage, serveur de stockage en ligne). 

- Avantages: les sauvegardes sont automatiques et sécurisees. Les couts materiels sont relativement faibles. 
- Inconvenients: Lessauvegardes realisees ne se font pas toujours en temps reel (risques de pertes de donnees). La restauration necessite des competences techniques. 

# Ou sauvegarder ? en ligne 
C'est un systeme de sauvegarde de donnees sur internet: l'ordinateur ou reseau est alors connecte a un serveur distant qui effectue des sauvegardes soit en leger decale, soit en temps reel (selon les offres des prestataires). 

- Avantages: La sauvegarde est quasi synchrone (perte de donnees minilmale en cas de problemes). La gestion des donnees en ligne (recuperation, classement) est relativement simple (codes d'acces administrateurs fournis). Vous pouvez stocker un grand volume de donnees (1000 Go et plus).
- Inconvenients: le temps de recuperation des donnees depuis le serveur peut etre assez long (fonction de la connexion internet et du volume d'informations). En cas d'interruption de la connexion internet, les sauvegardes et les recuperations ne sont plus possibles. Enfin, le cout de l'abonnement peut etre eleve. Attention, il est recommande de chiffrer ses donnees !

# La suvegarde des donnees 
Pour garantir la disponibilite des donnees, il faut definir la perte de donnees maximales admissibles en cas d'incident (PDMA=RPO) c'est la duree maximale acceptable entre la derniere sauvegarde et l'incident survenu quantifiant donc la perte de donnees acceptee. 
Le delai maximal d'interruption admissible (DMIA) d'une ressource comprends, le temps de la prise de decision du passage en mode secours apres l'incident, le delai de la relance de la ressource et de la restauration de ses donnees DIMA=RTO

# Les plans de secours, la tracabilite et l'audit 
Le controle de la securite necessite des outils permettant de prevoir un plan de secours, la tracabilite des evenements ainsi qu'un audit technique des procedures prevues par l'organisation en cas de breche de confidentialite, d'integrite ou de disponibilite. 
Le plan de continuite d'activite (PCA) et le plan de reprise d'activite (PRA) permettent aux organisations de poursuivre leur activite en cas d'incident ou de sinistre. 

- Plan de continuite: l'objectif est d'assurer la continuite des activites en cas d'incident. Un PCA peut, par exemple, prevoir des sauvegardes, qui permettent des restaurations en cas de pertes de donnees. 
- Plan de reprise d'activites: L'objectif est d'assurer la reprise des activites en cas de sinistre important (incendie, inondations, etc. ). Par exemple, une entreprise peut prevoir un site de secours. 

# PCA: plan de continuite d'activite 
- PDMA mesure le temps maximum acceptable durant laquel les donnees sont perdues, car elles ne peuvent pas etre reconstituees; il est nessaire de recourire aux dernieres donnees sauvegardees.
- DMIA mesure la duree d'interruption de fonctionnement du processus au-dela duquel les consequences deviennent intolerables. 
- DMRP (delais maximum de reprise technique prevu) mesure la duree d'interruption de fonctionnement des parties techniques du processus avant la repris een mode secours. Cela correspond a la duree de fonctionnement acceptable en mode degrade. 

Le PCA represente l'ensembe des mesures visant a assurer, selon divers scenarios de crises, y compris face a des chocs extremes, le maintien, le cas eceant de facon temporaire selon un mode degrade, des prestations de services ou d'autres taches operationnelles essentielles ou importantes de l'entreprise, puis la reprise planifiee des activites 

# PRA: Plan de Reprise d'activite 
Afin de pouvoir reellement se premunir d'un incident, une entreprise ne doit pas eulement sauvegarder ses donnees, elle doit egalement prevoir comment ses donnees sauvegardees vont etre utilisees. Il est ainsi necessaires de preparer un Plan de Teprise d'Activite (PRA) en anglais DR (Disaster Recovery Plan). 
40% des entreprises ayant subi un arret de 72 heures de leurs moyens informatiques et telecoms ne survvent pas a un desastre informatique. 

Qu'est-ce que le PRA ? 
un PRA permet d'assuerer dans le cas de défaillance: 
- la reconstitution de son infrastructure informatique
- la remise en route des applications necessaires a l'activite de l'entreprise 

A quoi set le PRA ?
en cas d'incident ou de sinistre, le PRA: 
- garantit l'activite par un plan de sauvegarde, de remise en route de services
- permet de reduire les consequences financieres
- pour conforter son image aupres des partenaires et clients 

# l'audit 
l'audit technique vise a evaluer les procedures prevues par une organisation en cas de breche de securite. Cet audit s'appuie sur l'elaboaration de FRAP (feuilles de revelation et d'analyse des problemes). Ces documents sont completes lorsque des dysfonctionnements ou des risques sont detectes: constat du probleme, causes, consequences, recommandations. 

FRAP:
- Probleme 
- Faits-Constats
- Causes
- Consequences 
- Recommandations
