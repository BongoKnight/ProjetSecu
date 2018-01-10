# Contrôle d'accès au Loria
## Contextualisation
Le LORIA contient des zones avec des niveaux de confidentialité différents. Tous les employés sont admis dans les zones de confidentialité basse. Et seules quelques personnes sont admises dans les zones classifiées "Secret". Il est utile qu'une personne puisse tout de même effectuer une demande d'accès exceptionnelle et que cette demande soit gérée dans les plus brefs délais.

## Architecture
Le réseau est organisé comme suit :
 
 - Des badgeuses à l'entrée de chaque pièce, qui permettent d’octroyer l'accès à la pièce.
 - Un serveur central qui vérifie que les permissions des employés utilisant la badgeuse sont conformes à ce qui est attendu.
 
## Rôle du serveur
Le serveur vérifie que les autorisations sont les bonnes et renvoit un message à la badgeuse indicatif de l'action à effectuer.

# Première version : naïve
## Connaissances initiales
 
 Le serveur connaît les identifiants des employés et des badgeuses et garde en mémoire leur niveau de confidentialité, il connaît de plus sa clef privé et sa clef publique, ainsi que les clefs publiques des badgeuses
 La badgeuse connait l'identifiant de l'employé qui vient de badger. Mais aussi son propre identifiant, ses clefs publiques et privées, l'adresse du serveur et sa clef publique.
 
## Protocole

 
> Badgeuse -> Serveur : {IdBageuse, IdEmploye}_PKs <br>
> Serveur -> Badgeuse : { Msg }_PKb <br>
> Badgeuse -> Serveur: { Msg }_PKs 
 
## Limitation
Ce protocole est sensible au rejeu. On peut rejouer le premier message de demande d'accès au serveur, mais aussi envoyé directement le message { Msg }_PKb à la badgeuse.

# Deuxième version : Nonces
 
## Connaissances initiales
 
Les connaissances initiales sont les mêmes, des nonces sont ajoutés afin d'éviter que le deuxième message soit rejoué. Des secrets sur les nonces sont prévus pour permettre une authentification entre serveur et intrus.

## Protocole

> Badgeuse -> Serveur : {IdBageuse, IdEmploye, Nb}_PKs <br>
>Serveur -> Badgeuse : { Msg , Nb.Ns}_PKb <br>
>Badgeuse -> Serveur: { Msg , Ns }_PKs




 

