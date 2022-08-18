# apt und dpkg 

## Alle Pakete anzeigen, die installiert sind auf dem System 

```
dpkg -l 
# oder 
apt list --installed
```

## Alle Paket die zur Verfügung stehen 

```
apt list 
```

## Wo sind die Repos konfiguriert 

```
cat /etc/apt/sources.list 
cd /etc/apt/sources.list.d 
```


## Paket deinstallieren und aufräumen 

```
# mit Konfigurationsdateien deinstallieren
apt purge mariadb-server 
# Konfgurationsdateien stehen lassen
apt remove mariadb-server 

# Aufräumen / alle Pakete die nicht mehr benötigt werden
apt autoremove 
```

## Pakete händisch mit dpkg installieren 

```
# Schritt 1: Im Browser
# Paket online finden und Link kopieren (Browser - Rechte Mauataste Link kopieren) 

# Schritt 2: auf dem Linux Server
sudo apt install wget
cd /usr/src
wget http://archive.ubuntu.com/ubuntu/pool/main/a/acl/acl_2.2.53-10build1_amd64.deb
sudo dpkg -i acl_2.2.53-10build1_amd64.deb
```

## Pakete mit apt search suchen 

```
# Vorbereitung
apt update

# suche nache apache 
apt search apache 
# mit pager
apt search apache | less 

# Alle Paket in denen apache am Anfang der Zeile fehlt 
apt search ^apache | less

```

## Installieren mit apt install 

```
# mit genauem Namen 
apt install apache2 
```

## Liste der Files aus dem Paket (wenn installiert)

```
dpkg -L openssh-server 

```

## Paket runterladen, wenn bereits installiert 

```
apt install -d --reinstall openssh-server # -d steht für download-only
# Lädt das Paket unter 
# /var/cache/apt/archives runter 

```

## Welche Dateien sind im Paket, die ausgerollt werden ? (ohne Installation) 

```
cd /var/cache/apt/archives 
dpkg --contents openssh-server-xyz.deb # im gleichen Verzeichnis oder vollen Pfad dorthin
# oder Paket haben händisch in ein anderes Verzeichnis runtergeladen (z.B. mit wget)
dpkg -c /usr/src/openssh-server-xyz.deb


```

# dpkg / apt 

## Show all files/directories being installed by package 

  * Important: without files being created by install-script 
  
```
dpkg -L openssh-server 
```

## dpkg -l - show all packages 

```
dpkg -l 
```

## update repo & update system 
```
apt update 
apt upgrade 
apt dist-upgrade
```

## autoremove ## 
```
apt autoremove 
```

## reinstall config - files 

```
apt-cache pkgnames pulse |xargs -n 1 apt-get -o Dpkg::Options::="--force-confmiss" install --reinstall
```

## deinstallation 

```
apt remove package  # leave config-files 
apt purge package # also delete config files
```


