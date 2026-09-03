# Le test logiciel 
1) Introduction: pourquoi tester ?
2) La mission du testeur 
3) Les qualités du testeur 
4) Le testeur dans le cycle de vie de projet 
5) Niveaux et types de tests 
6) Synthèse et quiz interactif

# Pourquoi tester 
Le vol 501 est le vol inaugural du lanceur européen Ariane 5, qui a eu lieu le 4 juin 1996. Il s'est soldé par un échec, causé par un dysfonctionnement informatique, qui vit la fusée se briser et exploser en vol seulement 36,7 secondes après le décollage. Le système de guidage inertiel qui se trouvait dans la fusée Ariane 5 était le même que celui qui équipait les précédents modèles de la fusée Ariane. Toutefois, le plan de vol suivi par Ariane 5 lors de son lancement diffère beaucoup de celui d'Ariane 4 : sa trajectoire est différente et les accélérations infligées aux instruments par la fusée sont cinq fois plus fortes que celles que produisait son aînée. Les valeurs trop élevées mesurées par les accéléromètres ont provoqué un dépassement d'entier, lors du calcul de la position géographique de la fusée par le dispositif informatique du système de guidage, ce qui a causé son plantage. Après enquête, les ingénieurs du CNES se sont aperçus que par mesure d'économie, le logiciel de navigation de la fusée Ariane 5 était celui qui avait été conçu pour Ariane 4, ce qui a induit une incompatibilité entre le logiciel et le matériel.

Les tests ne servent à rien. Il suffit de vérifier le code et de déployer en production. 

# Pourquoi tester ? Un standard 
La certification ISTQB (International Software Testing Qualifications Board) est un standard mondial qui valide les compétences et les connaissances des professionnels du test logiciel et de la qualité.

# Pourquoi tester ? Les objectifs 
Tester, ce n’est pas seulement chercher des anomalies.
Les tests permettent de :
-Évaluer un produit (donner une information sur le niveau de qualité)
-Vérifier la conformité aux exigences et spécifications
-Prévenir les défauts
-Construire la confiance dans la qualité du logiciel
-Réduire les coûts (corriger tôt coûte moins cher)
-Assurer la satisfaction client

Le test désigne toutes les activités qui consistent à rechercher des informations sur la qualité du système afin de permettre la prise de décisions. Un plan de test est un document décrivant l’étendue, l’approche, les ressources, le contexte et le planning des activités de test prévues.

# Pourquoi tester ? 7 principes ISQTB 
Voici les sept principes généraux du test à avoir à l’esprit :
• Les tests montrent la présence de défauts, mais ils ne peuvent pas garantir l’absence de défauts.
• Les tests exhaustifs sont impossibles. On aura beau faire tous les tests qu’on imagine, il y en aura toujours auxquels on n’aura pas pensé.
• Tester au plus tôt.
• Le regroupement de défauts.(les anomalies se concentrent souvent dans les mêmes zones)
• Le paradoxe du pesticide répéter les mêmes tests les rend moins efficaces
• Les tests dépendent du contexte (une app bancaire
ne se teste pas comme une app météo).
• L’illusion d’absence d’erreur (absence apparente d’erreurs ne signifie pas absence réelle)
Bien tester, c'est aussi savoir quand arrêter 

# La mission du testeur 
La principale mission d’un testeur est de contrôler si un nouveau produit informatique (logiciel, équipement, système, etc.) est conforme au besoin.
Pour vérifier la conformité d’un produit, le testeur doit :
• prendre connaissance des spécifications du produit et des normes qui lui sont imposées ;
• créer différents outils de test (plan de tests, automatisation de test) afin de préciser et définir tous les
points à vérifier ;
• effectuer des tests jusqu’à ce que chaque point soit validé et conforme ;
• reporter avec précision les résultats une fois tous les tests effectués.
Tester, c’est trois actions essentielles
Vérifier : est-ce que ça marche ? (conformité à ce qui a été défini)
Valider : est-ce que ça convient à l’utilisateur ? (atteinte de l’objectif)
Explorer : est-ce que le système est robuste, performant ? (spécifications implicites)

# La mission du testeur 
Les missions d’un testeur peuvent être très variables en fonction de ses appétences et des projets sur lesquels il intervient.
Il peut :
• exécuter un plan de test déjà écrit, et en reporter les résultats (OK,KO) : un testeur “presse-bouton”,
• faire de l’automatisation, c’est-à-dire réaliser des scripts qui vont tester le produit sans intervention humaine ;
• aider à concevoir les nouvelles fonctionnalités, accompagner les développeurs pour une meilleure qualité du code, etc. ;
• réaliser des tests de performance, de charge, de stress ;
• gérer le pilotage des tests ;
• suivre les anomalies ;
• insuffler l’esprit de la qualité au sein de son équipe.

