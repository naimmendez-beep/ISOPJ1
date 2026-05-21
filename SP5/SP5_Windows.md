---
layout: custom
title: "Sprint 5: Monitoratge, Auditories i Programari Client/Servidor"
---

# Monitorització del Sistema
### CPU (Processador)

- Què mostra:

    Tots els processos actius i el percentatge de CPU que consumeixen.

    Subprocessos i serveis associats a cada procés.

    Estadístiques com el temps de CPU, el nombre de fils o l'ID de procés (PID).

- Explicació dels conceptes:

    CPU (%): Indica quina proporció del processador utilitza cada procés. Si un procés consumeix més del 80-90% durant molt de temps, pot indicar una sobrecàrrega o un error de programari.

    PID (Process ID): Un número únic que permet identificar un procés en altres eines com el Visor d'esdeveniments o PowerShell.

    Nom del procés: Útil per identificar aplicacions conegudes (Chrome, Word) o sospitoses (per exemple, un "svchost.exe" amb un comportament inusual).

### Memòria (RAM)

- Què mostra:

    Quantitat de memòria utilitzada per cada procés.

    Estat de la memòria física: lliure, en ús, en espera, etc.

    Mida del fitxer de paginació (swap) i errors d'accés a la memòria.

- Explicació dels conceptes:

    Memòria en ús: La memòria que realment està utilitzant un procés en aquell moment.

    Memòria en espera: Dades que Windows manté preparades perquè puguin ser reutilitzades ràpidament si cal.

    Memòria disponible: És la suma de la memòria lliure i la memòria en espera.

    Memòria virtual: Combina la RAM física amb el fitxer de paginació al disc. Si s'utilitza gairebé tota, sol indicar una falta de RAM física.

### Disc

- Què mostra:

    Processos que accedeixen a la unitat d'emmagatzematge (lectura/escriptura).

    Bytes llegits o escrits per segon.

    Temps de resposta i latència dels discs.

    Fitxers concrets que s'estan utilitzant.

- Explicació dels conceptes:

    Lectura/escriptura (B/s): Indica si hi ha processos movent molta informació al disc.

    Temps de resposta (ms): El temps que triga el disc a respondre a una petició. Si supera els 20-30 ms de manera constant, el rendiment del sistema es veurà afectat.

    Cua de disc: Si és molt alta, significa que el disc no pot processar totes les peticions a temps i el sistema s'alentirà.

### Xarxa

- Què mostra:

    Aplicacions que estan enviant o rebent dades per internet o la xarxa local.

    Ports de comunicació i adreces IP remotes.

    Nombre de bytes per segon (Tx - transmissió i Rx - recepció).

- Explicació dels conceptes:

    Utilització de xarxa (%): Mesura la càrrega de la teva connexió.

    Ports locals/remots: Permet veure si una aplicació fa servir el port 80 (HTTP), 443 (HTTPS), 21 (FTP), etc.

    IP remota: Permet identificar amb quin servidor o destinació s'està comunicant l'aplicació.

    Connexions actives: Molt útil per detectar connexions sospitoses o aplicacions que consumeixen amplada de banda en segon pla.

# Part Pràctica

**Per accedir a aquestes dades en un entorn Windows, tens dues eines principals:**

- Administrador de tasques:

        Prem la combinació Ctrl + Shift + Esc.
<img width="661" height="590" alt="imatge" src="https://github.com/user-attachments/assets/75327b14-93df-4e38-a499-a288a2d96c73" />

        Aquí veuràs el consum de recursos de tots els serveis i aplicacions, fins i tot dividit per usuaris. És ideal per a una ullada ràpida o per "matar" processos que no responen.

<img width="661" height="590" alt="imatge" src="https://github.com/user-attachments/assets/df1b18fd-1530-4fea-a0fa-9f6ac8a1a445" />

<img width="661" height="590" alt="imatge" src="https://github.com/user-attachments/assets/65ef0bf0-8637-427b-ab3a-df8c98c5ed70" />

<img width="943" height="314" alt="imatge" src="https://github.com/user-attachments/assets/7ac58205-7fa9-4261-b741-bc0ff5351c11" />

<img width="430" height="337" alt="imatge" src="https://github.com/user-attachments/assets/ab0f8d13-7c55-42d7-a678-8a8e25a6c29b" />

- Monitor de recursos:

       Pots obrir-lo des de la pestanya "Rendiment" de l'Administrador de tasques o cercant-lo directament al menú d'inici.

       Aquesta eina és molt més detallada i permet analitzar a fons què està fent cada servei o aplicació amb el maquinari del teu dispositiu.

<img width="941" height="665" alt="imatge" src="https://github.com/user-attachments/assets/3c62ccd1-a85a-4a50-8831-cb54e8721d39" />

<img width="941" height="775" alt="imatge" src="https://github.com/user-attachments/assets/4b1c0e73-1a16-4665-bedd-e9018920780f" />

<img width="941" height="584" alt="imatge" src="https://github.com/user-attachments/assets/68ab45d9-8169-45a8-b0ae-b62b146416ff" />

<img width="941" height="524" alt="imatge" src="https://github.com/user-attachments/assets/583123e1-f3fe-4d81-88c1-30a68e772e94" />

<img width="941" height="663" alt="imatge" src="https://github.com/user-attachments/assets/d5141b1d-a6ea-42a1-964c-b8a56e18a2b8" />

