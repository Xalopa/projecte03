# Part Linux: LVM amb Zorin OS

1. Configuració inicial
 
Com a configuració inicial i amb la màquina parada hem creat dos Discs Virtuals de 10GB cada un. Gràcies a això disposarem de un emmagatzematge més elevat.

![captura1](img/1.png)

![captura2](img/2.png)

Acte seguit, hem obert la màquina virtual i comprovar amb la següent comanda fdisk -l que la maquina hagi detectat els dos discos creats anteriorment.
Amb aquesta comanda, hem pogut verificar que el sistema detecta els 2 discos creats. Gràcies a això tindrem un bon emmagatzematge per a utilitzar la nostra màquina.

![captura3](img/3.png)

2. Configuració inicial d’un grup de volum (VG) i un volum logic (LV)

A continuació hem creat els volums físics amb la comanda sudo pvcreate. Tot i que per poder executar-la haurem de tenir instal·lada l’eina “lvm2”, per instal·lar-la executarem la comanda: sudo apt install lvm2

![captura4](img/4.png)

![captura5](img/5.png)

Ara crearem un grup de volums i els assignarem als dos discs, amb la comanda vgcreate

![captura6](img/6.png)

Posteriorment podem crear o eliminar volums
        - Afegir volums: vgextend [nom del vg] [disc] /// vgextend volgrup /dev/sdd
Amb la comanda vgdisplay podem veure els grups creats i les seves característiques.

![captura7](img/7.png)

Per crear un volum lògic l’haurem de crear indicant la mida, el VG i el nom amb el qual volem crear-lo.

lvcreate -L [Mida] -n [Nom del Volum Lògic] [Nom del Grup] /// lvcreate -L 200M -n lv01 volgrup

![captura8](img/8.png)

Cada volum lògic és com una partició del disc, per tant caldrà muntar-lo correctamente perquè sigui funcional, per això haurem de crear una carpeta per poder muntar el volum dins el sistema d’arxius de la màquina.

Primer, haurem de crear la carpeta on volem muntar-lo: mkdir /mnt/lv01
seguidament muntarem el volum a el sistema de fichers: mkfs.ext4 /dev/volgrup/lv01

![captura9](img/9.png)

Ara ja tindriem el volum “inicialitzat”, però per poder utilitzar-lo usarem la comanda mount, per muntar el volum a la carpeta que hem creat.

mount /dev/volgrup/lv01 /mnt/lv01/

Ara ja hauriem muntat el volum a la carpeta creada, però cada cop que iniciem la màquina s’hauria de tornar a “asignar” aquest volum a la carpeta, per fer-ho permanent haurem d’editar l’arxiu /etc/fstab → nano /etc/fstab

![captura10](img/10.png)

Els camps de la línia que hem utilitzat tenen el següent significat:

- /dev/volgrup/lv01: unitat que es vol muntar.
- /mnt/lv01: punt de muntatge
- ext4: per indicar el sistema de fitxers utilitzat.
- defaults: les opcions de muntatge per defecte. Aquí
es podria indicar si és només lectura, etc.
- dump: 0 per indicar que el sistema de fitxers no
s'hagi de bolcar. Avui dia és la conf. normal.
- pass: 0 per indicar que no es faran comprovacions
d'aquest volum a l'arrancar el sistema.

Si volem modificar el tamany d’un volum lògic (LV) usarem normalment aquestes dues comandes:
lvextend: només serveix per estendre el volum
lvreduce: permet reduir la mida
També podem usar la comanda lvresize

IMPORTANT, sempre que volguem modificar un LV, haurem de desmuntar-lo perque no estigui en ús.

3. Creació d’un mirall (lvm_mirror)

Ara crearem un snapshot o còpia del nostre LV, per fer-ho primer crearem alguns archius dins el nostre LV, ho farem amb la comanda touch:

touch /mnt/lv01/file01
touch /mnt/lv01/file02
touch /mnt/lv01/file03

![captura11](img/11.png)

Seguidament crearem la instantània (snapshot) amb la comanda lvcreate
lvcreate -L 100M -s -n copialv01 /dev/volgrup/lv01

![captura12](img/12.png)

En aquesta comanda usem -s per indicar que es un snapshot.

Per veure els LV que tenim creats i com la còpia apunta al original usarem la comanda:
lvs volgrup

![captura13](img/14.png)

Si volem veure el contingut que té aquesta còpia muntarem el LV per poder veure el contingut que té dins. Per fer-ho crearem una nova carpeta i seguidament muntarem el volum a aquesta

mkdir /mnt/copia
mount /dev/volgrup/copialv01 /mnt/copia

Ara podem veure el contingut que té dins amb la comanda ls /mnt/copia

![captura14](img/15.png)

Ara ja tindrem creada la snapshot.





