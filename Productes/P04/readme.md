# P04: Documentació servidor DNS

## 📘 Breu descripció

Molt benvinguts a la vostra nova tasca, consultors! 🚀

Com a membres de l’equip de sistemes d’EverPia, us heu enfrontat al repte de configurar un servidor de noms com a prova de concepte pel nostre client **Digicore**. Actualment, el resultat de la vostra feina es troba dins d’una màquina virtual.

L’objectiu principal és poder publicar aquestes configuracions a **GitHub**, assegurant així que qualsevol futura replicació del servidor es pugui realitzar de forma ràpida i eficient. D’aquesta manera, només caldrà descarregar els arxius de configuració al servidor Linux corresponent i reiniciar el servei per tenir el servidor completament operatiu. ⚡

---

# 🛠️ Fase 1: Preparació de la Connectivitat i Extracció dels Arxius

## 🔌 Pas 1.1: Configuració de la Interfície Host-Only

Per poder copiar fitxers de la màquina virtual Ubuntu Server a la màquina física (host), primer cal assegurar la connectivitat de xarxa.

### Tasques a realitzar:
- Afegir una **segona interfície de xarxa** a la configuració de la màquina virtual.
- Assignar-li el mode **Host-Only**.
- Configurar i activar la interfície.
- Verificar que hi ha connectivitat entre la màquina virtual i la màquina física.

✅ Un cop completat, les dues màquines podran comunicar-se correctament.

---

## 📂 Pas 1.2: Còpia Segura dels Fitxers amb SCP

Amb la connectivitat establerta, utilitzarem el protocol **SCP (Secure Copy Protocol)** per transferir els arxius de configuració.

SCP és segur i funciona a través del servei SSH.

### 📁 Arxius a copiar

```bash
/etc/bind/named.conf.options
/etc/bind/named.conf.local
/etc/bind/zones/
```

### 💻 Exemple d’ús de SCP

```bash
scp usuari@IP_SERVIDOR:/etc/bind/named.conf.options .
```

> ℹ️ El punt (`.`) al final de la comanda indica que l’arxiu es copiarà al directori actual de la màquina física.

---

# ☁️ Fase 2: Integració a GitHub

## 📄 Pas 2.1: Crear carpeta i arxiu README.md

El primer pas serà crear la carpeta:

```text
producte04
```

i dins d’aquesta, l’arxiu:

```text
README.md
```

### 📌 Important
La carpeta es pot crear automàticament des de GitHub indicant:

```text
producte04/README.md
```

### 📝 Contingut del README
L’arxiu ha d’incloure:
- El títol del producte.
- Una explicació clara del contingut.
- La finalitat de la configuració DNS.

---

## ⬆️ Pas 2.2: Pujar els arxius

Caldrà pujar tots els arxius de configuració al repositori GitHub.

### 📁 Estructura recomanada

```text
producte04/
│
├── README.md
├── named.conf.options
├── named.conf.local
└── zones/
    ├── db.exemple.com
    └── db.192
```

### ⚠️ Nota important
Abans de pujar els arxius de zones, cal crear la carpeta `zones`.

Es pot fer creant temporalment un arxiu:

```text
zones/esborrar
```

i després eliminar-lo quan els arxius definitius ja estiguin pujats.

---

# 🎯 Objectius específics de la tasca

L’objectiu principal és utilitzar **GitHub** per documentar configuracions de servidors DNS, valorant els avantatges de:

- 🔁 Replicació ràpida de configuracions.
- 🔒 Seguretat i control de versions.
- 📚 Documentació centralitzada.
- 👥 Treball col·laboratiu.
- ⚙️ Automatització i reutilització de configuracions.

---

# ✅ Resultat esperat

Al finalitzar la pràctica, disposareu d’un repositori GitHub completament funcional amb tota la configuració necessària per desplegar un servidor DNS de manera ràpida i eficient. 🚀
