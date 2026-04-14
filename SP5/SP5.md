---
layout: default
title: 'Sprint 5: Monitoratge, Auditories i Programari Client/Servidor'
---


## Logs
### Exercici 1: Fer captures del monitor del sistema

Els logs del sistema es troben a /var/log. Tots els serveis del sistema generen logs, però algunes aplicacions tenen els logs a les seves pròpies carpetes.

Llistem el contingut de /var/log per veure tots els fitxers de log disponibles:

<img width="722" height="460" alt="image" src="https://github.com/user-attachments/assets/b1262717-fb0a-409f-9628-12deb7f4dce2" />

Visualitzem el contingut del log principal del sistema (syslog) amb cat:

<img width="723" height="256" alt="image" src="https://github.com/user-attachments/assets/fdebee24-c91f-406a-ab1b-5b2b9df9ea8a" />

Podem seguir en temps real els nous missatges del syslog amb tail -f /var/log/syslog:

<img width="736" height="405" alt="imatge" src="https://github.com/user-attachments/assets/e3fa242c-06d5-40a0-8d6a-b36e112d46af" />

## Rotació de logs del sistema

La rotacio de logs s'encarrega d'arxivar i eliminar els logs antics per evitar que el disc s'ompli. La configuració de logrotate es troba a /etc/logrotate.d/:

<img width="664" height="560" alt="image" src="https://github.com/user-attachments/assets/228b3edd-7ad6-4963-9db1-3b14b6e0ee38" />

Obrim el fitxer de configuració principal de rsyslog i veiem quina es la ruta per defecte

<img width="716" height="323" alt="image" src="https://github.com/user-attachments/assets/74b45eb2-50fd-4df9-afe2-bf111278f2f6" />

## Proves amb la comanda logger
La comanda logger permet enviar missatges als logs del sistema especificant la facility (origen) i la priority (nivell de gravetat).

<img width="719" height="480" alt="image" src="https://github.com/user-attachments/assets/a45b6acf-4943-4930-8145-5738783fb240" />

I ara per al mail.notice

<img width="722" height="479" alt="image" src="https://github.com/user-attachments/assets/5178cbf9-f621-4479-92ed-8ebd5ef0a1a3" />

<img width="725" height="79" alt="image" src="https://github.com/user-attachments/assets/37375e74-6c46-4a4a-84e2-fa77fa4002f6" />

Veiem que surten totes les proves menys la que hem creat després d’editar el 50-default.conf

<img width="723" height="205" alt="image" src="https://github.com/user-attachments/assets/5d4e8ff3-2a48-4432-9d7a-43c808053dc7" />

Ara com hem creat l’arxiu al .err si que surt al cat

<img width="721" height="184" alt="image" src="https://github.com/user-attachments/assets/914b859f-842c-44b6-bf5c-6428f8aea189" />

Amb .crit no surt

<img width="720" height="191" alt="image" src="https://github.com/user-attachments/assets/96f648b8-dff9-49e3-8b2e-71c94bbe9150" />

<img width="722" height="277" alt="image" src="https://github.com/user-attachments/assets/fcdbd6cf-1aa2-469a-9f04-f81f56d6c6b6" />

<img width="721" height="167" alt="image" src="https://github.com/user-attachments/assets/c7b709d5-2b2d-45f2-82ec-6bb0f438178c" />

Tots els arxius que siguin .crit

<img width="722" height="100" alt="image" src="https://github.com/user-attachments/assets/5b3c014e-1ae4-4e69-b854-b7827f2640ba" />

## Consultes amb journalctl

journalctl permet consultar el journal del sistema (systemd). Podem filtrar per prioritat o per facility.

Filtrem per els que siguin mail

<img width="714" height="213" alt="image" src="https://github.com/user-attachments/assets/fcec7695-c6c0-4acd-8641-53841ea4c94a" />

## Exercici 2: Enviar logs remotament a una altra màquina

En aquest exercici configurem dues màquines:

    ferranserver (IP 10.0.2.15) → actua com a servidor de logs (rep els logs)
    ferranbernis1-VirtualBox → actua com a client (envia els logs)

Configuració del servidor (ferranserver)

Al servidor creem /etc/rsyslog.d/10-remote.conf per habilitar la recepció de logs per UDP i TCP al port 514 i desar-los a /var/log/remote/<hostname>/syslog.log:

<img width="800" height="325" alt="imatge" src="https://github.com/user-attachments/assets/cb3351f8-059c-42a5-a57a-c5fda909dd09" />

Comprovem que rsyslog escolta al port 514 tant per UDP com per TCP amb ss -tulpn | grep 514:

