---
layout: default
title: "Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers"
---

# Sistemes de fitxers i particions

## Mida sector

La unitat mínima fisica del disc on es guarden totes les dades, per defecte són 512 bytes, i no es pot cambiar la mida.

## Mida block

És la unitat mínima lògica on es guarden les dades del Sistema Operatiu, normalment solen ser de 4096 bytes, i es pot canviar la mida quan es formateja el disc.
També anomentat clúster, i el sistema de fitxers pot ser diferent a cada partició del disc.

Exemple:

- En aquest cas podem veure que la mida amb la primera comanda el que pesa el text són 5 bytes, i amb la segona comanda podem observar la mida en el disc, que és l'espai mínim que el sistema de fitxers reserva per a un fitxer.

<img width="480" height="270" alt="imatge" src="https://github.com/user-attachments/assets/d24f2dbe-64b5-4455-87a5-ed271c11cece" />

# Tipus de formateig

Baix nivell: Borra sistema de fitxers, borra formateig, etc. És a dir, que borra totes les dades i el deixa com si fós nou, hem de tenir en compte que desde el sistema operatiu no es pot formatar, es necessiten programes adequats.

Mig nivell: Només borra sistemes de fitxers, però si hi han sectors defectuosos els marca pero no els arregla.

Alt nivell: El format d'alt nivell només borra el sistema de fitxers.

# Gestió de Particions

Començarem amb les particions de disc, per poder emmagatzemar al mateix disc, però en diferents parts i organitzar-lo millor. Utilitzant la comanda fdisk -l podem veure l'espai.

<img width="550" height="500" alt="imatge" src="https://github.com/user-attachments/assets/ac015f40-023f-44d2-bc51-8245525388b8"/>

Utilitzem la comanda tune2fs amb el grep block per veure les diferents carpetes creades per al sda5 i veure la mida del bloc de la partició.

<img width="750" height="125" alt="imatge" src="https://github.com/user-attachments/assets/45191349-7c16-44c5-a6cf-55feab66d291"/>

Per a la fragmentacio externa amb la comanda "e4defrag" ens indica si una partició fa falta fragmentar.

<img width="600" height="400" alt="imatge" src="https://github.com/user-attachments/assets/fe221678-32e0-42b4-82c9-70854e596d7b" />

I en cas de voler fragmentar-ho podem executar-la sense el paràmetre '-c'.

# App Gparted

Hem de descarregar l'eina amb la comanda 'sudo apt install gparted' i un cop descarregada l'executem, posem la nostra contrasenya i ja la podem fer servir. 

<img width="480" height="270" alt="imatge" src="https://github.com/user-attachments/assets/d9709fc1-5a22-4acf-aec7-b3d70d7ed504" />

És una eina visual per crear, eliminar o formatar particions.

   Permet triar el sistema de fitxers (FAT32, EXT4, NTFS...) però no permet canviar la mida del bloc.

Entrem a l'eina i seleccionem el disc /dev/sdb.

<img width="780" height="538" alt="imatge" src="https://github.com/user-attachments/assets/5fc54fe8-575f-4e41-b0c9-7280782ceb0b" />

Seleccionem l'opció 'Dispositivo' i 'Crear tabla de particiones'.

<img width="780" height="538" alt="imatge" src="https://github.com/user-attachments/assets/c1c27bd6-97f8-4e65-8e65-a25c40730636" />

Ens sortirà l'avís i hem de canviar el tipus de taula de particions i posar-ho en 'gpt'.

<img width="780" height="538" alt="imatge" src="https://github.com/user-attachments/assets/ea354c27-4db4-43ee-95f7-eec5ab0744d8" />

Un cop ho tenim fem clic dret damunt de la partició i crear una nova.

<img width="780" height="609" alt="imatge" src="https://github.com/user-attachments/assets/c82d47fe-0ead-429d-9102-8820886d54aa" />

Aqui posem l'opció NTFS i podem canviar la mida de la partició que volem.

<img width="780" height="535" alt="imatge" src="https://github.com/user-attachments/assets/bd237775-8274-4486-b1cd-f3fe95afcb3c" />


I per últim hem d'aplicar els canvis, per fer-ho cliquem el tick verd de adalt i apliquem canvis

<img width="780" height="535" alt="imatge" src="https://github.com/user-attachments/assets/629bc579-72f5-41ba-b119-80483fc7520c" />

I apliquem.

<img width="780" height="535" alt="imatge" src="https://github.com/user-attachments/assets/3a0943b7-a6a8-403a-bf19-545c311a9e8c" />


Amb comandes seria utilitzar la comanda fdisk, podem crear i modificar particions manuals.

