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