<img width="1016" height="191" alt="imatge" src="https://github.com/user-attachments/assets/496e4379-7018-466b-90ca-c66856e083bc" />

### Configuració del client (ferranbernis1-VirtualBox)

Al client creem /etc/rsyslog.d/90-forward.conf amb la directiva *.* @@10.0.2.15:514 per reenviar tots els logs al servidor via TCP:

<img width="706" height="60" alt="imatge" src="https://github.com/user-attachments/assets/d98c23f8-2feb-46d3-a274-c9221d64acb0" />

**Prova**: enviar un log des del client

Des del client enviem un missatge de prova amb logger "PROVA":

<img width="548" height="67" alt="imatge" src="https://github.com/user-attachments/assets/3e6ce968-8ed8-436b-a411-771762387b7a" />

**Verificació al servidor**

Al servidor comprovem que s'ha creat la carpeta remota per a cada màquina client dins de /var/log/remote/:

<img width="733" height="165" alt="imatge" src="https://github.com/user-attachments/assets/813b634f-2a9d-4c04-a9a6-170e4d86c235" />

Dins de la carpeta del client (ferranbernis1-VirtualBox) hi ha el fitxer syslog.log amb els logs rebuts:

<img width="739" height="116" alt="imatge" src="https://github.com/user-attachments/assets/f1b68db7-df38-4244-86e1-942d85193db7" />

Finalment, visualitzem el contingut del syslog.log remot i confirmem que el missatge "PROVA" enviat pel client ha arribat correctament al servidor:

<img width="1574" height="773" alt="imatge" src="https://github.com/user-attachments/assets/32c6e6bd-3cdb-4bcb-9c07-79869b9ad3f5" />

## Servidor de actualitzacions
### Per què és recomanable tenir un servidor d'actualitzacions

- Centralitza totes les actualitzacions de la xarxa, permetent controlar quines es fan i quan.
- Evita errors i problemes d’incompatibilitat entre equips.
- Estalvia ample de banda, ja que cada actualització es baixa només una vegada al servidor local.
- Millora la seguretat mantenint tots els dispositius amb els últims parches.
- Facilita la gestió i els informes sobre l’estat de les actualitzacions.
- Redueix la feina administrativa automatitzant el procés i estalviant temps.

### Paquet instal·lat a classe

El paquet escollit és apt-mirror, que permet crear un mirall local dels repositoris d'Ubuntu (i d'altres) per distribuir actualitzacions i paquets a tots els clients de la xarxa sense que cada equip hagi de descarregar-los d'Internet.

Per exposar el mirall als clients s'utilitza Apache2 com a servidor web HTTP.

- Instal·lació d'Apache2

Primer instal·lem el servidor web Apache2, que servirà els paquets als clients via HTTP:

<img width="1061" height="352" alt="1" src="https://github.com/user-attachments/assets/d1f1a301-7a65-4b39-b28d-4c1128b6f32c" />

- Instal·lació d'apt-mirror

A continuació instal·lem el paquet apt-mirror, que s'encarregarà de descarregar i mantenir una còpia local dels repositoris configurats:

<img width="1038" height="409" alt="2" src="https://github.com/user-attachments/assets/cd3b336d-b272-43d0-957c-d9bbc87d959e" />

- Configuració del fitxer /etc/apt/mirror.list

Editem /etc/apt/mirror.list per indicar quins repositoris volem replicar. En aquest cas configurem els repositoris principals d'Ubuntu Jammy (jammy, jammy-security, jammy-updates) i també el repositori de Google Chrome:

<img width="1038" height="674" alt="3" src="https://github.com/user-attachments/assets/058c7b16-0095-4825-9938-85b5af3a8ff7" />

<img width="1012" height="660" alt="4" src="https://github.com/user-attachments/assets/0092c1ec-1e1e-47f7-964f-eb7cad47d4d0" />

- Execució d'apt-mirror

Executem la comanda apt-mirror per iniciar la descàrrega dels paquets configurats. El procés descarrega els índexs i després els arxius:

<img width="1047" height="747" alt="5" src="https://github.com/user-attachments/assets/54115a80-5cc3-4ae4-86fa-5c85fb83afc6" />

- Creació del enllaç simbòlic a Apache2

Un cop descarregats els paquets, creem un enllaç simbòlic (ln -s) des del directori on apt-mirror desa els fitxers (/var/spool/apt-mirror/mirror/dl.google.com/) fins a /var/www/html/, perquè Apache els pugui servir als clients:

<img width="983" height="159" alt="6" src="https://github.com/user-attachments/assets/6e9aecd9-bfe0-45d1-ba41-36446d7da9ea" />

- Configuració del client: /etc/apt/sources.list

