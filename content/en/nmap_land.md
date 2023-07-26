---
title: "Nmap for pentesting"
author: "c4r4nch0"
date: "2022-05-07"
draft: false
searchHidden: false
tags: ["nmap", "machete"]
ShowToc: false
ShowBreadCrumbs: false
# cover:
#     image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSQud1wlz3Fl6brRiyQMKkg8XMhI2BE9J7SazqbG4DBOcbkVorYi34k1Y6axGErJj0L9LU&usqp=CAU"
#     # can also paste direct link from external site
#     # ex. https://i.ibb.co/K0HVPBd/paper-mod-profilemode.png
#     alt: "Bug Bounty Bootcamp"
#     caption: "Bug Bounty Bootcamp"
#     relative: false # To use relative path for cover image, used in hugo Page-bundles    
---
## Nmap - all in

Encontrar users con contraseñas por defecto o vacias
```
nmap -f -sS -sV -vv --script auth IP
```
Corre scripts por defecto de nmap
```
nmap -f -sS -vv --script default ip
```
Comandos menos intrusivos para el target
```
nmap -f --script safe IP -vv
```
Detectar vulnerabilidades conocidas
```
nmap -f --script vuln -vv IP -Pn
```
Revisa conexiones abiertas por malware
```
nmap -f --malware
```

```
nmap -sS -sv -f --script discovery IP
``` 

```
nmap -f --script intrusive
```
Incluye Deteccion OS
```
nmap -T4 -A example.com -vv -Pn
```

```
 nmap --script targets-asn --script-args targets-asn.asn=numberASN
```

tomando las IP del comando anterior, se puede usar masscan
```
nmap -p- -sV -iL company.txt --> 
```

```
nmap 0iL list.txt -Pn -n -sn -oG output.txt
```
```
masscan -iL output.txt -p 0-65535 - max-rate 1000
```
