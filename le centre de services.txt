# LE CENTRE DE SERVICES ET SES MISSIONS
# Qu'est-ce qu'un centre de services ? Les missions du centre de service
# L'ITIL et GLPI
# Les incidents, problèmes et changements 
# Le SLA, OLA, UC
# Le processus de gestion des incidents 
# Hiérarchisation/Priorisation
# Les logiciels utilisés

# Qu'est-ce qu'un centre de services 
Le centre de services (Service Desk) porte toute la relation entre le SI et les utilisateurs du SI. Il coordonne toute l'activité support du SI. Il est le point de contact unique(Spoc: Single Point Of Contact) entre les utilisateurs et l'organisation informatique, pour l'ensemble des services proposés par la direction des systèmes d'informations.
L'utilisation des moyens numériques est devenue ATAWADAC: at any time, any where, any device, any content; "tout partout, tout le temps, quel que soit le support" (poste de travail, smartphone, etc.), le moindre dysfonctionnement entraîne des risques cruciaux: mécontement des clients, réputation négative, pertes de revenus, voire mise en péril de l'entreprise. 

# Pourquoi un guichet unique de sollicitation de la DSI ?
Le principe de base est que les utilisateurs arrêtent de contacter toutes les personnes de l'informatique, entraînant des pertubations dans les activités informatiques quotidiennes (études, projets, développement...).

# Les missions du centre de services (Service desk)
- Prendre en compte toutes les sollicitations des utilisateurs: accueillir, recevoir et enregistrer, suivre de bout en bout, tracer les demandes et les interventions sur le SI.
- Assurer le bon fonctionnement des sollicitations: résoudre les incidents, les dépanner, traiter ou faire suivre les demandes. 
- Prendre en charge la communication avec les utilisateurs: tenir informer l'utilisateur par une communication adptée, exemplaire, sereine et efficace, évaluer et communiquer et produire sur la Qos des métriques, améliorer l'image de la DSI. 
- Coordonner les équipes support: permettre l'affectation, la planification et le suivi du traitement des demnades d'assistance, d'intervention et de services, prévoir les déplacements, les besoins, relancer. 

- Le centre d'appels (call center): compétences techniques limitées et compétences métiers inexistantes. S'en tient à la prise d'appels, à l'enregistrement et à l'affectation des demandes aux personnes compétentes (délai de traitement long !). 
- Le centre de services (help desk): ne traite (gestion, coordination et résolution) que les incidents, avec un niveau technique peu approfondi, généralement peu communicant, peu proche des métiers. Traite inlassablement le même dysfonctionnement qui se reproduit sans cesse. 
- le centre de services (service desk): englobe donc plus de missions que le help desk ou le call center. En permettant la gestion des niveaux de service, il contractualise la fourniture des services avec l'utilisateur de l'organisation. 

Les évolutions majeures du SI obligent les entreprises à repenser leur support informatique, et à l'organiser en suivant les bonnes pratiques d'ITIL via un logiciel de gestion de tickets comme GLPI, pour traiter et se protéger contre les pannes, les pertes de données, etc.

# Qu'est-ce que ITIL ? 
ITIL signifie Information Technology Infrastructure Library. En français, on traduirait par bibliothèque pour l'infrastructure des technologies de l'inforamtion. C'est un ensemble de bonnes pratiques permettant d'assurer une bonne gestion du SI d'une entreprise. 

# Qu'est-ce que GLPI ? 
GLPI est un outil ITSM pour Information Technic Service Mangement. C'est un outil open source qui permet de mener de nombreuses actions de gestion de l'IT, comme la gestion de parc ou le suivi des tickets utilisateurs. GLPI permet d'orchestrer la gestion des incidents et de problèmes informatiques. 

# Qu'est-ce qu'un incident ? Problème ? Changement ? 
Un incident correspond à un comportement anormal d'un composant des SI: dysfonctionnement matériel, logiciel, réseau. 
Exemples:
- les défaillances de messageries 
- les pannes de matériel 
- les ruptures de connexion au réseau de l'entreprise 
- les soucis de bureautiques 
- les anomalies d'applications métier 

