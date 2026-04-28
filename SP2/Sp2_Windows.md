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

# Fase 4 – Verificació i documentació

### Pas 15 – Comprovació: l'script fa la còpia a Backups

Iniciem sessió amb l'usuari alumne1. L'script s'executa automàticament a l'inici de sessió i copia el contingut de C:\Users\alumne1 a B:\CòpiesUsuaris\alumne1.

<img width="719" height="484" alt="imatge" src="https://github.com/user-attachments/assets/1045a671-76bd-41a2-b10f-98153e50ff82" />

# Fase 5 – Gestió de processos i serveis

### Pas 19 – Llistar processos actius

Iniciem sessió com a alumne1, obrim la consola (CMD) i executem tasklist per obtenir la llista de tots els processos actius, amb el seu PID, sessió i ús de memòria.

<img width="660" height="308" alt="imatge" src="https://github.com/user-attachments/assets/14882bae-1d38-4f66-ae4c-bc680d6c5622" />

Redirigim el tasklist cap a un fitxer de text per poder veure-la, veiem que s'ha redirigit be

<img width="548" height="450" alt="imatge" src="https://github.com/user-attachments/assets/2078a43b-ac93-4c7f-8154-87078f0bb68f" />

Comprovem alguns processos clau usant findstr per filtrar del fitxer guardat:

<img width="663" height="216" alt="imatge" src="https://github.com/user-attachments/assets/ae061e6e-2860-4ec5-963c-34320a3bbeab" />

### Pas 20 – Identificar processos prescindibles

### Busca processos no essencials per a l’usuari, com: OneDrive.exe, Teams.exe, SkypeApp.exe
**Fes una taula amb:**
- Nom del procés
- Memòria usada
- Justificació per eliminar-lo

<img width="635" height="72" alt="imatge" src="https://github.com/user-attachments/assets/56b83a2a-2586-4b39-b95a-ae29c03f164f" />


**Taula de processos prescindibles identificats:**

| Nom del procés | Memòria aprox. | Justificació per eliminar |
|----------------|----------------|---------------------------|
| `OneDrive.exe` | ~135 MB | Sincronització al núvol innecessària en un entorn de VM sense connexió a internet real |
| `Teams.exe` | ~150-400 MB | Client de videoconferència no necessari per a tasques d'aula |
| `SkypeApp.exe` | ~80-150 MB | Aplicació de comunicació no requerida en l'entorn de laboratori |

### Pas 21 – Eliminar processos manualment

Executem taskkill per finalitzar el procés d'OneDrive forçosament:

<img width="483" height="102" alt="imatge" src="https://github.com/user-attachments/assets/39b09178-a3d3-4821-93b4-041fa49793f5" />

### Pas 22 – Automatitzar-ho a l'inici de sessió

Modifiquem l'script que haviem creat (jo l'he modificat una mica més per a quan l'executi manualment surti informació)

<img width="518" height="245" alt="imatge" src="https://github.com/user-attachments/assets/8a21f4c8-eafe-4db1-a241-4ce51b555da7" />

Per fer la comprovació, haurem d'iniciar sessió amb alumne2 i comprovar que OneDrive no s'executa.

<img width="435" height="69" alt="imatge" src="https://github.com/user-attachments/assets/adb65180-503e-487f-9710-401db0cb32b4" />

### Pas 23 – Documentació: tasklist, anàlisi de processos crítics i rendiment

- Llistat de Processos (Tasklist)
Per generar el fitxer base, s'ha utilitzat la comanda `tasklist > tasklist.txt` des de la terminal de Windows.

#### Taula Justificativa de Processos Clau
A continuació, es justifiquen els processos més rellevants trobats en el sistema:

| Procés | Descripció | Justificació | Recomanació (Recursos Baixos) |
| :--- | :--- | :--- | :--- |
| `System` | Nucli del Sistema Operatiu | Essencial per al funcionament de l'equip. | No tocar mai. |
| `lsass.exe` | Local Security Authority | Gestiona la seguretat i l'inici de sessió. | Essencial. |
| `svchost.exe` | Service Host | Contenidor per a múltiples serveis de Windows. | Mantenir (optimitzar serveis). |
| `explorer.exe` | Explorador de Windows | Interfície gràfica (escriptori, barra de tasques). | Essencial per a l'usuari. |
| `OneDrive.exe` | Sincronització de núvol | Sincronitza fitxers amb Microsoft Cloud. | **Aturar** per estalviar RAM/Xarxa. |
| `msedge.exe` | Microsoft Edge | Navegador web de Windows. | **Tancar** si no s'està navegant. |
| `ctfmon.exe` | Processador d'entrada | Gestiona el teclat, veu i entrades alternatives. | Mantenir si s'usa teclat normal. |

- Prova de Control: Finalització de `explorer.exe`

**Procediment:**
S'ha executat la finalització del procés `explorer.exe` mitjançant el Gestor de Tasques o la comanda `taskkill /f /im explorer.exe`.

**Resultat observat:**
1.  **Desaparició de la interfície:** La barra de tasques, el menú d'inici i les icones de l'escriptori desapareixen immediatament.
2.  **Pantalla:** Si no hi ha altres finestres obertes, la pantalla queda d'un color sòlid (generalment negre o el color de fons).
3.  **Processos actius:** Altres aplicacions obertes (com un navegador o un terminal) continuen funcionant, ja que el nucli del sistema no ha caigut.

**Com recuperar-lo:**
Cal prémer `Ctrl + Alt + Supr`, obrir el *Gestor de Tasques*, anar a **Fitxer > Executar nova tasca** i escriure `explorer.exe`.

- Impacte en el Rendiment (MV i Recursos Baixos)

La gestió estricta de processos té un impacte crític en entorns amb recursos limitats (com Màquines Virtuals):

* **Alliberament de Memòria RAM:** Molts processos de "bloatware" o de telemetria consumeixen entre 20MB i 100MB cadascun. En una MV amb 2GB de RAM, aturar 5 processos innecessaris pot recuperar un 15-20% de la memòria disponible.
* **Reducció de l'ús de CPU:** Processos en segon pla (com actualitzadors automàtics) generen pics de CPU que provoquen "lag" en la màquina virtual.
* **Millora de l'I/O de Disc:** Especialment en discs mecànics o discs virtuals, reduir processos minimitza les lectures/escriptures constants, fent que el sistema respongui molt més ràpidament.

# Fase 6 – Gestió de permisos (ACLs)

## Què són les ACLs i com funcionen a Windows?

A Windows, cada fitxer i carpeta té una **Llista de Control d'Accés** (ACL, *Access Control List*). Aquesta llista és el mecanisme principal de seguretat que defineix qui pot fer què amb aquell recurs específic.



Cada entrada individual dins d'una ACL s'anomena **ACE** (*Access Control Entry*). Una ACE sempre indica dos aspectes fonamentals:
* **La identitat:** Quin usuari o grup específic està afectat per la regla.
* **Els permisos:** Quin nivell d'accés o denegació té (lectura, escriptura, execució, control total, etc.).

### Diferències amb els permisos de xarxa

Els permisos ACL són molt més detallats i granulats que els permisos "normals" de compartició en xarxa (Share permissions), perquè ofereixen les següents característiques:

- **Nivell de fitxer:** Permeten configurar permisos no només per a carpetes senceres, sinó per a fitxers específics dins d'aquestes.
- **Flexibilitat d'assignació:** S'apliquen de manera independent tant a usuaris individuals com a grups sencers.
- **Granularitat avançada:** Permeten combinacions molt precises, com per exemple "només lectura", "només esborrar", o "control total excepte canviar permisos".
- **Gestió per Herència:** Els permisos poden ser heretats automàticament d’una carpeta superior (directori pare) o assignats manualment trencant aquesta herència.

### Pas 24 – Crear la carpeta Projectes

Iniciem sessió amb l'usuari administrador i al disc **E:** creem la carpeta 'Projectes'