# L'équipe du testeur 
En méthode agile : Product Owner, Scrum Master, UX/UI Designers, développeurs, testeurs.
En méthode séquentielle : chef de projet (à la place du PO), mêmes autres intervenants.
S’il y a plusieurs testeurs : un Lead QA (responsable de qualification) répartit les tâches.
QA = Quality Assurance = assurer un niveau minimal de qualité au logiciel.
Scrum est un processus qui s'appuie sur 3 piliers: la treansparence, l'inspection et l'adaptation. 

Les 6 qualités du testeur :
- Curiosité : expérimenter, poser des questions, analyser les anomalies, apprendre en permanence
- Rigueur : examiner les exigences, réaliser des tests complets, documenter les défauts, vérifier les corrections
- Autonomie : prendre des initiatives, travailler sans supervision constante
- Proactivité : améliorer le processus de test, anticiper les problèmes
- Polyvalence : s’adapter à de nouveaux outils et technologies, être déployé sur divers projets
- Communication : s’adapter à son interlocuteur (technique ou non), poser les bonnes questions

# Le testeur dans le cycle de vie d'un projet: 3 modèles 
- Modèle en cascade (séquentiel)
Phases successives : besoins, analyse, conception, développement, validation, validation client, mise en service. Le testeur intervient uniquement lors de la phase de validation. Limite : une anomalie détectée en validation fait remonter le cycle (mise en oeuvre, voire conception), ce qui ralentit le
développement.
- Cycle en V (séquentiel, avec conception des tests en amont)
Flux descendant (détail du produit) : besoins, analyse, conception générale, conception détaillée, développement. Flux ascendant (validation) : tests unitaires, tests d’intégration, tests système, validation client, mise en service. Caractéristique clé : pour chaque phase de production, un test est conçu en amont. Les tests système sont conçus lors de la phase d’analyse. Cela évite les problèmes du modèle en cascade
- Méthode agile (incrémental et itératif) 
Fonctionnement par sprints (cycles courts et itératifs). Le testeur intervient à chaque étape de la boucle : Définition des exigences : critères d’acceptation, Conception : tests système, Développement : compréhension des API, tests d’intégration, Validation à chaque livraison Mise en service. Valeurs clés : collaboration, flexibilité, rapidité, qualité. Stand-ups quotidiens et rétrospectives

# Test
Consigne : Associez chaque situation au modèle le plus pertinent, et
justifiez.
1. Application bancaire avec exigences très réglementées figées dès le
départ
2. Site e-commerce en démarrage, besoin de livrer vite et de s’adapter
3. Projet avec cahier des charges précis et besoins stabilisés

Niveaux et types de test:
- Niveau: Tests unitaires/composants, Tests d'intégration, Tests système, Tests d'acceptation 
- Réalisé par: Développeurs, Développeurs ou testeurs, Testeurs, Testeurs et PO/client
- Objectif: Vérifier chaque "brique du code, Vérifier que les composants communiquent entre eux, Vérifier la conformité aux spécifications au niveau système, Vérifier la conformité au besoin utilisateur 

L’analogie du mur
Un client veut un mur de 2 m x 5 m :
Vérifier que chaque brique est correcte : tests unitaires
Vérifier que les briques s’emboîtent : tests d’intégration
Vérifier que le mur fait bien 2 m x 5 m : tests système
Le client contrôle le mur… mais il voulait un mur en pierre, pas en brique : tests d’acceptation
Leçon : comprendre le besoin final avant de développer ; des spécifications correctes évitent les mauvaises surprises.
Un produit peut être conforme aux spécifications mais ne pas répondre au besoin utilisateur. 

# 2 grandes catégories: 
- Tests fonctionnels : valider que les fonctionnalités du produit fonctionnent et répondent au besoin.
- Tests non fonctionnels : évaluer les aspects implicites du produit : - Robustesse (résister aux pannes) - Performance (temps de réponse) - Montée en charge (supporter un nombre d’utilisateurs) - Compatibilité (navigateurs, systèmes d’exploitation, appareils) - Ergonomie et utilisabilité - Sécurité Un type de test peut couvrir un ou plusieurs niveaux de test

Test: classez chaque test dans la bonne catégorie (fonctionnel ou non fonctionnel): 
1. Le formulaire de contact envoie un email au destinataire choisi
2. Le système offre une bonne performance et réactivité
3. Le système est compatible avec les différents navigateurs
4. Le système affiche un message d’erreur si le mot de passe est incorrect
5. Le temps de chargement d’une page ne dépasse pas 3 secondes
6. Le système gère correctement les entrées et sorties de données
7. Le système supporte 1 000 utilisateurs simultanés sans ralentissement
8. Le système respecte les règles métier et les scénarios d’utilisation