Un incident est détecté soit par un utilisateur qui va contacter le Centre de services, soit par des outils de supervision. 
 
 On distingue les incidents, des problèmes, des changements 
 
 - Incidents: un incident est isolé et ne nécessite pas la résolution d'un problème plus global. La gestion des incidents permet de restaurer le fonctionnement normal du service, souvent par un contournement, pas toujours par une résolution définitive. 
 Exemple: lenteur d'une application de saisie d'une commande client.e La MAJ de l'appli résout le pb=>incident 

 - Problème: lorsqu'un incident se répète, ou lorsque plusieurs incidents résultent de la même cause supposée, il s'agit d'un problème. La gestion des problèmes, elle, vise à traiter la cause de l'incident pour que celui-ci ne se reproduise plus.
 Exemple: le technicien diagnostiquent un problème de perfomance côté serveur. Il redémarre le serveur. L'application fonctionne normalement jusq'au lendemain où l'application est à nouveau lente=>problème 

 - Changement: la résolution d'un incident, d'un problème (ou encore un nouveau projet) peut entraîner un changement de configuration des systèmes d'informations. Un tel changement est rarement neutre. 

 Les conséquences d'un changement de configuration peuvent donc être critiques. Il convient donc de les gérer via GLPI, en suivant les bonnes pratiques d'ITIL: le processus de gestion des changements précise les opérations et le dispositif à mettre en place pour veiller aux risques de régression de l'existant, selon l'impact présumé du changement (majeur ou pas...), ou bien bien selon la maîtrise de ce changement (changement standard...).

 # SLA ? OLA ? UC ?
 selon ITIL, la valeur d'un service est fonction de: 
 - son utilité: le service est adapté aux besoins du client;
 - sa garantie selon 4 axes: assurer la disponibilité, la perfomance, la sécurité de l'information et la continuité de service. 

 La gestion des niveaux de service (SLM: Service Level Management) propose la création de trois types d'accord:
 - le SLA (Sevice Level Agreement) ou accord de niveaux de service: accord défini entre l'utilisateur (client du service) et la DSI sur le niveau de qualité de services offert;
 - le OLA (Operational Level Agreement) ou accord sur les niveaux oprationnels: accord passé entre les différents pôles de la DSI;
 - l'UC (Underpinning Contract) ou contrat de sous-traitance: contrat entre la DSI et un fournisseur externe. 
 L'ensemble présuppose l'existence d'un catalogue des srevices proposés par la DSI, qui a par ailleurs l'intérêt de clarifier l'offre de l'informatique. 

# le SLA (Service Level Agreement)
Les bonnes pratiques ITIL se traduisent par la contractualisation de la gestion des incidents en définissant et en gérant des niveaux de services. 
Le SLA ou accord de niveaux de service définit le niveau de qualité de service entre l'utilisateur (client du service) et le prestataire informatique (interne ou externe à l'organisation) sur le niveau de qualité de service offert. 
Cet engagement réciproque est formalisé dans un contrat de services. 
Un contrat de service est donc:
- un accord sur le service proposé;
- un accord sur les niveaux de services associés;
- un accord sur le coût de la solution; 
- un engagement de résultats sur des objectifs à atteindre pour un ou plusieurs services. 

Le SLA précise les droits et les devoirs de chaque partie, les responsabilités de chacun pour une période donnée. A l'échéance du contrat, celui-ci est renégocié. 
Les niveaux de service précisent :
- la description du service, la durée du contrat;
- les engagements sur les heures de fourniture ou de disponibilité du service, les délais de prise en charge des appels au Centre de service et les délais de résolution (délais de rétablissement du service);
- les coûts associés à la production du service;
- les indicateurs permettant de vérifier que les engagements sont tenus;
- les modalités de production des tableaux de bord (fréquence, communication);
- les pénalités pour non-respect des engagements de la part du fournisseur du service. Si le prestataire est un service informatique interne, il n'y a pas nécessairement de pénalités. 

Exemple:
- ouverture aux heures ouvrées de bureau;
- rétablissement du service en moins de 4 heures; etc...

# Le processus de gestion de tickets 
- Enregistrement: à chaque incident, il y a ouverture d'un ticket d'incident avec les informations administratives (date et heure, nom de la personne qui a détecté l'incident, lieu et site, numéro de contrat si nécessaire...)
- Classification: permet au centre de service de catégoriser l'incident. Pour cela une série d'étapes, de questions hiérachisées permettront de déterminer le type de l'incident ce qui déterminera les ressources à mobiliser pour le résoudre. 
- Codification: une priorité est attribuée avec les délais de rétablissement prévue par contrat. Ce n'est pas l'utilisateur mais le centre de services qui assume cette responsabilité. 
- Diagnostic initial: une recherche est effectuée pour déterminer si la situation décrite est déjà connue dans les bases de connaissances. 

# Hiérarchisation/Priorisation(impact et urgence):
Chaque incident doit être codifié pour déterminer la priorité que l'on va lui attribuer. Une notation est utilisée en général sur une échelle de 1 à 3 ou de 1 à 5 (Elevé:1 3 ou 5: Faible).

Il faut distinguer l'impact de l'urgence d'un incident:
L'impact est l'effet de l'incident sur l'utilisation du service comme la perte d'exploitation (serveurs indisponible), ou le nombre d'utilisateurs qui ne peuvent pas travailler, etc.
L'urgence est le temps nécessaire pour rétablir le service avant que les effets de l'incident ne se fassent sentir. Par exemple, la non disonibilité de l'application de gestion de la paie n'a pas la même importance si cela arrive en début de mois ou en fin de mois quand il faut établir les bulletins de paie.
La priorité de l'incident résulte de son impact et son urgence sur l'activité métier. Cette priorité permet d'identifier l'importance relative des incidents les uns par rapport aux autres 

A chaque niveau de priorité (P1,P2,P3) , on affecte un délai de rétablissement (exemple: P1=2h, P2=8h, P3=24h). Ces codifications d'un incident (impact, urgence, matrice d'attribution des niveaux de priorité et délais de rétablissement) doivent être explicitées dans le SLA avant la mise en exploitation du service. 

# Un logiciel utilisé 

GLPI: gestion de parc (matériel, logiciel, datacenter), helpdesk, base de connaissances, gestion financière, gestion de projet