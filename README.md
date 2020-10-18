# TP_02

Téléchargemetnt du fichier 
```shell
  wget http://julien.sopena.fr/LU2IN020-TP_01-EXO_03.tgz
```

## Exercice 1
### Question 1
```shell
  cd  LU2IN020-TP_02
```
### Question 2
```shell
  cd exo1
```




## Exercice 3:  Une Histoire de famille
### Question 1
Implémentez un script fils.sh qui affiche son PID, accessible depuis la variable $$, et le PID de son père, accessible depuis la variable $PPID
```shell
  echo   "je suis " echo $$    "et mon père est " $PPID
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
  echo   "je suis " echo $$    "et mon père est " $PPID
```
```shell
$ chmod u+x fils.sh

$ ./fils.sh
je suis  echo 1823 et mon père est  1599
```


```shell
#!/bin/bash
echo "le processus courant est : "   echo $$;

  for p in {1..10}; do
  # affichage du process courant
    ./fils.sh;
   done;

```


```shell
$ chmod u+x pere.sh

$ ./pere.sh
le processus courant est :  echo 1900
je suis  echo 1901 et mon père est  1900
je suis  echo 1902 et mon père est  1900
je suis  echo 1903 et mon père est  1900
je suis  echo 1904 et mon père est  1900
je suis  echo 1905 et mon père est  1900
je suis  echo 1906 et mon père est  1900
je suis  echo 1907 et mon père est  1900
je suis  echo 1908 et mon père est  1900
je suis  echo 1909 et mon père est  1900
je suis  echo 1910 et mon père est  1900

```

### Question 4
```shell
#!/bin/bash
# la process courant est renvoyé par  echo $$
# alors que le process parent est renvoyé par $PPID
  echo   "je suis " echo $$    "et mon père est " $PPID
```

```shell
#!/bin/bash
# affichage du process en cours
echo "le processus courant est : "   echo $$;
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
echo "le processus courant est : "   echo $$;
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
echo "Je suis   : "   echo $$;
i=1;
# la boucle  exécuter dix fois le fichier fils.sh
  while [ $i -le "$1" ]; do
  # affichage du process courant
    echo " Fils $i " ;  ./fils.sh;
((i++)) ;
   done;
fi

```
