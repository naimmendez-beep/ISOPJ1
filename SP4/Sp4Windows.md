---
layout: custom
title: "Sprint 4: Configuració del Programari de Base i Sistemes d’Emmagatzematge en Windows"
---

---
layout: default
title: "Sprint 4: Configuració del Programari de Base i Sistemes d’Emmagatzematge en Windows"
---

# Pas 1. Preparació de la màquina virtual

## 1. Afegir 3 discs addicionals mínim per fer el RAID 5 i iniciar la màquina virtual.

<img width="859" height="520" alt="image" src="https://github.com/user-attachments/assets/bc4cee41-46c9-4faf-b3b3-854ad3f07b17" />

A la configuració de la màquina virtual crearem 3 discos addicionals i els afegirem a la màquina en qüestió.

<img width="939" height="931" alt="image" src="https://github.com/user-attachments/assets/6272ca55-d90f-4dba-8605-228f368a44e6" />

I iniciem la màquina normalment.

---

# Pas 2. Inicialitzar i configurar els discs

## 1. Obre Disk Manager i inicialitzar discos.

<img width="318" height="567" alt="image" src="https://github.com/user-attachments/assets/16034331-1d0d-4aaa-acb1-9a9b29a1a7f6" />

Amb Win + X obrirem aquest desplegable i haurem de anar a _Administración de Discos_.

<img width="763" height="601" alt="image" src="https://github.com/user-attachments/assets/d0d0d0ac-9be5-4115-b9e0-69d0758701cb" />

Ens surtirà aquesta pantalla on se'ns demana d'inicialitzar els discos. Ens assegurem de tenir els 3 discos sel·lecionats i fem click sobre _Aceptar_. També hem de tenir en compte l'estil de partició.

<img width="755" height="802" alt="image" src="https://github.com/user-attachments/assets/4c5624b2-d214-4804-9a52-caad06dddab7" />

Un cop aceptem, veurem els 3 discos afegits sense assignar.

---

# Pas 3. Crear el RAID 5 des del Gestor de discs

## 1. Clica amb el botó dret sobre un dels nous discos i selecciona "New RAID-5 Volume"

<img width="659" height="299" alt="image" src="https://github.com/user-attachments/assets/840653f6-1b44-49b2-92f6-f33823845fdb" />

## 2. Afegeix els altres 2 discos a la configuració, assignar una lletra i formatar el volum.

<img width="503" height="417" alt="image" src="https://github.com/user-attachments/assets/172f26bd-60f1-48d5-9d66-5cba8e077465" />

Fem click a _Siguiente_.

<img width="495" height="400" alt="image" src="https://github.com/user-attachments/assets/4f223089-04cc-4521-ad6e-0f220a0c058b" />

En aquesta pantalla haurem de sel·leccionar els discos que volem afegir al RAID fins que tinguessim tots els que volem sel·lecionats.

<img width="497" height="404" alt="image" src="https://github.com/user-attachments/assets/d8859349-7fc6-47b7-8f1f-9f4f29f5ca58" />

Assignarem una lletra al RAID.

<img width="496" height="404" alt="image" src="https://github.com/user-attachments/assets/620bdd5b-e2cd-4fa9-a111-3734ee94fa73" />

Li donem format al volum i li podem un nom.

<img width="491" height="408" alt="image" src="https://github.com/user-attachments/assets/ef4a263b-5009-4f20-aa5b-6cdc796130b1" />

Finalitzem el assistent.

<img width="426" height="203" alt="image" src="https://github.com/user-attachments/assets/83e88fd2-912f-4b34-abbb-c78717499657" />

<img width="644" height="309" alt="image" src="https://github.com/user-attachments/assets/a0fc6086-2fda-4b61-a64c-e3e97296eb53" />

En aquesta pantalla diem que sí i esperem a que es completi el procés.

--- 

# Pas 4. Proves de funcionalitat

## 1. Copia arxius al volum E:\ (per exemple, una carpeta amb imatges o documents)

<img width="683" height="188" alt="image" src="https://github.com/user-attachments/assets/e3a2b146-11bf-41e3-b0d7-6e3903d86f84" />

Generem fitxers de prova al RAID.

## 2. Obre i comprova que els fitxers són accessibles

<img width="334" height="107" alt="image" src="https://github.com/user-attachments/assets/0974a5b2-4930-467e-92b7-6d9cb8dd8e28" />

---

# Pas 5. Simulació de fallada (treure un disc)

<img width="758" height="917" alt="image" src="https://github.com/user-attachments/assets/f99895c1-a308-4f39-8134-48df6044991e" />

Per simular una fallada tornem al Administrador de discos i fent click dret sobre el disc, el marcarem com sense connexió.

<img width="663" height="196" alt="image" src="https://github.com/user-attachments/assets/78636a2f-6bca-4f3b-a49a-df6e8dba6bd9" />

Tot i això veurem que continuem tenint accés als fitxers.

<img width="298" height="129" alt="image" src="https://github.com/user-attachments/assets/d30ca222-27c2-43c7-991e-f1ded34d93d3" />

I al seu contingut.

---

# Pas 6. Simulació de segona fallada

<img width="728" height="452" alt="image" src="https://github.com/user-attachments/assets/72b6890f-c1f4-432e-b0ee-e16699d45cc2" />

Ara si marquem un altre disc com _Offline_ veurem que el RAID sencer està amb error ja que RAID 5 només tolera una fallada.

<img width="820" height="449" alt="image" src="https://github.com/user-attachments/assets/4557a94f-51ed-4fc7-ac3a-9a0fd7d078e5" />

I veurem que hem perdut l'accés als fitxer emmatgatzemats.

---

# Pas 7. Recuperació

<img width="723" height="433" alt="image" src="https://github.com/user-attachments/assets/5026089a-1467-41b8-8eb1-43b2fa9ce683" />

Fent click dret sobre el disc que volem activar, al desplegable que ens surtirà fem click sobre _En línea_.

<img width="735" height="405" alt="image" src="https://github.com/user-attachments/assets/7f4f1b85-9d86-4e95-b90a-3287f223ddca" />

Ara veurem que tenim error de redundàcia, però podriem continuar accedint a la informació.

<img width="866" height="467" alt="image" src="https://github.com/user-attachments/assets/934ee75a-af53-4738-9ec4-fce9747cee25" />

Com podem veure, el volum ha aparegut.

<img width="766" height="198" alt="image" src="https://github.com/user-attachments/assets/870ad5d4-73cd-4dc9-b4de-598d0b84a481" />

I los arxius també.

---

# Pas 8. Conclusions i observacions

El **RAID 5** és una solució d’emmagatzematge que reparteix les dades i la paritat entre tots els discos. Això permet que el sistema pugui continuar funcionant encara que falli **un sol disc**, ja que la informació es pot reconstruir a partir de la paritat.

Tot i això, cal tenir clar que un RAID 5 **no substitueix una còpia de seguretat**. Serveix per donar redundància i millorar la disponibilitat del sistema, però si fallen dos discos al mateix temps, es poden perdre les dades.

En resum, RAID 5 és útil per protegir-se davant d’una fallada simple de disc, però sempre s’hauria de combinar amb un sistema de còpies de seguretat extern.
