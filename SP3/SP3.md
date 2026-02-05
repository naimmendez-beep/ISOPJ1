---
layout: default
title: 'Sprint 3: Administració de dominis i seguretat (20h)'
---

# Administració de dominis i seguretat

<img width="1280" height="720" alt="imatge" src="https://github.com/user-attachments/assets/bd85f89a-7920-463d-abc2-425d61ba7bdb" />

## Configuració previa
Començarem fent dos màquines virtuals, una de servidor i una de client.

<img width="1056" height="286" alt="imatge" src="https://github.com/user-attachments/assets/ef4f81f2-fae8-4ffe-a96c-0512b17f6c98" />

Primer hem de posar la xarxa adequada, que en aquest cas sera una xarxa NAT tant al server com al client.

<img width="877" height="536" alt="imatge" src="https://github.com/user-attachments/assets/8d66b1a4-e3d5-4a4c-9b78-57ef159530ae" />

Un cop hem configurat el tema de la xarxa a les dues màquines, iniciem el servidor i començem la seva configuració, que el primer que farem sera canviarli el nom. 

<img width="657" height="93" alt="imatge" src="https://github.com/user-attachments/assets/d2170465-594f-4eb3-960a-ef40d0f4d1e8" />

Canviarem la ip i el nom del servidor dins l'arxiu /etc/hosts

<img width="658" height="181" alt="imatge" src="https://github.com/user-attachments/assets/c401c036-877d-4e35-b77a-ceb6acb4865d" />

Utilitzem les comandes 'sudo apt update' i 'sudo apt install slapd ldap-utils', i un cop instal·lat el ldap demanarà que posem una contrasenya d'administrador de domini.

<img width="658" height="162" alt="imatge" src="https://github.com/user-attachments/assets/d7ba879d-de53-4990-8251-39d15ad00066" />

I per obtenir la info dels objectes, unitats, etc, utilitzem la comanda slapcat

<img width="656" height="283" alt="imatge" src="https://github.com/user-attachments/assets/b5495379-f44d-4d5b-b1ec-d5a6825d9da4" />

Fem un dpkg-reconfigure slapd per configurar el paquet i sortiran les opcions a configurar 
<img width="658" height="140" alt="imatge" src="https://github.com/user-attachments/assets/45566d01-31d1-40b4-8173-4301caee5a34" />

<img width="660" height="120" alt="imatge" src="https://github.com/user-attachments/assets/b96b289a-6f75-495d-9ac6-5908813c1608" />

<img width="656" height="148" alt="imatge" src="https://github.com/user-attachments/assets/148aabbc-a6b6-438b-a44e-a583844e318e" />

<img width="659" height="150" alt="imatge" src="https://github.com/user-attachments/assets/2a1172f0-da99-4997-a48a-03e0ac0ab44d" />

<img width="657" height="145" alt="imatge" src="https://github.com/user-attachments/assets/e8e11919-a334-48d6-97a0-b3c1d7f79547" />

<img width="660" height="103" alt="imatge" src="https://github.com/user-attachments/assets/d0eb5536-adc1-4802-95d6-2e79b8f1778f" />

Un cop configurat el paquet, hauria de retornar un missatge dient que la configuració s'ha dessat correctament

<img width="654" height="101" alt="imatge" src="https://github.com/user-attachments/assets/ebd88392-0c1e-4fd5-9f5a-f8e69b864d6b" />

Que fa realment? 
Quan l'executes, s'obre un assistent a la terminal que et permet definir els paràmetres crítics perquè el sistema es comuniqui amb el directori.

Posteriorment he modificat els arxius uo.ldif, usu.ldif, grup.ldif, base.ldif i primerqueres.ldif.

**"uo.ldif":**  <img width="288" height="108" alt="imatge" src="https://github.com/user-attachments/assets/a351e681-8a6a-4f57-8adc-68beb4b030c2"/>

**"usu.ldif:**  <img width="296" height="352" alt="imatge" src="https://github.com/user-attachments/assets/37baaf1f-1308-49c0-813a-148b7910c7eb"/>

**"grup.ldif":**  <img width="324" height="144" alt="imatge" src="https://github.com/user-attachments/assets/566e9adc-951b-4fe6-ac91-671f6f15ad4f"/>

