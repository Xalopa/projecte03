# T03: Gestió flexible de discos (LVM i Espais d’emmagatzematge)

## 🧩 Breu descripció

Un cop superada la fase de formació, ja esteu preparats per afrontar el repte dels nostres clients.  
Com ja es va explicar, tenim un nou i important client: **el bufet d’advocats Garriga i Associats**, un dels més prestigiosos de la ciutat, que ha requerit els serveis de la nostra consultora.

Gestiona una gran quantitat d'informació legal sensible, per la qual cosa **la integritat, la disponibilitat (alta redundància)** i **la facilitat de gestió** del seu emmagatzematge són d'importància crítica.

![captura1](img/capt1.png)

La direcció de *Garriga i Associats* ha expressat la necessitat urgent de renovar els seus sistemes de servidors per garantir que la informació estigui protegida contra fallades de disc i que l'espai pugui ser ampliat sense interrupcions.

Com a tècnics d’**Everpia**, teniu l'encàrrec de **dissenyar i documentar les solucions d'emmagatzematge** que compleixin aquests requisits tant en entorns Linux com Windows. Aquest disseny permetrà presentar al client una proposta de solució.

---

## 🎯 Objectiu principal

Dissenyar i documentar **dues solucions d'emmagatzematge** (una per a servidors **Linux** i una altra per a **Windows**) que compleixin amb els principis de:

- Alta disponibilitat  
- Redundància  
- Escalabilitat  

⚙️ Com que ha de ser una prova de concepte, **no treballareu amb servidors**, sinó amb **màquines virtuals** de sistemes operatius clients per documentar els procediments.

---

## 🐧 1. Part Linux: LVM amb Zorin OS

S'ha d'utilitzar la distribució **Zorin OS** (o una alternativa Linux compatible) per demostrar la utilitat del **Logical Volume Manager (LVM)**.

### 🔧 Requisits de la Implementació i Demostració

#### **Configuració Inicial**
- Crear un **grup de volums (VG)** i un **volum lògic (LV)** utilitzant inicialment **dos discos de 10 GB** (simulats).  
- El volum ha d'estar **formatat i muntat automàticament** al sistema mitjançant l’edició de l’arxiu `/etc/fstab`.

#### **Alta Disponibilitat**
- Implementar la configuració d’un **mirall (lvm_mirror)** per protegir la informació davant la fallada d'un disc.

#### **Instantànies (snapshots)**
1. Afegir **dos discos de 10 GB** al grup de volums.  
2. Crear un volum **`lvm_dades`** amb el primer disc afegit, formatar-lo i muntar-lo.  
3. Afegir arxius al volum (poden ser imatges d’Internet).  
4. Usar el segon disc per crear un **snapshot (`lv_snapshot`)** i documentar com es pot **restaurar** si la informació original es danya.

#### **Escalabilitat**
- Demostrar el **procés d'ampliació** utilitzant l’espai lliure dins el grup de volums per **ampliar el volum `lv_dades`**.

---

## 🪟 2. Part Windows: Espais d'Emmagatzematge (Storage Spaces)

S'ha d'utilitzar **Windows 11** per demostrar les configuracions possibles mitjançant els **Espais d'Emmagatzematge (Storage Spaces)**.

### 🔧 Requisits de la Implementació i Demostració

#### **Configuració inicial**
- Crear un **Storage Pool** amb **tres discos de 10 GB** (simulats).

#### **Estudi de Configuracions**
1. **Resiliència de Mirall (Mirroring):**  
   - Utilitzar dos dels discos.  
   - Comprovar que ofereix **alta disponibilitat**.  

2. **Resiliència de Paritat (Parity):**  
   - Explicar la seva **eficiència d'espai** en comparació amb el mirall.  
   - Cal utilitzar **els tres discos**.

3. **Resiliència de Mirall Triple:**  
   - Afegir tants discos de 10 GB com siguin necessaris.

#### **Demostració de la Gestió**
- Mostrar com es visualitza **l'estat dels discos i del pool** des de la consola de gestió de Windows, simulant la **facilitat de manteniment**.

---

## 👩‍💻 Com treballareu i què lliurareu?

- El treball serà **en grup**.
- Us dividireu en **dos equips**:
  - Un per la gestió amb **LVM (Linux)**
  - Un per la gestió amb **Espais d'Emmagatzematge (Windows)**

### 📄 Desenvolupament

1. Cada membre prepararà **el guió de la tasca** individualment:  
   - Cercar comandes  
   - Consultar documentació i enllaços  

2. Cada parella realitzarà **la seva part de la demostració**.  
3. El grup revisarà conjuntament **la documentació final**.  
4. Cada membre la **pujarà al seu repositori personal**.

---

## 📁 Entrega

- La documentació dels dos casos s’ha de fer en **format Markdown**, incloent:
  - Imatges
  - Explicacions
- Tot dins una carpeta anomenada **`tasca03`** dins del projecte.

L’arxiu principal **`README.md`** de la carpeta ha de contenir:
- La **descripció de la tasca**
- Els **enllaços** per accedir als dos documents (Linux i Windows)

> 🧠 La nota és conjunta al grup, així que organitzeu-vos bé i manteniu una bona comunicació interna.

---

## 🎤 Presentació final

Posteriorment haureu de **presentar al client** les conclusions de la vostra feina en una **presentació conjunta**.

---

## 📚 Material de classe (disponible al Moodle)

- **LVM Linux**  
- **Espais d’emmagatzematge (Windows)**

