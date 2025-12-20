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

També tenim dos altres comandes més completes, que son top i htop

*top* 

Top és una comanda que mostra informació en temps real sobre processos i l'ús del sistema.

<img width="1050" height="927" alt="image" src="https://github.com/user-attachments/assets/6fc41355-2501-4656-a3cc-1fc06fe2ae0d" />

Comandes interactives de top

tecla,  accio
q,      Sortir del programa.
h,      Ajuda (mostra totes les tecles disponibles).
M,      Ordena els processos per ús de Memòria.
P,      Ordena els processos per ús de CPU (opció per defecte).
k,      Matar un procés: et demanarà el PID del procés que vols tancar.
1,      Mostra el detall de cada nucli de la CPU individualment.
z,      Canvia el color de l'interfície per fer-la més llegible.

*htop*

Si top és l'eina clàssica de tota la vida, htop és la seva evolució moderna, interactiva i molt més visual.

<img width="1050" height="1035" alt="image" src="https://github.com/user-attachments/assets/6331f9b8-34d8-4d2c-add0-95d4d8614b52" />

Tecla,   Acció,    Descripció
F3,      Search,   Busca un procés pel seu nom.
F4,      Filter,   Filtra la llista perquè només vegis el que t'interessa.
F5,      Tree,     "Mostra la relació ""pare-fill"" dels processos."
F6,      Sort,     Obre un menú per triar per quina columna vols ordenar.
F9,      Kill,     Envia un senyal al procés (com el SIGKILL) per tancar-lo.
F10,     Quit,     Surt del programa.

# Comandes Bàsiques

## Adduser

La comanda bàsica per crear usuaris es adduser 

<img width="684" height="394" alt="image" src="https://github.com/user-attachments/assets/55585ba6-810c-464a-acf9-b68f4ec00f1c" />


## Deluser

Podem observar que l'usuari Manuel que habiem creat s'elimina

<img width="723" height="304" alt="imatge" src="https://github.com/user-attachments/assets/d470d46e-16e3-4a13-8aad-599524cf1c58" />

## Userdel

Aqui veiem com l'usuari 'eros' que habiem creat s'elimina 

<img width="696" height="125" alt="image" src="https://github.com/user-attachments/assets/55855805-3e51-46d0-91fa-00572640733a" />

## Useradd

Aqui utilitzem la comanda useradd per crear un usuari i fem les comprovacions adients per veure quins permisos te

<img width="511" height="121" alt="image" src="https://github.com/user-attachments/assets/c6606cd2-ff0a-4dfb-be37-6630177dae18" />

I veiem els canvis de la shell

<img width="443" height="255" alt="image" src="https://github.com/user-attachments/assets/71ee7426-00de-4ce9-9ff8-0a86b72264f9" />

## Passwd

Amb la comanda passwd podem canviar les contrasenyes dels usuaris

<img width="431" height="99" alt="image" src="https://github.com/user-attachments/assets/6750f450-e4e6-48df-ab03-c33f3e1be5e4" />

I amb la comanda usermod -L podem bloquejar l'usuari, hem de mirar l'arxiu shadow per comprovar-ho (veiem que surt al principi un ¡), fent un cat 

<img width="728" height="145" alt="image" src="https://github.com/user-attachments/assets/2c99576c-3678-412a-8abc-d12cf8c9e440" />

## Addgroup

Podem crear grups i canviar algunes coses utilitzant la comanda groupmod

<img width="735" height="378" alt="image" src="https://github.com/user-attachments/assets/fc9b3cfc-bfb7-49c6-b41d-182b0c887d91" />

Podem asignar usuaris a grups i fer algunes altres modificacions en els grups

<img width="545" height="300" alt="image" src="https://github.com/user-attachments/assets/4e33de8a-273a-410d-a4dd-4762fe8058cd" />

## ACL