Utilitzem el fdisk i seleccionem el disc que volem fer la particio 

<img width="731" height="488" alt="imatge" src="https://github.com/user-attachments/assets/8006bbc4-0c97-44d0-a5b4-ae21eabf900b" />

Creem la partició

<img width="731" height="324" alt="imatge" src="https://github.com/user-attachments/assets/e56b8f94-4dc4-44b6-9bc2-6ae8918bed1d" />

Aqui podem observar que esta creat correctament

<img width="690" height="256" alt="imatge" src="https://github.com/user-attachments/assets/19b5aeb7-3823-42b8-8076-4fd027e475cd" />

I amb la comanda mkfs.ext4 podem canviar la mida del bloc, podem posar la mida que vulguem. 

<img width="690" height="256" alt="imatge" src="https://github.com/user-attachments/assets/7b6be023-2bd5-4d0b-b474-ea25f2b9b67d" />

I podem comprovar que s'han fet els canvis correctament amb la comanda 'tune2fs'

<img width="563" height="97" alt="imatge" src="https://github.com/user-attachments/assets/7085df75-dc36-4f7a-8299-206cbe4450ee" />

I amb NTFS per a que Windows ho reconeixi.

<img width="564" height="109" alt="imatge" src="https://github.com/user-attachments/assets/91a69f98-31f1-45d9-a0b9-57e6fbdc14ea" />


# Grups, Usuaris i Permisos

*Grups*

A un grup s'agrupen diversos usuaris amb permisos comuns sobre arxius o directoris.
Cada usuari pertany a:

- un grup principal
- o pot formar part de grups secundaris.

Els grups permeten definir permisos col·lectius, per exemple, donar accés a una carpeta compartida sense fer-ho usuari per usuari.

| Fitxer       | Funció principal                               |

| /etc/passwd  | Llista tots els usuaris definits al sistema.   |
| /etc/shadow  | Desa les contrasenyes xifrades dels usuaris.   |
| /etc/group   | Conté la llista de grups i els seus membres.   |
| /etc/gshadow | Desa contrasenyes i administradors dels grups. |



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

# Fitxers importants

En linux, la informació d'usuaris i grups es gestiona de manera centralitzada mitjançant fitxers de configuració de text ubicats dins del directori /etc.

/etc/passwd

<img width="723" height="454" alt="imatge" src="https://github.com/user-attachments/assets/5b1c27b1-522d-48ad-9b96-f4eadb8e1d7d" />

Cada línia representa un usuari i conté 7 camps separats per dos punts, dins trobem els usuaris que poden accedir a aquest sistema:

nom_usuari:x:UID:GID:GECOS:directori_home:shell 
          
El primer que trobem es el nom de l'usuari, la contrasenya, UID és el número d'identificació, GID el número del grup al que pertany, GECOS és la informació opcional sobre l'usuari, directori_home és el directori personal de l'usuari i la shell és l'interpret d'ordres que s'executa en iniciar

/etc/shadow

<img width="723" height="468" alt="imatge" src="https://github.com/user-attachments/assets/d2ad75f3-5977-45d3-8c17-acf46a5de7a3" />

Aquest arxiu guarda l'informació de les contrasenys dels usuaris i polítiques d'expiració. És un arxiu segur que només pot llegir l'usuari root.

Cada línia torna a representar cada usuari i conté 9 camps separats per dos punts.

/etc/group

<img width="723" height="468" alt="imatge" src="https://github.com/user-attachments/assets/3e5a8679-4cf7-4d08-bf12-ec1e953d9cdb" />

L'arxiu /etc/group conté la informació dels grups del sistema i els seus membres. Defineix els grups d'usuaris i les seves relacions.

Cada línia representa un grup i conté 4 camps separats per dos punts.

/etc/gshadow 

<img width="723" height="473" alt="imatge" src="https://github.com/user-attachments/assets/3a9a6172-0ecc-404d-b52e-a3d305987da6" />

Al gshadow es guarda l'informació segura dels grups, incloent contrasenyes de grups i administradors, diguèssim que és el fitxer /etc/group però segura.

/etc/skel

El directori que conté els arxius de configuració dels usuaris és el /etc/skel, quan creeu un nou usuari al Linux (usant ordres com useradd o adduser), el sistema no només crea una entrada al fitxer de contrasenyes; també heu de configurar un entorn de treball inicial.

En lloc de crear fitxers de configuració des de zero cada vegada, el sistema simplement fa un "copy-paste" de tot el que hi ha dins de /etc/skel cap al nou directori /home/nou_usuari, i per això és un dels directoris més importants. 

<img width="723" height="237" alt="imatge" src="https://github.com/user-attachments/assets/604206ab-1e7b-4b23-b04f-6032aec25572" />

