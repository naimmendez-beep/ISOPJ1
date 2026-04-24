---
layout: custom
title: "Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers"
---
# Fase 1 - Preparació del sistema

### Pas 1 – Afegir un nou disc virtual a la màquina virtual
Per ampliar l'emmagatzematge de la màquina virtual cal afegir un nou disc des de la configuració de VirtualBox. Fem clic a la icona per afegir un nou disc dur virtual i seleccionem Crea un nou disc.

<img width="875" height="536" alt="imatge" src="https://github.com/user-attachments/assets/8ada1038-1ebd-4d1f-b857-a0300b66b19c" />

El creem i un cop creat l'haurem de seleccionar

<img width="920" height="792" alt="imatge" src="https://github.com/user-attachments/assets/d7bd7f15-8036-4497-a987-6b760ae8f08a" />

### Pas 2 – Iniciar Windows i obrir Gestió de discs

Hem d'iniciar el disc, ja que windows el detecta pero es com si no estigués funcionant, anem a configuració i "crear y formatear particiones de discos".

Veiem que el disc dur el reconeix però no està assignat.

<img width="751" height="596" alt="imatge" src="https://github.com/user-attachments/assets/92a7f814-2bb7-4d90-a236-53b2ab829cbe" />

### Pas 3 – Inicialitzar el disc i crear dues particions: Dades (NTFS) i Portable (FAT32)

Hem de crear la partició fent clic dret damunt el disc virtual i seleccionant l'opció "Nuevo volumen simple".

<img width="609" height="218" alt="imatge" src="https://github.com/user-attachments/assets/9aeb0dd1-871a-4174-a62e-91635a30a42b" />

Hem de seleccionar el tamany del volum (en el meu cas he ficat 5000 MB o 5 GB). I la següent opció és assignarli una lletra, s'escogeix la que vulguis, jo l'he deixat la 'E'.

<img width="500" height="393" alt="imatge" src="https://github.com/user-attachments/assets/cb374b90-22a7-4083-b396-8c513346d4a5" />

Formatem la partició amb el sistema de fitxers NTFS, que és el format natiu de Windows i l'únic que suporta quotes de disc i permisos ACL avançats. L'etiqueta del volum serà el nom que li volguem possar.

<img width="500" height="392" alt="imatge" src="https://github.com/user-attachments/assets/da387414-921b-44a8-9806-7d8bb6d75f0b" />

Per últim et diu les opcions que has escollit per si hi ha algun error i si no es així li donarem a 'FInalizar'.

<img width="496" height="393" alt="imatge" src="https://github.com/user-attachments/assets/b67ed93e-581f-4a50-b6b5-d8f6b9843dd5" />

Tornem a fer el mateix per a la partició sense assignar i escollim el tamany per defecte (que es el volum restant).

<img width="498" height="393" alt="imatge" src="https://github.com/user-attachments/assets/d65bbe00-efb3-4ff7-9ea9-e4c8fc27a1e1" />

Continuem amb la configuració i aquesta partició haurà de ser en FAT32 i anomenada 'Dades'

<img width="500" height="392" alt="imatge" src="https://github.com/user-attachments/assets/985e683d-8933-470c-b3a7-5c4db459aaf5" />

Finalitzem la configuració 

<img width="497" height="392" alt="imatge" src="https://github.com/user-attachments/assets/250cb780-feb4-41df-9c2e-6a10c097aa8b" />

### Pas 4 – Assignar lletres i comprovar amb diskpart la configuració

**Per verificar la configuració de manera exacta, obrim una consola CMD com a administrador i executem diskpart**

<img width="730" height="505" alt="imatge" src="https://github.com/user-attachments/assets/ffc247da-20c1-46a1-b839-360fcbbc48f6" />

# Fase 2 – Quotes i usuaris

### Pas 5 – Activar quotes de disc a la partició Dades (NTFS)

Les quotes de disc a Windows permeten limitar l'espai que cada usuari pot usar dins d'una partició NTFS. Per activar-les, obrim l'Explorador de Windows, clic dret sobre la unitat Dades (E:) i seleccionem Propietats.

<img width="1083" height="729" alt="imatge" src="https://github.com/user-attachments/assets/0a39bcd5-bc75-43b9-b777-ffc84f17562f" />

A la finestra de propietats ens dirigim a la pestanya Cuota i fem clic a Mostrar configuració de cuota.

<img width="361" height="208" alt="imatge" src="https://github.com/user-attachments/assets/01e421dc-0af3-4a94-b3c4-b4aa261f4ce9" />

### Pas 6 – Establir límit de 300 MB per usuari, amb notificació d'advertència

Dins del panell de configuració de quotes, activem les següents opcions.

<img width="362" height="447" alt="imatge" src="https://github.com/user-attachments/assets/4ba24cd0-2a3f-462c-8d74-3adbd48ee1d3" />

### Pas 7 – Crear dos usuaris locals: alumne1 i alumne2

Executem lusrmgr.msc per a gestionar usuaris locals 

<img width="396" height="207" alt="imatge" src="https://github.com/user-attachments/assets/4b082650-7812-455c-9ece-d2e4489b01b4" />

