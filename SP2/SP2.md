---
layout: default
title: "Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers"
---

# Sistemes de fitxers i particions

Començarem amb les particions de disc, per poder emmagatzemar al mateix disc, però en diferents parts i organitzar-lo millor. 

<img width="853" height="510" alt="imatge" src="https://github.com/user-attachments/assets/ac015f40-023f-44d2-bc51-8245525388b8"/>

Utilitzem la comanda tune2fs amb el grep block per veure les diferents carpetes creades per al sda5

<img width="851" height="125" alt="imatge" src="https://github.com/user-attachments/assets/45191349-7c16-44c5-a6cf-55feab66d291"/>

Per a la fragmentacio externa amb la comanda "e4defrag" ens indica si una partició fa falta fragmentar.

<img width="600" height="400" alt="imatge" src="https://github.com/user-attachments/assets/fe221678-32e0-42b4-82c9-70854e596d7b" />

# App Gparted

És una eina visual per crear, eliminar o formatar particions.

   Permet triar el sistema de fitxers (FAT32, EXT4, NTFS...) però no permet canviar la mida del bloc.

<img width="845" height="599" alt="imatge" src="https://github.com/user-attachments/assets/86742c70-b3d8-42b7-9a9f-dfde9263b293" />

Amb comandes seria utilitzar la comanda fdisk podem crear i modificar particions manuals.

# Grups, Usuaris i Permisos

*Grups*

Un grup agrupa diversos usuaris amb permisos comuns sobre arxius o directoris.
Cada usuari pertany a:

- un grup principal, i
- pot formar part de grups secundaris.

Els grups permeten definir permisos col·lectius, per exemple, donar accés a una carpeta compartida sense fer-ho usuari per usuari.

Fitxer       | Funció principal                               |

/etc/passwd  | Llista tots els usuaris definits al sistema.   |
/etc/shadow  | Desa les contrasenyes xifrades dels usuaris.   |
/etc/group   | Conté la llista de grups i els seus membres.   |
/etc/gshadow | Desa contrasenyes i administradors dels grups. |

*Usuaris*

Per crear usuaris tenim dues comandes, adduser o useradd, amb adduser demana una serie d'informació bàsica sobre l'usuari com podem veure a la captura. També faig una comprovació de permisos.

<img width="550" height="500" alt="image" src="https://github.com/user-attachments/assets/55bc29a4-02c0-4109-8d9c-97e303d6b36e" />


Es pot donar o treure permisos, tant a directoris com a arxius

<img width="550" height="500" alt="image" src="https://github.com/user-attachments/assets/0545fd02-0aba-4816-8ef8-651d935f88a8" />

*Permisos*

En sistemes UNIX, els permisos fan part del sistema. Sense ells no podem visualitzar, alterar o executar fitxers, entrar en directoris o llistar-ne el contingut.

- El primer indica si es directori (d) o fitxer (-)
- Els tres primers atributs després del primer (que identifica directoris), són per a *propietaris*
- Els tres següents són per a *grup*
- Els ultims són per als altres usuaris/ grups

| Fitxer       | Funció principal                               |
| ------------ | ---------------------------------------------- |
| /etc/passwd  | Llista tots els usuaris definits al sistema.   |
| /etc/shadow  | Desa les contrasenyes xifrades dels usuaris.   |
| /etc/group   | Conté la llista de grups i els seus membres.   |
| /etc/gshadow | Desa contrasenyes i administradors dels grups. |

Per mirar quins permisos tenim a un directori podem utilitzar la comanda umask

<img width="273" height="65" alt="imatge" src="https://github.com/user-attachments/assets/e7cad38c-2109-4d76-9aac-ca7b1d1dfa8c" />

També tenim l'opció d'entrar al fitxer /etc/login.defs, en aquest arxiu podem configurar coses respecte a la contrasenya de l'usuari, com la duració, o per veure si els permisos, per a tots els usuaris que entrin a aquell concret directori o fitxer, son els mateixos, però seran permisos per a tots els usuaris, no específics com amb la comanda umask.

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/659e0cb5-d12e-4e92-bdc1-98a00d2e9fb1" />

A l'arxiu .profile també podem veure quins permisos tenen els usuaris que no siguin administradors

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/83513d93-9fdb-4cc9-a67e-2782cfe4940b" />

Utilitzant umask podem canviar els permisos a un directori o fitxer com veiem a continuacio, podem decidir els seus permisos.

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/75fa46ee-0d08-45f4-b280-8e80efc4098f" />

Veiem com els permisos han canviat

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/f8f73cf0-57fe-44c2-9247-ccbf528c3eee" />

També es poden canviar desde l'arxiu /etc/login.defs

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/f7d8d7af-5bbc-4eb9-a4f5-18dc8653dc88" />

Podem treure els permisos per a certs usuaris i no deixar que entrin a certes carpetes, utilitzant setfacl i getfacl

<img width="550" height="500" alt="image" src="https://github.com/user-attachments/assets/8e23274e-8825-4ff7-b0f8-d140d1c44083" />

Veiem que no deixa entrar a la carpeta

<img width="400" height="150" alt="image" src="https://github.com/user-attachments/assets/104ac7aa-485c-4806-ad3f-69febf2bb6dc" />

I entrant a un usuari concret veiem que no tenim permisos

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/79e47249-fe51-43d2-919a-70aeab277814" />


# Gestió de processos

Els processos són programes en execució dins del sistema. Cada procés té un PID (Process ID), un usuari propietari i pot estar en diferents estats (actiu, en espera, aturat...). El sistema operatiu planifica i reparteix el temps de CPU entre ells.

*Eines bàsiques per gestionar-los*

- ps, top, htop → veure processos actius.
- kill, pkill → finalitzar un procés per PID o nom.
- nice, renice → ajustar la prioritat d’execució.
- systemctl, service → controlar serveis (daemons).

A nivell pràctic, cada procés hereta permisos de l’usuari que l’ha iniciat i pot estar vinculat a un servei o a una sessió d’usuari.

*Gestió d'usuaris i grups i permisos*
La seguretat en Linux es basa en usuaris i grups, que determinen qui pot accedir o modificar arxius i processos.

*Tipus d’usuaris*

- Usuari normal: pot iniciar sessió i executar programes dins del seu espai.
- Superusuari (root): té tots els permisos i pot gestionar el sistema sencer.
- Usuari de servei (daemon): creat per executar serveis com www-data, mysql, sshd (no inicien sessió interactiva).
- Usuari de sistema: similar al d’un servei, amb UID baix (<1000), reservat per processos interns.


Un grup agrupa diversos usuaris amb permisos comuns sobre arxius o directoris.
Cada usuari pertany a:

- un grup principal, i
- pot formar part de grups secundaris.

Els grups permeten definir permisos col·lectius, per exemple, donar accés a una carpeta compartida sense fer-ho usuari per usuari.

| Fitxer       | Funció principal                               |
| ------------ | ---------------------------------------------- |
| /etc/passwd  | Llista tots els usuaris definits al sistema.   |
| /etc/shadow  | Desa les contrasenyes xifrades dels usuaris.   |
| /etc/group   | Conté la llista de grups i els seus membres.   |
| /etc/gshadow | Desa contrasenyes i administradors dels grups. |

