## Network Address Translation (NAT) & Port Address Translation (PAT)
# Adresses privées/adresses publiques 
# Rôle du NAT et du PAT
# NAT statique/NAT dynamique/PAT
# Avantages et inconvénients 
# Commandes Cisco

# Adresses privées/adresses publiques 
Une entreprise s'est vue attribuer un pool d'adresse IP publique. Problème: leur quantité est limitée. Il faut donc traduire les adresses privées en adresse publique et vice-versa
Vocabulaire: 
- Inside address: adresse privée, située à l'intérieur du routeur 
- Outside address: adresse publique située à l'extérieur du routeur 

Inside address: adresses privées, en grand nombre 
Outside address: adresses publiques, donc en quantités limitée
Internet ne route pas les adresses privées  

# Terminologie NAT 
La fonction NAT comprend 4 types d'adresses: 
- Adresse interne: l'adresse du périphérique traduite via le NAT
- Adresse extene: l'adresse du périphérique de destination 
- Adresse locale: une adresse locale peut faire référence à toute adresse qui apparaît sur la partie interne du réseau 
- Adresse globale: une adresse globale peut faire référence à toute adresse qui apparaît sur la partie externe du réseau 

# NAT statique/NAT dynamique/PAT 
Il existe 3 types de traduction NAT: 
- NAT statique: 1 adresse interne<=>1 adresse extene. Mappage "un à un" entre les adresses internes et externes 
- NAT dynamique: n adresses internes<=>m adresses externes. Mappages de plusieurs adresses internes et externes 
- PAT: n adresses internes<=>1 adresse externe. Mappage de plusieurs adresses internes et externes vers une seule 

# Avantages du NAT et du PAT 
- Economie des adresses publiques 
- Augmente la souplesse des connexions au réseau public 
- Permet un adressage du réseau local indépendant du FAI
- Sécurité: adresses internes non divulguées à l'extérieur

# Inconvénients du NAT et du PAT 
- Dégradation des perfomances: le routeur doit examiner chaque paquet 
- Perte de l'adressage de bout en bout=>ex: problème en FTP
- Perte de traçabilité=>Dépannage plus difficile 

# Commandes Cisco 
Indiquer au routeur où se situe le réseau privé et le réseau public: 
R1(config)#int fa0/0 
R1(config-if)#ip nat inside 
R1(config-if)#exit 
R1(config)#int fa0/1 
R1(config-if)#ip nat inside
R1(config-if)#exit 
R1(config)#int s0/0 
R1(config-if)#ip nat outside 
R1(config-if)#exit

Exempke de configuration du NAT statique pour C3=>translation statique dans la table de translation NAT= "ouvrir un port". Il s'agit au routeur que ce qui arrive sur son interface publique(S0/0) et dont l'adresse destination est 201.49.10.30 (une des adresses du pool publique) doit être redirigé vers 192.168.1.100.

- Configurer du NAT statique:
 R1(config)#ip nat inside source static 192.168.1.100 201.49.10.30

- Visualiser la table de translations NAT: 
 R1#show ip nat translations 
 Pro Inside global Inside local Outside local Outside global
 --- 201.49.10.30  192.168.1.100 ---   

Exemple de configuration du NAT dynamique pour C2=>donner au routeur une plage d'adresses publiques (un pool d'adresse) dans laquelle il peut piocher pour créer dynamiquement les translations. 

- Créer le pool d'adresses: 
 R1(config)#ip nat pool POOL-NAT-LAN2 201.49.10.17 201.49.10.30 netmask 255.255.255.240

Il nous faut ensuite définir quelles adresses IP sources seront susceptibles d'être translatées... pour cela il faut créer une ACL. 

- Créer une ACL (Acces Control List):
 R1(config)#access-list 1 deny 192.168.1.100 
 R1(config)#access-list 1 permit 192.168.1.0 0.0.0.255
- Configuration du NAT
 R1(config)#ip nat inside source list 1 pool POOL-NAT-LAN2         ou
 R1(config)#ip nat inside source list 1 pool POOL-NAT-LAN2 overload=>s'il y plus de machines dans le réseau privé que d'adresses publiques disponibles=>PAT

Exemple de configuration du NAT dynamique avec surcharge (PAT) pour C1=>configuration la plus courante dans un réseau modeste (par exemple dans un réseau domestique). 
- Créer une ACL:
 R1(config)#access-list 2 permit 192.168.0.0 0.0.0.255
- configuration du NAT:
 R1(config)#ip nat inside source list 2 interface serial 0/0 overload

Nous disons ici au routeur de translater les paquets provenant des adresses décrites dans l’ACL 2 (192.168.0.0/24) et de remplacer l’adresse IP source par celle configurée sur l’interface Serial 0/0 en la surchargeant pour permettre à plus d’une machine de communiquer avec l’extérieur (PAT).

