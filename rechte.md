# Rechte 

## Arten 

```
r = Lesen 
w = Schreiben
x = Ausführen 
```

## Aufbau triple 

```
kurs@ubuntu2004-101:~$ # rwx | rw- | r--
kurs@ubuntu2004-101:~$ #  u    g      o
kurs@ubuntu2004-101:~$ # 421 | 42- | 4--
kurs@ubuntu2004-101:~$ #  7  |  6  | 4

# rwx | rw- | r--
#  u    g      o
# 421 | 42- | 4--
#  7  |  6  | 4
```

## Bedeutung Oktalzahlen 

```
# rwx 
# r = 4, w = 2, x = 1
```

## Beispiele 

```
- w -  
0 2 0  = 020 
```


## Berechtigungen mit Symbolen setzen 

```
chmod g+w,o+r testfile
```
