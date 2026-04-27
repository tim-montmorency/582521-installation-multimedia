# Raspberry PI AV Analogue 

## Sortie A/V analogique du Raspberry Pi → Téléviseur composite

### 🎯 Objectif

Utiliser la prise **jack 3,5 mm TRRS** du **Raspberry Pi 4 Model B** (idem B+, Pi 2, Pi 3) pour alimenter un **téléviseur analogique** via les entrées RCA composite.

---

## 1️⃣ Brochage électrique de la prise A/V

La prise combine **audio stéréo + vidéo composite** :

| Contact TRRS       | Signal                 | Rôle          |
| ------------------ | ---------------------- | ------------- |
| **Tip (pointe)**   | Audio gauche           | Canal L       |
| **Ring 1**         | Audio droite           | Canal R       |
| **Ring 2**         | Masse (GND)            | Retour commun |
| **Sleeve (corps)** | Vidéo composite (CVBS) | Image TV      |

---

## 2️⃣ Câblage TRRS → RCA

```
          Raspberry Pi
          Jack TRRS 3,5 mm

 TIP     → RCA BLANC  (centre)  = Audio Gauche
 RING 1  → RCA ROUGE  (centre)  = Audio Droite
 RING 2  → Masse      (coquilles de tous les RCA)
 SLEEVE  → RCA JAUNE  (centre)  = Vidéo composite
```

✔ Les parties métalliques extérieures des prises RCA = **masse commune**.

---

## 3️⃣ Branchement au téléviseur

| Fiche RCA | Entrée TV | Signal     |
| --------- | --------- | ---------- |
| 🟡 Jaune  | VIDEO IN  | Image      |
| ⚪ Blanc   | AUDIO L   | Son gauche |
| 🔴 Rouge  | AUDIO R   | Son droit  |

Fonctionne comme un lecteur DVD, magnétoscope, etc.

---

## 4️⃣ ⚠️ Attention aux câbles TRRS

Les câbles TRRS ne sont **pas tous câblés pareil**.

Certains standards (caméscopes, anciens MP3, téléphones) placent la vidéo sur **Ring 1 ou Ring 2**.

Le Raspberry Pi utilise le standard **Apple / Pi** :

**Sleeve = Vidéo**
**Ring 2 = Masse**
**Ring 1 = Audio droit**
**Tip = Audio gauche**

👉 Si vous avez le son mais pas l’image → mauvais câble.

---

## 5️⃣ Activation de la sortie TV sur le Pi

Dans le fichier `/boot/config.txt` :

```
enable_tvout=1
sdtv_mode=0   # 0=NTSC, 2=PAL
```

---

## 6️⃣ Caractéristiques du signal

| Signal          | Niveau              |
| --------------- | ------------------- |
| Vidéo composite | 1 Vpp / 75 Ω        |
| Audio           | Niveau ligne stéréo |

---

### ✅ Résultat

Le Raspberry Pi peut directement piloter un téléviseur analogique via un simple câble **TRRS → 3 RCA** correctement câblé.


<!-- start-replace-subnav depth=1 -->
<!-- end-replace-subnav -->
