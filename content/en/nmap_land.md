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
```bash
nmap -f -sS -sV -vv --script auth IP
```
Corre scripts por defecto de nmap
```bash
nmap -f -sS -vv --script default ip
```
Comandos menos intrusivos para el target
```bash
nmap -f --script safe IP -vv
```
Detectar vulnerabilidades conocidas
```bash
nmap -f --script vuln -vv IP -Pn
```
Revisa conexiones abiertas por malware
```bash
nmap -f --malware
```

```bash
nmap -sS -sv -f --script discovery IP
``` 

```bash
nmap -f --script intrusive
```
Incluye Deteccion OS
```bash
nmap -T4 -A example.com -vv -Pn
```

```bash
 nmap --script targets-asn --script-args targets-asn.asn=numberASN
```

tomando las IP del comando anterior, se puede usar masscan
```bash
nmap -p- -sV -iL company.txt --> 
```

```bash
nmap 0iL list.txt -Pn -n -sn -oG output.txt
```
```bash
masscan -iL output.txt -p 0-65535 - max-rate 1000
```
```bash
#!/usr/bin/env bash
#### Script finds UP hosts and its HOSTNAME
#### Usage:
#### sh nmap_find_hostname.sh IP/MASK
#### eg.: sh nmap_find_hostname.sh 192.168.0.0/16

nmap -sn $1 -oG - | awk '$4=="Status:" && $5=="Up" {print $2, $3}'
```
