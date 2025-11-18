# T04: Serveis de directori. LDAP



1. Comprobar el nom de servidor i el domini de la xarxa


Primer com sempre, farem una actualització del sistema per que estigui tot correcte i actualitzat.

sudo apt update && sudo apt upgrade -y

![captura1](img/Capt1.png)

Seguidament, haurem de deixar les configuracions així per poder modificar el domini.

sudo nano /etc/hosts

![captura2](img/Capt2.png)

Llavors per comprovar que tenim configurat el servidor i el domini de la xarxa de forma correcte, haurem de fer el següent.

hostname

hostname -f

![captura3](img/Capt3.png)

I si volem modificar el nom del servidor haurem d'utilitzar la següent comanda.

sudo hostnamectl set-hostname server

![captura4](img/Capt4.png)

Si ja tenim configurats els adaptadors correctament (Adaptador1: Xarxa NAT o Adaptador pont i Adaptador2: host-only) podrem començar amb la instal·lació de l’eina OpenLDAP.

![captura5](img/Capt5.png)

2. Instal·lació del servei i les seves utilitats

Ara començarem amb la instal·lació del server LDAP on utilitzarem la següent comanda “sudo apt install slapd lapd ldap-utils -y”. 

![captura6](img/Capt6.png)

![captura7](img/Capt7.png)

Seguidament haurem de comprovar que el servei Slapd funciona correctament i esta actiu.

![captura8](img/Capt8.png)

Ara, comprovem que el directori s’ha creat correctament.

![captura9](img/Capt9.png)

En el cas que haguem configurat el nom del domini d’instal·lar el servei haurem de reconfigurar-lo amb les preferències del document.

![captura10](img/Capt10.png)

![captura11](img/Capt11.png)

![captura12](img/Capt12.png)

![captura13](img/Capt13.png)

![captura14](img/Capt14.png)

![captura15](img/Capt15.png)

![captura16](img/Capt16.png)

Tornem a revisar els canvis que hem fet a l’eina. (sudo slapcat)

![captura17](img/Capt17.png)

3. Tasques d’implementació i configuració del servidor LDAP

El client, ens demana crear dos UnitatsOrganitzatives, llavors, ara crearem amb extensió “.ldif”: sudo nano OU_users.ldif
I seguidament, haurem d’introduir el següent contingut:

![captura18](img/Capt18.png)

Tot seguit, haurem d’introduir el seguent directori 
ldapadd -D “cn=admin,dc=innovatech14,dc=test” -W -f OU_users.ldif

![captura19](img/Capt19.png)

Seguidament, haurem de revisar que la OUs s’han creat correctament en el directori.
ldapsearch -x -LLL -b “dc=innovatech14,dc=test” ou

![captura20](img/Capt20.png)

Ara, en el cas que haguessim d’eliminar un OU, hauriem de executar la següent comanda:

ldapdelete -D “cn=admin,dc=innovatech14,dc=test” -W “ou=groups,dc=innovatech14,dc=test

![captura21](img/Capt21.png)

4. Implementació del gestor d’usuaris de LDAP  LAM

Tot seguit, haurem d’instal·lar el gestor LDAP LAM.
Primer de tot haurem d’actualitzar el sistema amb:
sudo apt upgrade && apt update

![captura22](img/Capt22.png)

I després farem per la instal·lació:
sudo apt install ldap-account-manager -y

![captura23](img/Capt23.png)

5. Gestió i Administració (LAM)

Per gestionar i administrar el (LAM) entrarem al gestor gràfic des de la màquina física amb l’url:
http://192.168.56.103/lam/templates/login.php

![captura24](img/Capt24.png)

Ara anirem a la part que diu “editar perfiles de servidor”.

![captura25](img/Capt25.png)

Seguidament, de contrasenya posarem “lam” que es la que ve per defecte, per així, poder cambiarla.

![captura26](img/Capt26.png)

Ara configurarem el idioma, compte i admin:

![captura27](img/Capt27.png)

![captura28](img/Capt28.png)

![captura29](img/Capt29.png)