- Raons principals per utilitzar ACL

   1. Flexibilitat en gestió de permisos

      Superen les limitacions del model usuari/grup/altres

      Permeten assignar múltiples usuaris i grups al mateix recurs

      Ofereixen control granular d'accés

   2. Escalabilitat en entorns complexos

      Necessàries en sistemes amb múltiples usuaris i grups

      Essencials en servidors compartits

      Importants en entorns corporatius

   3. Seguretat més precisa

      Permeten implementar polítiques d'accés detallades

      Milloren el principi de mínim privilegi

      Faciliten l'auditoria d'accés

Podem treure els permisos per a certs usuaris i no deixar que entrin a certes carpetes, utilitzant setfacl i getfacl

<img width="550" height="500" alt="image" src="https://github.com/user-attachments/assets/8e23274e-8825-4ff7-b0f8-d140d1c44083" />

Veiem que no deixa entrar a la carpeta

<img width="400" height="150" alt="image" src="https://github.com/user-attachments/assets/104ac7aa-485c-4806-ad3f-69febf2bb6dc" />

I entrant a un usuari concret veiem que no tenim permisos

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/79e47249-fe51-43d2-919a-70aeab277814" />

## Umask

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

També es poden canviar desde l'arxiu /etc/login.defs permanentment

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/f7d8d7af-5bbc-4eb9-a4f5-18dc8653dc88" />

# Còpies de seguretat i automatització de tasques

Còpies de seguretat

Una còpia de seguretat és una duplicació de les dades que permet recuperar informació en cas de pèrdua, dany, error humà, virus o qualsevol altre desastre. Aquestes còpies s’emmagatzemen de manera independent de les dades originals, preferiblement en un altre dispositiu, servidor o servei al núvol.

Normalment segueixen polítiques definides, com ara el temps de retenció, el nombre de versions guardades i la realització de proves de restauració per assegurar que les dades es poden recuperar correctament.

Tipus principals de còpia de seguretat
Còpia completa

Desa totes les dades cada vegada que es fa la còpia.

És la més lenta i la que ocupa més espai, però també la més segura i la més fàcil de restaurar, ja que només cal una única còpia per recuperar tota la informació.

Còpia incremental

Només guarda els canvis realitzats des de l’última còpia, sigui completa o incremental.

És molt ràpida i ocupa poc espai. L’inconvenient principal és que, per restaurar les dades, cal disposar de la còpia completa inicial i de totes les còpies incrementals posteriors.

Còpia diferencial

Guarda tots els canvis fets des de l’última còpia completa.

És més ràpida que la còpia completa i ocupa un espai intermig. La restauració és més senzilla que amb les incrementals, però cada nova còpia diferencial ocupa més espai fins que es fa una nova còpia completa.

Exemples de funcionament
Còpia completa

Dilluns: còpia completa
Dimarts: còpia completa
Dimecres: còpia completa

Si es perd un fitxer dijous, només cal restaurar la còpia completa de dimecres.

Còpia incremental

Dilluns: còpia completa
Dimarts: còpia incremental
Dimecres: còpia incremental

Per recuperar un fitxer perdut dijous, cal la còpia completa de dilluns i totes les còpies incrementals fins dimecres.

Còpia diferencial

Dilluns: còpia completa
Dimarts: còpia diferencial
Dimecres: còpia diferencial

Si es perd un fitxer dijous, cal la còpia completa de dilluns i l’última còpia diferencial, la de dimecres.

RAID i emmagatzematge

Els sistemes RAID combinen diversos discs perquè funcionin conjuntament, millorant el rendiment i/o la seguretat segons el tipus de RAID utilitzat.

RAID 0 uneix la capacitat i la velocitat de diversos discs, però no ofereix cap protecció: si un disc falla, es perden totes les dades.
RAID 1 crea una còpia mirall: les dades es dupliquen i, si un disc falla, l’altre continua funcionant.
RAID 5 i RAID 6 reparteixen les dades i la informació de paritat entre diversos discs, oferint un bon equilibri entre velocitat i seguretat.
RAID 10 combina la velocitat del RAID 0 amb la seguretat del RAID 1.

