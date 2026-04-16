# Qu'est-ce que le système RAID
en informatique, le mot RAID désigne les techniques permettant de constituer une unité à partir de plusieurs disques durs afin:
- d'améliorer la tolérance aux pannes, la disponibilité;
- d'améliorer les perfomances;
- d'augmenter la capacité des partitions logiques.
RAID est l'acronyme de Redundant Array of Independent (or inexpensive) Disks, ce qui signifie "chîne redondante de disques indépendants"

# Les différents niveaux de RAID
Les différents types d'architecture RAID sont numérotés à partir de 0 et peuvent se combiner entre eux (on parlera alors de RAID 0+1, 1+0, etc.). Les plus utilisés sont les RAID0, 1 et 5.
# Attention 
la technologie RAID n'est, en aucun cas, une technologie de sauvegarde (différentielle, incrémentielle) ni de stockage (nas, das, san, cloud...), ni d'archivage (tris et durée dans le temps des données). 

# Le RAID 0: volume agrégé par bandes
Le RAID 0, également connu sous le nom d'« entrelacement de disques » ou de « volume agrégé par bandes » (striping en anglais), est une configuration RAID permettant d'augmenter significativement les performances de la grappe en faisant travailler n disques durs en parallèle (avec n ≥ 2).
- Avantages: cumuler la capacité de plusieurs disques physiques sur un même lecteur logique, augmenter les perfomances en lecture/écriture. 
- Inconvénient: n'apporte rien au niveau de la sécurité. Au contraire: si un des disques crash, on perd toutes les données.
Les entreprises utilisent RAID 0 principalement pour les tâches nécessitant un accès rapide à une grande capacité de stockage temporaire sur disques.

# Le RAID 1: le miroir
Le RAID 1 consiste en l'utilisation de n disques redondants (avec n ≥ 2), chaque disque de la grappe contenant à tout moment exactement les mêmes données, d'où l'utilisation du mot « miroir » (mirroring en anglais).
- Avantages: sécurité (si un des disques crash, on conserve toutes le données), perfomances en lecture (mais pas en écriture). 
- Inconvénients gaspillage de 50% de l'espace disque. 
RAID 1 offre une garantie de protection des
données pour les environnements où la redondance absolue des données, la disponibilité et les performances jouent un rôle essentiel, et où le coût par gigaoctet de capacité utilisable est un élément secondaire.

# Les RAID 3 et 4: entrelacement avec parité 
Les RAID 3 et 4 combine la méthode du volume agrégé par bandes (striping) à une parité stockée sur un disque. Le RAID3 et le RAID4 sont sensiblement semblables sauf que le premier travaille par octets et le second par blocs.
- Avantages: sécurité, résiste à la panne d'un disque, augmentation des perfomances en lecture et en écriture 
- Inconvénients: le disque qui stocke la parité est beaucoup plus sollicité que les autres, et a donc une durée de vie plus courte. 
Les RAID 3 et 4 sont remplacés par les RAID 5 et 6. 

# Le RAID 5: entrelacement avec parité répartie 
Le RAID 5 combine la méthode du volume agrégé par bandes (striping) à une parité répartie. Les données sont entrelacées sur tous les disques de la pile, mais pour chaque bande de la pile, une unité de bande est réservée pour l’enregistrement de données de parité calculées à partir des autres unités.
- Avantages: sécurité (si un des disques crash, on conserve toutes les données), perfomances en lecture. 
- Inconvénients: les écritures sont pénalisées (temps de calcul des parités). 
RAID 5 rest devenu la référence pour les environnements de serveurs nécessitant une capacité de tolérance aux pannes. 
La capacité totale se calcule selon la formule (nombre de disques - 1) x (capacité du disque le plus petit).

# Le RAID 6: entrelacement avec double parité 
Le RAID 6 fonctionne de manière similaire au RAID 5, à la différence qu'il est capable de préserver l'intégrité des données après la panne de 2 disques durs. Pour ce faire, il génère deux jeux d'informations de parité et les stocke sur deux disques différents. Étant donné qu'il faut créer plus d'informations de parité lors des opérations d'écriture, les grappes RAID 6 sont généralement plus lentes que les RAID 5, mais la probabilité de perte de données est nettement plus faible.
- Avantages: sécurité (si deux des disques crashent, on conseve toutes les données), perfomances en lecture 
- Inconvénients: les écritures sont pénalisées (temps de calcul des parités), nombre de disques. 

