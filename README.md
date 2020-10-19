# TP_02


## Exercice 1

### Question 1
```shell
  wget http://julien.sopena.fr/LU2IN020-TP_01-EXO_03.tgz
  tar  -xvzf LU2IN020-TP_02.tgz
```
 
### Question 2
```shell
  cd exo1
  cat mon_test.c
  cat README
  gcc mon_test.c -o mon_test
```



### Question 3

```shell
  $	./mon_test 
```
   Usage : mon_test <un_entier>
```shell
  $	./mon_test 23
```
   Il n'est pas pair
```shell
  $	./mon_test 24
```
   Il est pair


### Question 4
```shell
   mv  mon_test  est_il_pair 
```
je constate que l'exécution du fichier sans paramètre fait référence au fichier  "mon_test"

### Question 5
```shell
  #include<stdlib.h>
#include<stdio.h>

int main(int argc, char const *argv[])
{
	int i, ret;

	if (argc < 2) {
		printf("Usage : %s <un_entier>\n" , argv[0] );
		exit(-1);
	}

	printf("Il %s pair\n", atoi(argv[1]) % 2 ? "n'est pas" : "est");

	return 0;
} 
```


##  Exercice 2 : Et PATH le chemin
### Question 1

```shell
  cp est_il_pair ../exo2
  cd ../exo2/
  ./est_il_pair 24
```
> Il est pair

### Question 2

```shell
  est_il_pair 24
```
> l'exécution  du fichier vas renvoyer un message d'erreur. Au fait le shell ne parvient pas à localise le fichier est_il_pair.

### Question 3

```shell
  $PATH_OLD=$PATH
  PATH = tp2/exo2:$PATH_OLD
```

### Question 4

```shell
PATH = .: $OLD_PATH
```
> On peut exécuter le fichier  "est_il_pair"  sans préciser le chemin du dit fichier. CAD  sans passer par  ./est_il_pair. 


### Question 5

```shell
   mkdir -p rep1/rep2
```

### Question 6
> il est dangereux de mettre '.' dans un PATH  parcequ'on risque de confondre les  commandes shell avec ceux des fichiers excécutables déjà crée. Pour éviter toute confusion , il faut toujours préciser le chemin du fichier à exécuter.

## Exercice 3:  Une Histoire de famille
### Question 1
Implémentez un script fils.sh qui affiche son PID, accessible depuis la variable $$, et le PID de son père, accessible depuis la variable $PPID
```shell
  echo   "je suis "   $$    "et mon père est " $PPID
```
### Question 2
```shell
echo "le processus courant est : "    $$;

  for p in {1..10}; do
    ./fils.sh;
   done;
```

### Question 3
```shell
#!/bin/bash
  echo   "je suis "   $$    "et mon père est " $PPID
```
```shell
$ chmod u+x fils.sh

$ ./fils.sh
je suis    1823 et mon père est  1599
```


```shell
#!/bin/bash
echo "le processus courant est : "     $$;

  for p in {1..10}; do
  # affichage du process courant
    ./fils.sh;
   done;

```


```shell
$ chmod u+x pere.sh

$ ./pere.sh
le processus courant est :    1900
je suis    1901 et mon père est  1900
je suis    1902 et mon père est  1900
je suis    1903 et mon père est  1900
je suis    1904 et mon père est  1900
je suis    1905 et mon père est  1900
je suis    1906 et mon père est  1900
je suis    1907 et mon père est  1900
je suis    1908 et mon père est  1900
je suis    1909 et mon père est  1900
je suis    1910 et mon père est  1900

```

### Question 4
```shell
#!/bin/bash
# la process courant est renvoyé par  echo $$
# alors que le process parent est renvoyé par $PPID
  echo   "je suis "   $$    "et mon père est " $PPID
```

```shell
#!/bin/bash
# affichage du process en cours
echo "le processus courant est : "     $$;
# la boucle  exécuter dix fois le fichier fils.sh
  for p in {1..10}; do
  # affichage du process courant
    ./fils.sh;
   done;
```

##  Exercice 4
### Question 1
```shell
 $ pwd
 /c/Users/User/Downloads/TP_02/exo1
 $ cp pere.sh ../exo4
```

_ pere.sh
```shell
#!/bin/bash
# tester l'éxistance d'1 paramaètre
if [ -z  $1 ] ; then
echo " il manque un paramètre"; exit 1;
else
# affichage  du process en cours
echo "le processus courant est : "     $$;
# la boucle  exécuter dix fois le fichier fils.sh
  for p in {1..10}; do
  # affichage du process courant
    ./fils.sh;
   done;
fi

```


### Question 2
```shell
 #!/bin/bash
# affichage  du process en cours
if [ -z  $1 ] ; then
echo " pas de paramètre fourni"; exit 1;
else
echo "Je suis   : "     $$;
i=1;
# la boucle  exécuter dix fois le fichier fils.sh
  while [ $i -le "$1" ]; do
  # affichage du process courant
    echo " Fils $i "   $(./fils.sh);
((i++)) ;
   done;
fi

```