És important recordar que RAID no és una còpia de seguretat. Si s’esborren fitxers o un virus afecta les dades, l’error es replica a tots els discs.

Imatge de disc

Una imatge de disc és una còpia exacta de tot un disc o partició, incloent el sistema operatiu, els programes, la configuració i les dades. S’utilitza per clonar equips o restaurar un sistema complet tal com estava en un moment concret.

És molt completa, però requereix molt espai i temps per crear-se. A canvi, permet restaurar un ordinador sencer en molt poc temps.

Snapshot

Un snapshot és una captura instantània de l’estat d’un sistema de fitxers o d’un dispositiu d’emmagatzematge. Normalment depèn de la tecnologia utilitzada (LVM, ZFS, Btrfs, màquines virtuals, etc.) i és molt ràpid de crear, ja que només guarda els canvis fets a partir del moment en què es crea.

Els snapshots són útils per tornar enrere ràpidament o fer proves, però no són una còpia de seguretat segura si es guarden al mateix disc. Si el disc falla, el snapshot també es perd.

Resum final

La còpia de seguretat serveix per protegir les dades guardant-les en un lloc segur.
La imatge de disc copia tot el sistema exactament com és en un moment concret.
El snapshot permet tornar enrere ràpidament, però no protegeix contra fallades del mateix disc.

No s’ha de confiar només en snapshots locals com a única protecció. La millor estratègia combina snapshots per recuperacions ràpides i còpies de seguretat externes per protegir-se davant desastres.

1. cp -> Es una copia simple no inteligent nomes transfereix fitxers localment es molt simple de utilitzar pero no optimitzar
2. rsync -> Es una eina inteligent que nomes copia els fitxers modificats i la sincronitzacio pot ser local o en remot via ssh
3. dd -> Es una eina per a clonar discs o particions i no es inteligent copia tots els sectors

## Comanda cp
Comanda cp (teoria)

La comanda cp s’utilitza en sistemes operatius Linux i Unix per copiar fitxers i directoris d’una ubicació a una altra. Permet duplicar informació mantenint, si es vol, atributs com permisos, dates i propietari.

Funcionament general

cp copia un o més fitxers cap a un fitxer o directori de destí. Quan el destí ja existeix, el fitxer pot ser sobreescrit segons les opcions utilitzades. Per defecte, cp només copia fitxers; per copiar directoris cal indicar-ho explícitament.

Opcions i paràmetres principals Còpia recursiva

Permet copiar directoris sencers amb tots els seus subdirectoris i fitxers. Sense aquesta opció, els directoris no es copien.

Mode interactiu

Fa que el sistema demani confirmació abans de sobreescriure un fitxer existent, evitant pèrdues accidentals d’informació.

Mode forçat

Sobreescriu els fitxers de destí sense demanar confirmació, fins i tot si estan protegits contra escriptura.

Mode detallat

Mostra informació del procés de còpia, indicant quins fitxers s’estan copiant.

Actualització

Només copia els fitxers que són més nous que els del destí o que encara no existeixen, estalviant temps i espai.

Conservació d’atributs

Manté els permisos, el propietari, el grup i les dates originals dels fitxers copiats.

Mode arxiu

Realitza una còpia completa conservant l’estructura, els atributs i els enllaços, i és l’opció més utilitzada per fer còpies de seguretat de directoris.

Gestió d’enllaços

La comanda pot tractar els enllaços simbòlics de diverses maneres:

Copiar l’enllaç com a enllaç

Seguir l’enllaç i copiar el fitxer real

No seguir l’enllaç i conservar-lo tal com és

També permet crear enllaços simbòlics o enllaços durs en lloc de fer una còpia real del fitxer.

Altres funcionalitats

