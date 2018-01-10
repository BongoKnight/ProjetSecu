# Contrôle d'accès au Loria
## Contextualisation
Le LORIA contient des zones avec des niveaux de confidentialité différents. Tous les employés sont admis dans les zones de confidentialité basse. Et seules quelques personnes sont admises dans les zones classifiées "Secret". Il est utile qu'une personne puisse tout de même effectuer une demande d'accès exceptionelle et que cette demande soit gérée dans les plus brefs délais.

## Architecture
Le réseau est organisé comme suit :
 
 - Des badgeuses à l'entrée de chaque pièce, qui permettent d'octoryer l'accès à la pièce.
 - Un serveur central qui vérifie que les permissions des employés utilisant la badgeuse sont conformes à ce qui est attendu.
 

# Première version : naïve
## Connaissances initiales
 
 Le serveur connaît les identifiants des employés et des badgeuses et garde en mémoire leur niveau de confidentialité, il connait de plus sa clef privé et sa clef publique, ainsi que les clefs publiques des badgeuses
 La badgeuse connait l'identifiant de l'employé qui vient de badger. Mais aussi son propre identifiant, ses clefs publiques et privées, l'adresse du serveur et sa clef publique.
 
## Protocole

 >
 Badgeuse -> Serveur : {IdBageuse, IdEmploye}_PKs
 Serveur -> Badgeuse : { Ok }_PKb
 Badgeuse -> Serveur: { Ok }_PKs
 
## Limitation
Ce protocole est sensible au rejeu. On peut rejouer le premier message de demande d'accès au serveur, mais aussi envoyé directement le message { Ok }_PK~b~ à la badgeuse.

## Deuxième version : clef de session
 
## Connaissances initiales
 
Les connaissances initiales sont les mêmes, des nonces sont ajoutés afin d'éviter que le deuxième message soit rejoué.

## Protocole

 >
 Badgeuse -> Serveur : {IdBageuse, IdEmploye, Na}_PKs
 Serveur -> Badgeuse : { Ok , Na.Nb}_PKb
 Badgeuse -> Serveur: { Ok , Nb }_PKs

 -----
# Remarques :
 - Sécuriser l'échange via une clef de session pour éviter le rejeu.
 - Prévoir plusieurs serveurs
 - Gérer les accès exceptionnels.
 