Seguidament, a la pestanya “Tipos de cuentas” configurem els OUs per els nostres usuaris i grups:

![captura30](img/Capt30.png)

I ara farem clic a “guardar”.

La primera vegada ens demana si les volem crear al perfil del servidor LAM, les creem.

![captura31](img/Capt31.png)

En el següent apartat, crearem dos grups de seguretat al directori “tech i manager”.

![captura32](img/Capt32.png)

![captura33](img/Capt33.png)

![captura34](img/Capt34.png)

Després haurem de crear dos usuaris; tech01 i manager01, a part asignar cada usuari al seu grup.

![captura35](img/Capt35.png)

I assignarem cada usuari al seu grup.

![captura36](img/Capt36.png)

![captura37](img/Capt37.png)

Finalment haurem configurat i administrat el LAM (gestor d’usuaris LDAP) amb l’eina gràfica.

6. Integració de Client (Client Ubuntu Desktop)
   
Ens caldrà treballar des d’un client amb Zorin o Ubuntu. Si no en disposem d’un, haurem de crear una màquina virtual amb aquest sistema operatiu. En aquesta màquina, caldrà configurar l’adaptador de xarxa en mode NAT, igual que al servidor, per tal que ambdues màquines puguin comunicar-se.
Si la configuració és correcta, hauríem de poder fer un ping entre les dues màquines i obtenir resposta.

![captura38](img/Capt38.png)

Tot seguit, configurarem el hostname i asignarem un nom a l’ip del nostre servidor modificant l’arxiu /etc/hosts amb sudo nano /etc/hosts i el deixarem tal que així.

![captura39](img/Capt39.png)

Ara si fem ping al nom del servidor hauriem de fer ping a l’ip pero de forma “traduïda”.

ping server.innovatech24.test

![captura40](img/Capt40.png)

Per veure el hostname haurem d'utilitzar la següent comanda:

hostname -f

![captura41](img/Capt41.png)

7. Instal·lació per gestionar ldap i els seus usuaris

Ara instal·larem els paquets per gestionar ldap i els seus usuaris

sudo apt install libnss-ldapd libpam-ldapd nslcd -y

![captura42](img/Capt42.png)

![captura43](img/Capt43.png)

![captura44](img/Capt44.png)

![captura45](img/Capt45.png)

![captura46](img/Capt46.png)

Un cop instal·lat correctament podem verificar que ho hem fet bé i que detecta la configuració de ldap amb aquesta comanda:

![captura47](img/Capt47.png)

Seguidament haurem de modificar les extensions següents:

Primer de tot haurem de modificar l’extensió /etc/nsswitch.conf amb ldap en passwd, group. sudo nano /etc/nsswitch.conf.

![captura48](img/Capt48.png)

Ara, modificarem /etc/pam.d/common-password i comentar la línea marcada  sudo nano /etc/pam.d/common-password

![captura49](img/Capt49.png)

Seguidament, haurem d’ edita /etc/pam.d/common-session i afegir la següent linea: “session optional pam_mkhomedir.so skel=/etc/skel umask =077”

![captura50](img/Capt50.png)

Finalment, l’última extensió que haurem de modificar és
/etc/pam.d/gdm-launch-environment per activar l’autenticació LDAP. 

![captura51](img/Capt51.png)

Ara per finalitzar, haurem d’agafar els usuaris de ldap amb la comanda següent:
getent passwd | tail

![captura52](img/Capt52.png)

Si els canvis anteriors han funcionat correctament, ja podem reiniciar la màquina i iniciar sessió amb un dels usuaris.

Ara entrem a la màquina del client amb uns dels dos usuaris que hagim creat, en aquest cas entrarem amb l'usuari “tech01”.

![captura53](img/Capt53.png)

Un cop iniciat sessió podrem veure que l’usuari té el grup que hem assignat anteriorment i que s’han creat correctament els seus directoris.

![captura54](img/Capt54.png)

Ara ja podem accedir als diferents usuaris gestionats que hem creat a l’LDAP des de la o les nostres màquines.








