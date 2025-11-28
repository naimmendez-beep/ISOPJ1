---
layout: default
title: "Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers"
---
<t>Sistemes de fitxers i particions</t>
## *Mida sector: el sector és la unitat mínima fisica del disc on es pot guardar les dades i per defecte son 512 Bytes
## *Mida blcok: és la unitat logica on es guarden les dades al 50, per defecte són 4096 bytes. Es pot cambiar la mida quena es formata el disc.
##  La mida del block o cluster i el sistema de fitxes pot ser diferent a cada partició del mateix disc.
## *Fragmentacio interna: es quan es desaprofita espai perque els blocs son massa grans per al que s'ha de guardar dins
## *Fragmentació externa: 
## *Tipus de formateig:
## -baix nivell: no es pot formatar a traves del SO, necessites els programes especials per formatar-los 
## -mig nivell: borra sistema de fitxers i marca sectors defectuosos, però no els intenta arreglar
## -alt nivell: només borra sistema de fitxers i si hi han sectors defectuosos els arregla
## *Gestió de particions
## -GPARTED
## -comandes
<p>Començarem amb les particions de disc, per poder emmagatzemar al mateix disc, però en diferents parts i organitzar-lo millor.
Hem de </p>

<img width="853" height="510" alt="imatge" src="https://github.com/user-attachments/assets/ac015f40-023f-44d2-bc51-8245525388b8"/>
<p>Utilitzem la comanda tune2fs amb el grep block per veure les diferents carpetes creades per al sda5</p>
<img width="851" height="125" alt="imatge" src="https://github.com/user-attachments/assets/45191349-7c16-44c5-a6cf-55feab66d291"/>
<p></p>
<img width="600" height="550" alt="imatge" src="https://github.com/user-attachments/assets/fe221678-32e0-42b4-82c9-70854e596d7b" />

<img width="845" height="599" alt="imatge" src="https://github.com/user-attachments/assets/86742c70-b3d8-42b7-9a9f-dfde9263b293" />

<img width="273" height="65" alt="imatge" src="https://github.com/user-attachments/assets/e7cad38c-2109-4d76-9aac-ca7b1d1dfa8c" />

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/659e0cb5-d12e-4e92-bdc1-98a00d2e9fb1" />

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/83513d93-9fdb-4cc9-a67e-2782cfe4940b" />

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/75fa46ee-0d08-45f4-b280-8e80efc4098f" />

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/f8f73cf0-57fe-44c2-9247-ccbf528c3eee" />

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/f7d8d7af-5bbc-4eb9-a4f5-18dc8653dc88" />

<img width="737" height="480" alt="imatge" src="https://github.com/user-attachments/assets/79e47249-fe51-43d2-919a-70aeab277814" />

<img width="738" height="481" alt="image" src="https://github.com/user-attachments/assets/55bc29a4-02c0-4109-8d9c-97e303d6b36e" />

<p>Podem treure els permisos per a certs usuaris i no deixar que entrin a certes carpetes, utilitzant setfacl i getfacl</p>
<img width="738" height="221" alt="image" src="https://github.com/user-attachments/assets/8e23274e-8825-4ff7-b0f8-d140d1c44083" />

<p>Veiem que no deixa entrar a la carpeta</p>
<img width="433" height="80" alt="image" src="https://github.com/user-attachments/assets/104ac7aa-485c-4806-ad3f-69febf2bb6dc" />

<p>Es pot donar o treure permisos, tant a directoris com a arxius</p>
<img width="546" height="438" alt="image" src="https://github.com/user-attachments/assets/0545fd02-0aba-4816-8ef8-651d935f88a8" />


*Gestió de processos
*Gestió d'usuaris i grups i permisos
*Còpies de seguretat i automatització de tasques
*Quotes d'usuari