cp pot copiar múltiples fitxers alhora cap a un mateix directori. Permet mantenir l’estructura de directoris original quan es copien fitxers individuals. Pot limitar la còpia perquè no travessi diferents sistemes de fitxers. Es pot utilitzar com a eina bàsica dins d’estratègies de còpies de seguretat simples.

<img width="825" height="489" alt="image" src="https://github.com/user-attachments/assets/92e1093c-7301-4a57-a468-d8e45c129819" />

## Comanda rsync

La comanda rsync és una eina de Linux/Unix utilitzada per sincronitzar fitxers i directoris entre dues ubicacions, ja sigui dins del mateix sistema, entre diferents discs o entre equips a través de la xarxa. És especialment eficient per a còpies de seguretat i transferències de dades grans.

Funcionament general

rsync compara els fitxers d’origen i destí i només transfereix les diferències, fent que sigui molt més ràpid i eficient que copiar tot el contingut de nou. Pot treballar amb fitxers locals o remots i permet mantenir atributs i permisos dels fitxers originals.

Opcions i paràmetres principals Mode recursiu

Permet copiar directoris sencers, incloent subdirectoris i fitxers. Sense aquesta opció, només es copien fitxers individuals.

Conservació d’atributs

Manté propietari, grup, permisos, dates i atributs especials dels fitxers copiats. Això assegura que la còpia sigui exacta a l’original.

Compressió

Redueix la quantitat de dades transferides quan s’utilitza en xarxa, comprimint els fitxers durant la transmissió.

Modes detallats

Permet mostrar informació del procés de sincronització, indicant quins fitxers es transfereixen i quins ja estan actualitzats.

Actualització i sincronització

Només copia fitxers que han canviat o que no existeixen al destí, evitant duplicacions innecessàries i estalviant temps i espai.

Eliminació de fitxers obsolets

Permet eliminar del destí els fitxers que ja no existeixen a l’origen, mantenint les dues ubicacions sincronitzades exactament.

Modes segurs

Pot funcionar a través de connexions segures (per exemple SSH) quan es sincronitzen fitxers entre diferents equips, protegint la informació durant la transferència.

Enllaços i enllaços simbòlics

Rsync pot copiar enllaços simbòlics com a enllaços o bé seguir-los i copiar el contingut real, segons es configuri.

Altres funcionalitats

Permet filtrar fitxers per extensió, nom o directoris específics.

Admet transferències parcials per reprendre còpies interrompudes.

Pot funcionar de manera programada per automatitzar còpies de seguretat regulars.

És molt eficaç per sincronitzar grans quantitats de dades entre servidors, discs locals o sistemes de backup.

<img width="736" height="296" alt="image" src="https://github.com/user-attachments/assets/27850945-65eb-4e47-8087-42d0e98c4a55" />

## Comanda dd

La comanda dd és una eina de Linux/Unix utilitzada per copiar i transformar dades a baix nivell, normalment fitxers, discs o dispositius de blocs. És molt potent i flexible, ja que treballa amb dades binàries directament i permet fer còpies exactes sector per sector.

Funcionament general

dd llegeix dades des d’una font i les escriu en un destí especificat, amb la possibilitat de transformar-les durant el procés. Es pot utilitzar per crear imatges de discs, copiar particions, fer còpies de seguretat de dispositius complets o fins i tot escriure fitxers d’arrencada.

Opcions i paràmetres principals Input (if)

Defineix el fitxer o dispositiu d’origen d’on s’han de llegir les dades.

Output (of)

Especifica el fitxer o dispositiu de destí on s’escriuran les dades.

Block size (bs)

Permet establir la mida dels blocs de dades llegits i escrits. Ajustar aquesta mida pot millorar el rendiment de la còpia.

Count

Indica quants blocs s’han de copiar des de l’origen. Permet limitar la quantitat de dades copiades.

Skip