El '.bashrc' és, probablement, el fitxer més important de la llista per a un usuari comú.

Què fa: S'executa cada vegada que l'usuari obre una terminal interactiva nova.

Per a què serveix: S'utilitza per definir "àlies" (abreviatures de comandes), personalitzar el color i el format del text de la línia de comandes (el prompt) o carregar variables d'entorn.
    
<img width="723" height="475" alt="imatge" src="https://github.com/user-attachments/assets/da7b4254-aaa7-47bc-8d83-54c9db6cb6d0" />

El '.profile' 

Què fa: Aquest fitxer s'executa només una vegada, en el moment en què l'usuari inicia la sessió al sistema (per exemple, en fer el login gràfic o per SSH).

Per a què serveix: Normalment s'utilitza per configurar camins de programes (PATH) o paràmetres que han d'estar disponibles durant tota la sessió, no només dins de la terminal. Sovint conté un codi que crida al fitxer .bashrc.

<img width="723" height="475" alt="imatge" src="https://github.com/user-attachments/assets/7e56a050-51e5-4a00-bf2f-b7853c4f1854" />

El '.bash_logout'

Què fa: S'executa automàticament quan l'usuari tanca la sessió de la terminal (quan surts de la terminal o fas un exit).

Per a què serveix: Sol estar gairebé buit, però es pot fer servir per a tasques de neteja, com ara esborrar els fitxers temporals creats durant la sessió o netejar la pantalla per seguretat.

<img width="723" height="475" alt="imatge" src="https://github.com/user-attachments/assets/1bb60c38-204a-4357-8c9b-5a9cc538049f" />


# Gestió de processos

Els processos són programes en execució dins del sistema. Cada procés té un PID (Process ID), un usuari propietari i pot estar en diferents estats (actiu, en espera, aturat...). El sistema operatiu planifica i reparteix el temps de CPU entre ells.

*Eines bàsiques per gestionar-los*

- ps, top, htop → veure processos actius.
- kill, pkill → finalitzar un procés per PID o nom.
- nice, renice → ajustar la prioritat d’execució.
- systemctl, service → controlar serveis (daemons).

A nivell pràctic, cada procés hereta permisos de l’usuari que l’ha iniciat i pot estar vinculat a un servei o a una sessió d’usuari.

Començarem utilitzant pstree

| Paràmetre | Funció                                              |
| --------- | --------------------------------------------------- |
| -p        | Mostra el PID de cada procés.                       |
| -u        | Mostra l’usuari propietari de cada procés.          |
| -h        | Ressalta el procés actual (útil quan es filtra).    |
| -n        | Ordena processos per PID dins de cada arbre.        |
| -a        | Mostra els arguments complets del procés (cmdline). |

Veiem el pstree del root i també filtrant per la terminal

<img width="736" height="756" alt="imatge" src="https://github.com/user-attachments/assets/2cff2ab8-43eb-4aad-be26-aa1b32bbd782" />

<img width="729" height="96" alt="imatge" src="https://github.com/user-attachments/assets/c71a957d-4e40-4d4c-8553-2ee69df44d5b" />

*ps*
Aquesta comanda mostra informació sobre una seleccio dels processos actius. Una variant seria top, que el que fa és, una actualització repetitiva de la selecció i la informació mostrada.

<img width="729" height="701" alt="imatge" src="https://github.com/user-attachments/assets/f7e0504d-8c0e-4c8d-9970-e9a8550d4de1" />

Si volem matar o finalitzar algun d'aquests processos, hauriem d'utiltizar les comandes 'kill' 

Uns exemples de la comanda podrien ser 

kill PID: Demana al procés finalitzar netament
kill -9 PID: Mata immediatament, sense netejar recursos
kill -1 PID: Demana al procés que recarregui la configuració
kill -STOP PID: Pausa l’execució del procés
kill -CONT PID: Continua un procés pausat
kill -2 PID: Senyal d’interrupció (Ctrl+C)
kill -6 PID: Senyal d’error abortat, sovint genera core dump

Aqui tenim un exemple obrint xclock al fons amb el "&" i matant-lo suau, mentres comprovem amb ps aux que s'ha mort.

<img width="729" height="304" alt="imatge" src="https://github.com/user-attachments/assets/1b0b08e1-5e82-4478-b3eb-5a249f186865" />

També tenim dos altres comandes més simples
# Comandes Bàsiques

## Adduser



## Deluser

Podem observar que l'usuari Manuel que habiem creat s'elimina

<img width="723" height="304" alt="imatge" src="https://github.com/user-attachments/assets/d470d46e-16e3-4a13-8aad-599524cf1c58" />