<img width="849" height="231" alt="imatge" src="https://github.com/user-attachments/assets/4c2ec73f-5323-48eb-a581-876f6494c768" />

### Pas 25 – Assignar permisos normals al grup Limitats

Fem clic dret sobre la carpeta, propietats i seguretat i veurem que els permisos actuals són els següents:

<img width="361" height="481" alt="imatge" src="https://github.com/user-attachments/assets/aaf895c4-35ea-464e-ac32-07808ce8dd51" />

Cliquem a opcions avançades i desactivem l'opció d'herencia per poder gestionar els permisos.

<img width="765" height="519" alt="imatge" src="https://github.com/user-attachments/assets/b96e2148-c642-4607-82b9-bf138d862562" />

Agreguem i afegim com a entitat de seguretat el grup **Limitats**. 

<img width="917" height="593" alt="imatge" src="https://github.com/user-attachments/assets/3a8902b4-e944-41b0-a7c0-043132879bff" />

Aqui veiem la configuració final de les opcions avançades 

<img width="765" height="521" alt="imatge" src="https://github.com/user-attachments/assets/482d66cf-fc73-4169-bd1e-b970adef5d36" />

### Pas 26 – Comprovar accés amb alumne1

Iniciem sessio amb l'usuari **alumne1**

<img width="274" height="269" alt="imatge" src="https://github.com/user-attachments/assets/9df4ef8a-457f-43fd-8609-e9aec6cad07f" />

Comprovem que amb l'usuari **alumne1** (que pertany al grup **Limitats**) tenim permisos per crear arxius dins la carpeta.

<img width="755" height="202" alt="imatge" src="https://github.com/user-attachments/assets/06817078-f4a8-481d-a65a-72aa7a129762" />

I veiem que s'ha creat correctament

<img width="334" height="163" alt="imatge" src="https://github.com/user-attachments/assets/513af891-c1fd-4cd9-954c-5a5a309a71d5" />

### Pas 27 – Aplicar excepció per alumne2 (només lectura)

Tornem a iniciar sessió com a administrador i executem la comanda icacls per aplicar una excepció específica per a alumne2, com per exemple **icacls "E:\Projectes" /grant:r alumne2:(R)**.

Que el que fa aquesta comanda de Windows, serveix per donar permisos de lectura a un usuari específic sobre una carpeta, reemplaçant qualsevol altre permís explícit que tingués anteriorment.

<img width="562" height="105" alt="imatge" src="https://github.com/user-attachments/assets/b7813507-8e0f-4843-8de7-34ba6afed741" />

### Pas 28 – Comprovar l'excepció amb alumne2

Si iniciem sessio amb **alumne2** i accedim a E:\Projectes. La carpeta que habiem creat estarà buida.

<img width="272" height="264" alt="imatge" src="https://github.com/user-attachments/assets/9b18cef8-ccb4-486e-936d-7c23a2057402" />

La carpeta

<img width="579" height="308" alt="imatge" src="https://github.com/user-attachments/assets/9cffe4b2-0f07-4f54-9afe-dc3e56b3dd71" />

Tornem a iniciar sessió amb alumne1 i comprovem que si pot veure l'arxiu creat.

<img width="624" height="249" alt="imatge" src="https://github.com/user-attachments/assets/e19d57ea-d650-4feb-98e2-b472686ab105" />

Però si l'alumne2 intenta crear una carpeta sortira una alerta de que no te permisos i el sistema denegarà l'operació.

<img width="915" height="605" alt="imatge" src="https://github.com/user-attachments/assets/d68b7701-ebd5-41f1-a2a8-2ed6cfcdab51" />

### Pas 29 – Consultar els permisos aplicats amb icacls

Executem la comanda des de la consola com a administrador per veure l'estat final de tots els permisos de E:\Projectes

<img width="576" height="199" alt="imatge" src="https://github.com/user-attachments/assets/4327d4ba-c4b6-42fd-82b8-18741dbd7ce1" />