Permet saltar un nombre determinat de blocs al començar a llegir de l’origen, útil per treballar amb fragments de discs o fitxers grans.

Seek

Permet saltar blocs al destí abans de començar a escriure, facilitant la còpia parcial dins d’un dispositiu o fitxer.

conv

Permet aplicar transformacions a les dades durant la còpia, com per exemple canviar majúscules/minúscules, convertir entre formats o truncar dades.

Status

Mostra informació del progrés de la còpia, útil en operacions amb grans quantitats de dades.

<img width="745" height="454" alt="image" src="https://github.com/user-attachments/assets/e9b5f103-18ba-4fdb-a232-095805e88a36" />

# Atumatitzacio de tasques

## Cron

El cron es guarda a la ruta /etc/crontab i és, en essència, una agenda automatitzada que el sistema operatiu consulta cada minut per saber si ha d'executar alguna tasca

<img width="722" height="470" alt="image" src="https://github.com/user-attachments/assets/6c08e0bb-ac67-4486-abf3-5b71a1fe4e6b" />

Amb la comanda crontab -e -u 'usuari' podem especificar desde quin usuari volem entrar i el primer cop que entrem ens dirà en quin editor ho volem fer.

<img width="837" height="624" alt="image" src="https://github.com/user-attachments/assets/3d07ee0d-5343-42ca-8811-8cba7cf0bafc" />

Amb la seguent ruta podem veure tots els binaris del cron.

<img width="352" height="185" alt="image" src="https://github.com/user-attachments/assets/2f856852-543e-4804-b7c2-7ce2901a2054" />

I aquest es el anacron que està guardat en la ruta /etc/anacrontab

<img width="721" height="469" alt="image" src="https://github.com/user-attachments/assets/05d0aa01-3a19-4f21-9c2a-6e6846a2eef5" />

Ara he programat un script que conté el següent codi:

<img width="681" height="121" alt="image" src="https://github.com/user-attachments/assets/2a8153eb-71bb-41d6-9c78-a49661d54d09" />

Li dono permisos d'execució 

<img width="622" height="223" alt="image" src="https://github.com/user-attachments/assets/5fb817a7-8473-4760-8fa9-8b2bb8b456b3" />

Vaig al directori 'Documents' i creo dos imatges que seran les que copiarem

<img width="534" height="130" alt="image" src="https://github.com/user-attachments/assets/6a9115f6-dadb-46c1-9b8a-dab0eb30c220" />

Copio el script, el poso al cron.daily i comprovo que estan aññi.

<img width="754" height="100" alt="image" src="https://github.com/user-attachments/assets/b322d909-f264-422b-ad97-cb52d43cec07" />

I reemplaçem el valor per 1.

<img width="773" height="295" alt="image" src="https://github.com/user-attachments/assets/fa678fe4-dfe5-481b-ab0d-82707f231190" />

# Quotes d'usuari

Que es una quota?

En Linux, una quota és un mecanisme de control d’ús d’espai i fitxers dins d’un sistema de fitxers. Serveix per limitar la quantitat de disc o nombre d’inodes (fitxers) que un usuari o grup pot utilitzar, evitant que una sola persona ocupi tot l’espai i afecti la resta de l’equip.

Instal·larem el paquet 'quota'

<img width="736" height="542" alt="image" src="https://github.com/user-attachments/assets/af65110c-31e5-4c05-a6b7-21f987399cc2" />

Ara creem una carpeta anomenada 'dades'

<img width="371" height="91" alt="image" src="https://github.com/user-attachments/assets/dd02dd65-9efb-4df7-af3d-00bc504cc981" />

I farem el muntatge d'aquesta carpeta permanentment, a més aqui afegirem usrquota i grquota per a que puguem configurar les quotes aqui.

<img width="741" height="414" alt="image" src="https://github.com/user-attachments/assets/a9ab399f-a472-4511-b0bc-1d0e142cbcca" />

