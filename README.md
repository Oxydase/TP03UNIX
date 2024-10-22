# TP 03 Milton FIGUEIREDO

## Shell bash

## Exercice : paramètres

* Dans le 1er echo j'affiche le nombre de paramètre

* Dans le 2ème echo j'affiche le nom du script

* Dans le 3ème echo j'affiche la liste de paramètres
```
#!/usr/bin/bash

echo "Bonjour vous avez rentré $# paramètres"
echo "Le nom du script est $0"
echo "Le 3ème paramètre est $3"
echo "Voici la liste des paramètres: $@"

exit
``` 

## Exercice : vérification du nombre de paramètres

* Dans la 1ère ligne je verifie que le nombre d'argument est différent de 2 avec -ne (not equal) si on est dans ce cas je réalise ensuite un echo et arrête le script.

* Dans le cas ou la condition if n'est pas réalisé ca veut dire qu'il y'a 2 arguments donc je vais venir concatenner le 1er et 2eme paramètre dans une chaine de caractère pour les afficher ensuite

```
#!/usr/bin/bash
if [ "$#" -ne 2 ]; then 
    echo "Vous avez rentré plus ou moins de 2 paramètres"
    exit 
fi
RESULT="$1$2";
echo "$RESULT"
```

## Exercice : arguments types et droits

* Dans les 2 premières conditions je vérifie avec -d que le paramètre soit un répertoire et avec -s qu'il y'ait du contenu dans ce répertoire (! -s verifie qu'il n'y ait pas de repertoire)

* Dans les 2 dernières conditions je vérifie avec -f que le paramètre soit un fichier et avec -s qu'il y'ait du contenu dans ce fichier (! -s verifie qu'il n'y ait pas de repertoire)
```
#!/usr/bin/bash

if [[ -d $1 && -s $1 ]] ;then
    echo "c'est un répertoire avec du contenu"

elif [[ -d $1 && ! -s $1 ]] ;then
    echo "c'est un répertoire vide"

elif [[ -f $1 && -s $1 ]] ;then
    echo "c'est un fichier ordinaire avec du contenu"

elif [[ -f $1 && ! -s $1 ]] ;then
    echo "c'est un fichier vide"

fi
```

## Exercice : afficher le contenu d'un répertoire

* Je vérifie que le parametre soit un répertoire et ensuite j'affiche la liste de contenu de ce répertoire avec la commande `echo "$(ls $1)"`

```
#!/usr/bin/bash

if [ -d $1 ] ;then
echo "######### fichier dans $1"
echo "$(ls $1)";
fi
```

## Exercice : lister les utilisateurs

```
#!/usr/bin/bash

for user in $(cat /etc/passwd | cut -d: -f1,4); do echo $user;
```

Je n'ai pas réussi a coder les scripts "mon utilisateur existe t il" et "creation utilisateur"

## Exercice : lecture au clavier


* Quitter `more` : appuyer sur `q`
* Avancer d'une ligne : appuyer sur `entrée`
* Avancer d'une page : appuyer sur `espace`
* Remonter d'une page : appuyer sur `b`
* Rechercher : `/xyz`