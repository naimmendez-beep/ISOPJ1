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




















