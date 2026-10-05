Issue: https://github.com/Michi-esc/api-jeux-Michael-Lydia/issues/4

Ajout de deux fonctionnalités:
    1-une focntionalité de recherche des jeux du catalogue par filtre d'année de sortie, soit apres une année specifié, soit avant, ou entre deux plages d'années
    2-une deuxième fonctionnalité de recherche des éditeurs par leurs pays.

dans ce cadre sur j'ai definie deux fonctionnes
    1-une sur le fichier service/jeux.py et une sur le fichier service/editeurs.py
        celle de jeux.py def filtre_annees sur la ligne 60 qui prends deux input d'années limites en int qui peuvent etre NONE et appel la fonction filtre_annees dans le fichier depot/jeux.py sur la ligne 89 qui vérifie si les années limites du filtre n'est pas NONE, si la description 'annee' de la classe jeux peut correspondre à la requette, et la mets dans l'ordre de sortie dans une liste.
        celle editeurs.py def filtrer_par_pays sur la ligne 30 qui prends un str quelconque, verifie si il y a bien eut un input, si le str a bien été un text et non pas un nombre et si le str n'est pas trop longue; sinon il sort un message d'erreur. puis appel la fonction par_pays dans depots/editeurs.py sur la ligne 35 qui verifie si le texte entrer en miniscule correspond avec celui de la class Editeur : pays, puis les arrange en ordre alphabetique dans une liste.

ces deux fonctions sont appeler par deux commandes get dans les fichier routeurs/jeux.py et Editeurs.py
    celle de jeux.py sur la ligne 71
    celle de Editeurs.py sur la ligne 35 qui verifie si la liste renvoyer est vide et sort une erreur 404 si il y a eut aucun editeur trouvé.

Pour vérifier les test suivant été realisé
    pour le filtre d'année de sortie:
        si la saisie peut etre NONE
        si la saisie peut être un str ou float
        si les date min >= date max
    pour le filtre de pays
        si le str pleuvait être saisie en lower ou upper
        si la saisie pouvait être un int ou float
        si la saisie pouvait dépasser 100 char
        