<img width="941" height="772" alt="imatge" src="https://github.com/user-attachments/assets/098526a0-d87a-4d36-b3c3-99b93c22a96b" />

# Auditories 

### Auditories: què són i per a què serveixen
- Les auditories són com un sistema de control que et permet saber què passa dins del teu Windows Server. Serveixen per registrar coses com qui ha intentat entrar al sistema, qui ha accedit a una carpeta, qui ha modicat un txer, etc. És molt útil si vols tenir un control de seguretat i saber si algú fa coses rares o no autoritzades.

- Amb les auditories pots saber, per exemple, si algú ha intentat entrar amb un usuari que no li tocava, o si ha volgut esborrar un
arxiu important. També t’ajuden a veure si tot funciona bé o si cal canviar alguna conguració.
- Per activar les auditories a Windows, s’ha d’obrir secpol.msc i escollir què es vol controlar, com inici de sessió o accés a txers. Després, cal anar a les propietats del txer o carpeta, a “Seguretat” i afegir l’usuari que volem auditar i què volem registrar.
Els resultats es poden veure al visor d’esdeveniments (eventvwr.msc), on apareixen amb codis com el 4624 (entrada correcta) o 4625 (fallida). És important no activar massa auditories perquè poden fer el sistema més lent.

### Part pràctica

- El primer que hem de fer és buscar Directiva de seguretat

<img width="796" height="327" alt="imatge" src="https://github.com/user-attachments/assets/480dd751-a34b-4800-9ec9-c75d8134e303" />

- Fem click dret i premem "propiedades", marquem les dues caselles 'Correcto' 'Erróneo'.

<img width="420" height="507" alt="imatge" src="https://github.com/user-attachments/assets/041bf87b-dab2-4511-ba00-2550b3729585" />

- Un cop acceptat anem a 'visor de eventos' i apareixerà el **ID** **4624** que és d'inici de sessió

<img width="1006" height="885" alt="imatge" src="https://github.com/user-attachments/assets/24a4b2e7-f0ca-4855-a2d2-d1dbcd55cd18" />

- Després creem una carpeta per a configurar l'auditoria, entrem a les propietats de la carpeta, opcions avançades i agreguem l'entitat.

<img width="916" height="592" alt="imatge" src="https://github.com/user-attachments/assets/ad3f5e3f-1d0d-4a64-a49d-b9a37058e689" />

quedaria així

<img width="721" height="234" alt="imatge" src="https://github.com/user-attachments/assets/391d6667-267a-4ff0-8d4a-64fd562afdad" />

- Compartim la carpeta amb l'usuari

<img width="618" height="444" alt="imatge" src="https://github.com/user-attachments/assets/9a2887c6-e950-40a9-a6ce-3226d7159b4e" />

- També afegirem l'usuari Administrador i li donarem control total, per fer diferents proves

<img width="920" height="592" alt="imatge" src="https://github.com/user-attachments/assets/06491873-2716-4a98-86fb-bff9076573bb" />

- Si creem carpetes o arxius, dins del Visor d'esdeveniments sortirà l'ID de l'event 5379, que indica que s'han creat objectes i algun usuari els ha llegit

<img width="786" height="292" alt="imatge" src="https://github.com/user-attachments/assets/cd0256f4-1a0e-41c9-8eae-35cf1ae24db1" />

<img width="947" height="699" alt="imatge" src="https://github.com/user-attachments/assets/617211a5-b522-49a8-8ac6-60d24c9d88e3" />

- Activarem l'auditoria de seguiment de processos per comprovar que al obrir un programa generarà un event ID 4688, que indica que s'ha iniciat un procés.

<img width="944" height="752" alt="imatge" src="https://github.com/user-attachments/assets/e8bb8b21-5d6f-4004-89af-890c9ee4d660" />

- I el 4689 indica que el procés ha acabat

<img width="913" height="690" alt="imatge" src="https://github.com/user-attachments/assets/c5533bb2-cea0-4f33-8d01-3f833fc38504" />

- Activarem també l'auditoria per a l'administració de comptes, que generarà els codis 4720 que es de que un usuari s'ha creat i el 4722 que s'ha activat l'usuari

<img width="772" height="340" alt="imatge" src="https://github.com/user-attachments/assets/238ea6d5-956e-467a-a8a3-67463157015a" />

<img width="751" height="531" alt="imatge" src="https://github.com/user-attachments/assets/24f060e0-11f9-4829-b3e1-4b0687fd2cbf" />

<img width="868" height="707" alt="imatge" src="https://github.com/user-attachments/assets/996598fb-0e4b-4ccc-ae25-6ba786f7e9fa" />

<img width="939" height="750" alt="imatge" src="https://github.com/user-attachments/assets/868dea13-a65b-4d17-91ca-7bda9a55b560" />

- Si deshabilitem l'usuari sortirà el codi 4725

<img width="939" height="731" alt="imatge" src="https://github.com/user-attachments/assets/7e6a09f4-ce12-4398-8536-ce56afbcb9ed" />

- Però si l'eliminem sortirà el 4726

<img width="463" height="166" alt="imatge" src="https://github.com/user-attachments/assets/84e5c6ac-8856-4fc3-9e7d-ec27f48a5b9c" />

<img width="914" height="720" alt="imatge" src="https://github.com/user-attachments/assets/cd0e371c-95ec-4788-9542-565a0da88193" />