# Le RAID 1+0 ou RAID 10
Cette technologie combine celle des RAID 0 et RAID 1 : elle consiste à assembler deux ou plusieurs unités RAID 1 en un ensemble RAID 0. En clair, deux disques durs sont assemblés en RAID 1, deux autres disques durs sont assemblés de manière identique et ainsi de suite. Il faut donc un minimum de quatre disques et toujours en nombre pair.La redondance des données dans chaque sous-unité permet de garantir leur sécurité, tandis que la répartition des données sur plusieurs unités logiques accélère la lecture et l’écriture.

# Choix du RAID 
- la sécurité: RAID 1 ou RAID 1+0 et 5 offrent tous les deux un niveau de sécurité élevé;
- les perfomances: RAID 1 offre de meilleures perfomances que RAID 5 en lecture, mais souffre lors d'importantes opérations d'écriture.
- le coût: le coût est directement lié à la capacité de stockage de la grappe.

# La mise en place du RAID 
Les implémentations des solutions de RAID peuvent être matérielles ou logicielles. Une implémentation matérielle embarque sur une carte électronique (contrôleur RAID), un processeur et le code contenant les algorithmes de gestion de la configuration RAID. Dans une implémentation logicielle, ces algorithmes sont embarqués dans le code du système d'exploitation et confie l'exécution des algorithmes au processeur.
- RAID matériel: fonctionnalités implémentées onboard, pas de surchage CPU. L'OS voit la grappe comme un simple disque. 
- RAID logiciel: les solutions logicielles sont souvent moins coûteuses et il y a peu de limites de configuration. Le CPU est sollicité. 

# Vocabulaire 
- Grappe: unité de stockage créée à partir de plusieurs disques 
- Striping: tolérance des pannes des contrôleurs, car chaque disques est branché sur un contrôleur différent 
- MTBF: Middle Time Between Failures (temps moyen de fonctionnement avant panne), environ 500k heures
- Mode dégradé: lorsqu'un disque dur crash, le système continue à fonctionner dans un mode "dégradé", ce qui traduit le fait que la sécurité n'est plus assurée tant que le disque dur fautif n'est pas remplacé. 
- Hot swap ou hot plug: propriété de certains disques à pouvoir être remplacés "à chaud", sans éteindre le système. 

# Conclusion 
# Ce que peut faire le RAID 
- Réduire les risques de pertes de données en cas de défaillances d'une unité de stockage 
- réduire les pertes de production lors de la défaillance d'un disque 
- améliorer les perfomances 
# Ce que ne peut pas faire le RAID 
- protéger totalement des défaillances matérielles (éventualités de pannes successives de plusieurs disques ou du système RAID lui-même)
- protéger les données des erreurs humaines (suppression accidentelles de fichiers)
- protéger l'utilisateur des risques extérieurs au système (surchage électrique qui grillerait l'ensemble des disques, incendie, vol, inondations, vandalisme)
- protéger les données des virus qui pourraient corrompre les données 

# Et RAID Z... Z pour l'ultime technologie...
RAID Z est réservé aux grandes unités de stockage composés de plusieurs disques donc plutôt aux entreprises. Raidz est aussi une technologie de RAID mais est associé uniquement au système de fichiers ZFS ( comme le sont NTFS ReFS, EXT4...).ZFS est compatible avec les autres types de raid.
Les NAS, Proxmox utilise ce système de fichiers par exemple. Il est disponible entre autre sur les OS : FreeBSD, macOS, Linux.
ZFS est un système de fichiers, entièrement en mode Écriture Différée (Copy-on-Write, CoW). Dans une configuration RAID-Z, ZFS se sert de la copie sur écriture pour ajouter les nouvelles données aux côtés des anciennes, sans réécrire sur ces dernières.

# Et RAID Z...
ZFS vérifie tous les données et métadonnées avec des sommes de contrôle. Lorsque ZFS détecte une erreur, il la corrige immédiatement si possible.
Cela peut être réalisé en utilisant des RAIDZ (stripping et/ou miroirs de largeur arbitraire 3 disks mini) ou RAIDZ1, RAIDZ2 et RAIDZ3. En termes de terminologie RAID traditionnelle, les miroirs seraient du RAID1, le RAIDZ1 est approximativement équivalent au RAID5, le RAIDZ2 au RAID6. Le RAIDZ3 étend ce concept au-delà de ce que le RAID matériel offre avec un disque supplémentaire. Les pools ZFS peuvent être de taille arbitraire en utilisant le striping à travers ces groupes de disques internes redondants. C’est une technologie puissante mais complexe dans la reconstitution des disques.