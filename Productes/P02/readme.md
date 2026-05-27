# 📦 P02: Repositori de GitHub

## 📝 Breu Descripció
Aquesta activitat té com a objectiu establir una estructura organitzativa potent, neta i uniforme per a la documentació del projecte utilitzant **GitHub**. Es busca centralitzar guies, documentacions, configuracions i lliuraments per garantir la màxima traçabilitat del treball realitzat.

---

## 📐 Criteris d'Organització i Uniformitat

Per mantenir un control professional de la documentació, s'apliquen de manera estricta els següents criteris d'estructura:

* **🗂️ Índex Centralitzat:** El fitxer `README.md` principal del projecte actua com a eix connector amb enllaços directes a totes les carpetes.
* **📂 Desglòs de Tasques:** Cada tasca es troba en una carpeta individualitzada (`tasca01`, `tasca02`, etc.) amb el seu propi `README.md` que conté l'enunciat, la descripció i l'enllaç a la solució.
* **📦 Lliurament de Productes:** Els productes finals segueixen la mateixa lògica, ordenats en carpetes estructurades (ex. `producte01`, `producte02`, etc.).

---

## 📂 Esquema de l'Estructura del Repositori

Així és com s'organitza visualment l'arbre de directoris d'aquest projecte:

```text
📁 el-teu-repositori-projecte
├── 📄 README.md               <-- Índex de presentació general del projecte
├── 📁 tasques
│   ├── 📁 tasca01
│   │   ├── 📄 README.md       <-- Enunciat i enllaç a la solució de la T01
│   │   └── 📄 solucio.ext
│   └── 📁 tasca02
│       └── 📄 README.md
└── 📁 productes
    ├── 📁 producte01 (P01)
    │   └── 📄 README.md       <-- Enunciat i enllaç al Kanban
    └── 📁 producte02 (P02)
        └── 📄 README.md       <-- Aquest document