Al client editem el fitxer /etc/apt/sources.list per apuntar al servidor mirror local (http://10.0.2.15) en lloc dels repositoris originals d'Internet. Així totes les actualitzacions es descarregaran des del servidor intern:

<img width="800" height="172" alt="7" src="https://github.com/user-attachments/assets/7df6d559-c7d9-443a-9753-0920ce80f007" />

- Afegir la clau GPG de Google al client

Per poder instal·lar paquets del repositori de Google des del mirror local, cal afegir la seva clau de signatura GPG amb wget i apt-key add:

<img width="815" height="166" alt="8" src="https://github.com/user-attachments/assets/59021160-8ca3-4f5f-919b-da516549ca1d" />

- Actualització del client (apt update)

Executem apt update al client per actualitzar la llista de paquets disponibles. Es pot veure com els repositoris ara s'obtenen des del servidor intern (http://10.0.2.15) en lloc d'Internet:

<img width="894" height="135" alt="9" src="https://github.com/user-attachments/assets/90a696e5-d126-4aef-b923-fb42f2982378" />

- Instal·lació de Google Chrome des del mirror local

Finalment instal·lem google-chrome-stable des del client. El paquet es descarrega des del servidor mirror intern (http://10.0.2.13/dl.google.com/...), demostrant que el servidor d'actualitzacions funciona correctament:

<img width="876" height="260" alt="10" src="https://github.com/user-attachments/assets/1c149632-e3a6-4888-952a-13e5aaa2bd89" />

## Activitat individual

Per a l'activitat individual s'ha configurat un segon repositori mirror: el repositori oficial de nginx. Es tracta d'un repositori lleuger (menys paquets que Ubuntu sencer) i ideal per demostrar el funcionament del servidor d'actualitzacions amb un repositori diferent.

### Configuració del mirror.list amb nginx

Afegim al fitxer /etc/apt/mirror.list la línia del repositori oficial de nginx (http://nginx.org/packages/ubuntu jammy nginx), a més del repositori de Google Chrome que ja teníem configurat anteriorment:

<img width="859" height="519" alt="imatge" src="https://github.com/user-attachments/assets/15b85be3-5cb5-4e7b-a48c-84ca82a82d1f" />

### Execució d'apt-mirror

Executem apt-mirror per descarregar els índexs i paquets del repositori de nginx. El procés indica que es descarregaran 1,2 GiB de paquets al servidor local:

<img width="1015" height="559" alt="imatge" src="https://github.com/user-attachments/assets/df1503e3-dfa9-43dc-b4bd-607c36d45cd6" />

### Creació de l'enllaç simbòlic a Apache2

Un cop descarregats els paquets de nginx, creem un nou enllanç simbòlic (ln -s) des de /var/spool/apt-mirror/mirror/nginx.org/ fins a /var/www/html/, perquè Apache pugui servir-los als clients. Verifiquem amb ls que ara hi ha dos directoris al servidor web: dl.google.com i nginx.org:

<img width="852" height="86" alt="imatge" src="https://github.com/user-attachments/assets/c1084eb8-6991-417d-97df-75f1f5e2c398" />

### Configuració del client: afegir nginx al sources.list

Al client editem /etc/apt/sources.list i afegim la línia del repositori de nginx apuntant al servidor mirror intern (http://10.0.2.13/nginx.org/packages/ubuntu jammy nginx):

<img width="771" height="487" alt="imatge" src="https://github.com/user-attachments/assets/595604c1-d579-4009-9298-dc026595fad5" />

### Afegir la clau GPG de nginx al client

Per poder instal·lar paquets del repositori de nginx sense errors de signatura, cal afegir la clau GPG oficial de nginx al client amb wget i apt-key add:

<img width="864" height="112" alt="imatge" src="https://github.com/user-attachments/assets/3a74e4e4-2bbe-4711-a8a5-527027ebef77" />

### Actualització del client (apt update)

Executem apt update al client. Es pot veure com ara es descarrega el llistat de paquets de nginx directament des del servidor intern (http://10.0.2.13/nginx.org/packages/ubuntu), indicant que el mirror local funciona correctament:

<img width="816" height="214" alt="imatge" src="https://github.com/user-attachments/assets/1570adbd-5f86-43eb-8dd1-20b2a7677fcc" />

### Instal·lació de nginx des del mirror local

Finalment instal·lem nginx des del client. El paquet es descarrega des del servidor mirror intern (http://10.0.2.13/nginx.org/packages/ubuntu), confirmant que el servidor d'actualitzacions distribueix correctament el repositori de nginx a la xarxa local:

<img width="865" height="336" alt="imatge" src="https://github.com/user-attachments/assets/c989077d-9652-415f-ac3f-8dac29e44aa6" />