Dins fem clic dret sobre **usuaris** i **Usuari nou** 

<img width="349" height="224" alt="imatge" src="https://github.com/user-attachments/assets/d6982c1f-1afc-478a-935c-7cc2ca56a43a" />

Creem l'usuari alumne1 amb la contrasenya corresponent. Activem l'opció La contrasenya mai expira per evitar problemes en les proves.

<img width="419" height="384" alt="imatge" src="https://github.com/user-attachments/assets/a56b9852-cde5-4358-b663-e97b9141b6a4" />

De la mateixa manera, creem l'usuari alumne2 amb la mateixa configuració.

<img width="415" height="387" alt="imatge" src="https://github.com/user-attachments/assets/8e489803-ca49-45c0-b04d-94572cb3e141" />

### Pas 8 – Afegir-los a un grup nou anomenat Limitats

Dins de lusrmgr.msc, fem clic sobre la carpeta Grupos per veure tots els grups existents. Clic dret en un espai buit de la llista → "Grupo nuevo"

<img width="300" height="237" alt="imatge" src="https://github.com/user-attachments/assets/48a3504c-965c-44f6-9b03-9b6923a2f47e" />

Introduim el nom "Limitats" i afegim els usuaris creats i després només sera donar-li a crear i ja estarà.

<img width="417" height="389" alt="imatge" src="https://github.com/user-attachments/assets/d0a0a740-a698-4940-846f-5198ca01bc42" />

Veiem que estàn els dos usuaris creats al grup **Limitats**

<img width="441" height="465" alt="imatge" src="https://github.com/user-attachments/assets/5d5e06fb-3319-4fe2-b51c-fbe27121f629" />

### Pas 9 – Provar la còpia de fitxers a Dades per veure com actuen les quotes

Iniciem sessió amb alumne1 i començarem amb les proves

<img width="807" height="584" alt="imatge" src="https://github.com/user-attachments/assets/684ca971-1e60-4406-9966-664c140a6dc0" />

Per comprovar que les quotes funcionen correctament, iniciem sessió com a alumne1 i intentem crear fitxers de diverses mides a la partició E:\ amb la comanda fsutil file createnew:

<img width="740" height="482" alt="imatge" src="https://github.com/user-attachments/assets/20f86306-6646-46e8-bacc-25725494c672" />

# Fase 3 – Script de còpia i automatització

### Pas 10 – Afegir tercer disc virtual, formatar-lo en NTFS com a Backups

Des de la configuració de VirtualBox, afegim un tercer disc de 5 GB connectat al port SATA 3. Servirà com a unitat de còpies de seguretat.

<img width="875" height="538" alt="imatge" src="https://github.com/user-attachments/assets/4386ffad-bc2a-42d5-853f-d8b88a7395e8" />

Un cop dins de Windows, obrim la Gestió de discs i localitzem el nou **Disc 2 no asignat**. Clic dret → Nou volum simple.

<img width="830" height="640" alt="imatge" src="https://github.com/user-attachments/assets/c0ec5189-45ea-4510-ab3f-260137cf27c9" />

Formatem tot el disc com a NTFS i li posem l'etiqueta Backups. Assignem la lletra B:.

<img width="494" height="384" alt="imatge" src="https://github.com/user-attachments/assets/ccb862cb-d3c8-4220-9c42-56b8cac6987d" />

### Pas 11 – Crear carpeta CòpiesUsuaris dins Backups

Un cop creat i muntat el disc Backups (B:), creem manualment la carpeta CòpiesUsuaris dins de la unitat B:

<img width="628" height="357" alt="imatge" src="https://github.com/user-attachments/assets/8ad65f01-2cc0-4c1b-8c5b-2c4db6ef4d6c" />

### Pas 12 – Crear un script .bat que copiï C:\Users%USERNAME% a B:\CòpiesUsuaris%USERNAME%

Dins la carpeta B:\CopiesUsrs creem un script.bat que contingui el seguent:

<img width="654" height="265" alt="imatge" src="https://github.com/user-attachments/assets/555b5096-e144-4757-908e-cfdc4ec9b280" />

### Pas 13 – Obrir gpedit.msc → Configuració d'usuari → Scripts → Inici de sessió

Per assignar l'script per a que s'executi al iniciar sessió, hem d'obrir **gpedit.msc** amb Win+r.

<img width="394" height="205" alt="imatge" src="https://github.com/user-attachments/assets/7e740911-f6cc-4521-af95-e7c7a8b1cc10" />

Dins de l'editor, naveguem per l'arbre de directives:

Configuració d'usuari → Configuració de Windows → Scripts (inici de sessió o tancament de sessió)

<img width="733" height="339" alt="imatge" src="https://github.com/user-attachments/assets/374d5f93-f418-4c1b-86c9-25ca2e4e06d9" />

### Pas 14 – Assignar l'script perquè s'executi automàticament en iniciar sessió

A la finestra de propietats d'Iniciar sessió, fem clic a Agregar… i introduïm la ruta completa al nostre script (B:\CopuiesUsrs\script.bat)

<img width="377" height="193" alt="imatge" src="https://github.com/user-attachments/assets/abf12dfd-4a27-4da8-919b-2dfb9610e5a8" />



