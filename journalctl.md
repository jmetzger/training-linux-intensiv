# Journalctl 

## journalctl 

```
# ubuntu
journalctl -u ssh.service 
# centos
journalctl -u sshd.service

# sehr schön um alle felder zu sehen 
journalctl -o json-pretty 

# alles was pid xy
journalctl _PID=5 

# alles seit gestern 
journalctl --since yesterday 

```

## Help-pages 

```
man journalctl
man systemd.journal-fields
```


## Show all boots 

``` 
 journalctl --list-boots
 0 3c3cf780186642ae9741b3d3811e95da Tue 2020-11-24 14:29:44 CET▒<80><94>T>
lines 1-1/1 (END)
```

## Journal persistent 

  * Update: Ubuntu 22.04 ist per default persistent !!!
  * Normalerweise (auf den meisten Systemen), überlebt das Journal kein Reboot 
 
```
# persistent setzen
# Achtung: in /etc/systemd/journald.conf muss Storage=auto gesetzt sein
# Dies ist auch der Default - Fall 
# Achtung Achtung: Alle gezeigten Einträge mit # am Anfang sind die Default-Werte (in journald.conf) 
mkdir /var/log/journal 
systemctl restart systemd-journal-flush.service 

```

## Restrict how much is logged / data 

```
# in /etc/systemd/journald.conf 
SystemMaxUse=1G 
```
