---
author: admin
comments: false
date: 2013-07-11 07:18:00+00:00
layout: post
link: https://witr.net/quotation/?p=43
slug: copier-plusieurs-fichiers-avec-des-noms-contenant-des-caracteres-accentues-cause-un-probleme-dencodage-du-nom-sur-le-host-destination
title: copier plusieurs fichiers avec des noms contenant des caractères accentués
  cause un problème d'encodage du nom sur le host destination
wordpress_id: 43
categories:
- linux
---


Aujourd'hui, nous avons transférer des fichiers pdf depuis un poste windows vers un host linux avec l'outil SSH Secure.  
les fichiers avec des noms contenants des caractères accentués ont des points d'intérrogation à la place des caractères acentués. Ceci nous pose problème au niveau du programme qui va les parser avec leurs noms originaux (avec caractères accentués)  
  
Un tar et puis une extraction du tar ne résout pas le problème.  
  
Solution 1 :  
créer un partage samba avec une machine du réseau et faire un transfert scp  
  
Solution 2  bête :  
créer deux scripts d'encodage et de décodage des noms des fichiers.  
a. appliquer le script d'encodage sur le host source avant le transfert  
b. transférer  
c. appliquer le script de décodage sur le host destination  
  
_fichier_encodage.sh:_  
mv "Nöel Milad" 1.pdf  
mv "Knüer Dina.pdf" 2.pdf  
... etc  
  
  
_fichier_decodage.sh:_  
mv 1.pdf "Nöel Milad"  
mv 2.pdf "Knüer Dina.pdf"  
... etc  
  
si la liste est treès longue servez vous de Excel:  
colonne A : mv  
colonne B : vide  
colonne C : copier/coller la liste des nom de fichiers (résultat de la commande dir)  
colonne D : vide  
colonne E : énumération (taper 1 et + outil de remplissage incrémental automatique d'Excel)

