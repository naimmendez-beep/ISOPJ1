---
layout: default
title: 'Sprint 4: Configuració del Programari de Base i Sistemes d’Emmagatzematge en Ubuntu'
---

# Teoria RAID

### Què és un RAID?

**RAID** (*Redundant Array of Independent Disks*) és una tecnologia que combina múltiples discos durs físics en una sola unitat lògica amb l'objectiu de millorar el **rendiment**, la **disponibilitat** i/o la **redundància** de les dades. El sistema operatiu veu el conjunt de discos com si fos un únic dispositiu d'emmagatzematge.

### Beneficis principals del RAID

- **Tolerància a fallades:** Alguns nivells de RAID permeten que un o més discos deixin de funcionar sense perdre cap dada, gràcies a la redundància.
- **Major disponibilitat:** El sistema pot continuar funcionant fins i tot amb un disc defectuós, reduint el temps d'aturada (*downtime*).
- **Millora del rendiment:** Certs nivells distribueixen les lectures i/o escriptures entre varis discos simultàniament (*striping*), augmentant la velocitat de transferència.
- **Escalabilitat:** Es pot augmentar la capacitat o la protecció afegint discos al conjunt.
- **Cost-eficiència:** Permet obtenir alta disponibilitat amb discos econòmics en lloc d'invertir en costoses solucions de maquinari dedicat.

### Tipus de RAID més coneguts

| Nivell | Nom | Discos mínims | Descripció |
|--------|-----|---------------|------------|
| **RAID 0** | Striping | 2 | Distribueix les dades entre els discos en paral·lel. Ofereix el millor rendiment però **cap redundància**: si falla un disc, es perden totes les dades. |
| **RAID 1** | Mirroring | 2 | Fa una còpia exacta (*mirall*) de les dades en tots els discos. Si falla un disc, l'altre conté totes les dades íntegres. Penalitza la capacitat útil (50%). |
| **RAID 5** | Striping amb paritat distribuïda | 3 | Distribueix les dades i la informació de paritat entre tots els discos. Permet recuperar les dades si falla **1 disc**. Bon equilibri entre rendiment, capacitat i seguretat. |
| **RAID 6** | Striping amb doble paritat | 4 | Similar al RAID 5 però amb doble paritat. Permet la fallada simultània de **2 discos** sense perdre dades. |
| **RAID 10** | Mirroring + Striping | 4 | Combina RAID 1 i RAID 0: primer es creen miralls i després es fa striping entre ells. Alt rendiment i alta redundància, però menor capacitat útil (50%). |

### Combinacions possibles

- **RAID 0+1:** Primer striping i després mirroring. Menys comú perquè si falla un disc del grup de striping es perd tot el conjunt.
- **RAID 1+0 (RAID 10):** Primer mirroring i després striping. Més robust que RAID 0+1 davant fallades múltiples.
- **RAID 5+0 (RAID 50):** Agrupa múltiples conjunts RAID 5 i fa striping entre ells. Més rendiment que RAID 5 senzill.
- **RAID 6+0 (RAID 60):** Agrupa múltiples conjunts RAID 6 i fa striping. Màxima protecció i rendiment, però requereix molts discos.

### Què són els volums lògics (LVM)?

Els **volums lògics** (LVM, *Logical Volume Manager*) són una capa d'abstracció per sobre dels discos físics que permet gestionar l'espai d'emmagatzematge de forma molt més flexible que les particions tradicionals:

- **Volum físic (PV):** Cada disc o partició que s'incorpora a LVM.
- **Grup de volums (VG):** Conjunt d'un o més volums físics que formen un pool d'espai comú.
- **Volum lògic (LV):** Partició virtual creada dins d'un grup de volums. Es pot redimensionar en calent, fer snapshots, etc.

LVM es pot combinar amb RAID per obtenir el millor dels dos mons: redundància i flexibilitat en la gestió de l'espai.
