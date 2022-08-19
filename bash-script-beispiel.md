# Beispiel bash - script 

## /etc/auswertung.conf 

```
DATUM=$(date +"%Y-%m-%d")
LOG_BASE_DIR=/var/log/auswertung
LOGTO=$LOG_BASE_DIR"/"$DATUM".log"
```

## /usr/local/bin/caller.sh

```
#!/bin/bash

#echo "Scriptname" $0
#echo "Parameter 1" $1
#echo "PArameter 2" $2
#echo "Parameter @- alle parameter" $@
#echo "Parameter Anzahlt" $#

# . /etc/auswertung.conf
source /etc/auswertung.conf

##
# Preparation
###

if test ! -d $LOG_BASE_DIR
then
  echo "lege verzeichnis auswertung an"
  mkdir $LOG_BASE_DIR
else
  echo "basedir existiert bereits"
fi

##
# Log function
mlog(){
  echo "[$(date +'%Y-%m-%d') $(hostname)] $1" >> $LOGTO

}

mlog "Alles Auf Anfang ...."


let COUNT=0

cd /etc
for i in a*
do
  if test -f $i
  then
    mlog "Datei gefunden: $i"
    let COUNT=COUNT+1
  fi
done

echo "Wieviel files"$COUNT

# /var/log/auswertung
let WIEOFT=0

while test $WIEOFT -lt 5
do
   FRAGE="Wie heisst Du ?"

   if [ $WIEOFT -gt 0 ]
   then
     FRAGE="Der Name gefällt mir nicht. Wie heisst Du sonst noch ?"
   fi


   echo $FRAGE
   read NAME
   echo "o.k. Du heisst $NAME"
   let WIEOFT=WIEOFT+1
done

```

```
cd /usr/local/bin
chmod u+x caller.sh
# Aufruf 
caller.sh
```