**"base.ldif":**   <img width="956" height="466" alt="imatge" src="https://github.com/user-attachments/assets/e6cdc30d-52e0-419f-90e5-0a32b89c78e1"/>

**"primerqueres.ldif":**  <img width="331" height="272" alt="imatge" src="https://github.com/user-attachments/assets/5aeb1dc7-0cb0-4f02-988a-b5f3fd1c6714" />

Per veure tota la configuració realitzada fem un slapcat de nou 

<img width="515" height="789" alt="imatge" src="https://github.com/user-attachments/assets/517436da-cec4-4ec9-ac98-6e9346877713" />

## Configuració client

Primer canviarem el hostname amb la comanda adequada 

<img width="814" height="111" alt="imatge" src="https://github.com/user-attachments/assets/cd13d5ac-5a2d-4f26-9bef-6350f69eaa93" />

I utilitzarem la comanda apt install per descarregar els paquets libnss-ldap libpam-ldap nscd

<img width="773" height="71" alt="imatge" src="https://github.com/user-attachments/assets/a92feb2c-7e3b-4d8d-a65b-d40b337ab3f6" />

I podem fer un 'dpkg-reconfigure ldap-auth-config' per configurar el paquet, que gestiona la connexió entre el sistema operatiu i el servidor LDAP.

<img width="649" height="499" alt="imatge" src="https://github.com/user-attachments/assets/5311b981-0fd0-4807-86e0-7cbe088567d4" />
<img width="646" height="360" alt="imatge" src="https://github.com/user-attachments/assets/0a09f427-4002-4312-8a71-fc107141d56f" />
<img width="642" height="338" alt="imatge" src="https://github.com/user-attachments/assets/29ed8b68-a2b6-4786-9b58-3c818bf29e9b" />
<img width="641" height="353" alt="imatge" src="https://github.com/user-attachments/assets/e9fcc79d-d8f0-46d9-9ffb-d623e3fd86c3" />
<img width="640" height="373" alt="imatge" src="https://github.com/user-attachments/assets/dda84fab-d0a1-47f9-9fef-74672c538929" />
<img width="642" height="342" alt="imatge" src="https://github.com/user-attachments/assets/f6c9a321-7f5d-4e9e-9bd4-c1c1a620c88f" />
<img width="645" height="337" alt="imatge" src="https://github.com/user-attachments/assets/ce4c8555-bff3-4d61-a2cb-2466fc8a922f" />
<img width="639" height="333" alt="imatge" src="https://github.com/user-attachments/assets/3eaf79ab-65f5-41fe-9817-ef5c8fd3a8e5" />
<img width="645" height="357" alt="imatge" src="https://github.com/user-attachments/assets/0847f6e6-6b08-4e2a-85f7-c3838ca6a376" />
<img width="638" height="396" alt="imatge" src="https://github.com/user-attachments/assets/e7ba5164-8cbe-4016-bfbe-fb581963063e" />

Un cop feta la instal·lacio i configuració del paquet hem d'anar a l'arxiu /etc/nsswitch.conf i afegir 'ldap' per a que cerqui usuari, contrasenyes i grups.

<img width="657" height="503" alt="imatge" src="https://github.com/user-attachments/assets/3965578a-2dc3-4ac2-9095-2df8d36bdcd4" />

També hem de fer algunes configuracions dins de l'arxiu /etc/pam.d/common-session com
**- En el /etc/pam.d/common-password he eliminat el use_authtok.**
**- Afegit session optional pam_mkhomedir.so skel=/etc/skel umask=077 al final.**

<img width="655" height="501" alt="imatge" src="https://github.com/user-attachments/assets/37633db5-214e-4738-a3ab-97ba1db86083" />

I he configurat el fitxer de configuració de LightDM per permetre l'inici de sessió manual d'usuaris LDAP. Això és necessari perquè, per defecte, LightDM només mostra els usuaris locals i no permet introduir manualment un nom d'usuari. Afegint aquestes opcions:

<img width="656" height="502" alt="imatge" src="https://github.com/user-attachments/assets/fcc3816f-9436-4c77-939c-c2b3e1ab6acb" />
