<!-- %: BLOC1_SAVOIR6  -->
# Contrôle de la qualité du produit multimédia
<!-- %; -->

<!-- start-replace-subnav -->

<!-- end-replace-subnav -->



## 0) Outils utiles

Mètre laser, niveau à bulle, laser d’alignement, pieds/rigging certifiés, multiprise/UPS, luxmètre, ordinateur avec **mires** (grille, zones, PLUGE, rampes), chiffons/air duster, gaffer.

---

## 1) Paramètres physiques (d’abord)

### 1.1 Relevé du site

* **Surface** : dimensions, planéité, texture, couleur (albédo), obstacles (fenêtres, reliefs).
* **Ambiant lumineux** : mesurez au **luxmètre** (projection éteinte). Plus l’ambiant est élevé, plus il faut de lumens/superficie.
* **Distances & axes** : distance possible projecteur→surface, hauteur, angle d’incidence, contraintes d’accroche/ventilation.

### 1.2 Taille d’image & distance (rapport de projection)

* Formule : **Rapport** = *Distance lentille → surface* **÷** *Largeur image souhaitée*.
  → Choisissez **l’optique** (zoom fixe/interchangeable) qui couvre ce rapport avec marge.
* **Astuce** : s’il manque de recul, optez pour une **optique courte focale** (short-throw) ; s’il y a trop de recul, **long-throw**.

### 1.3 Placement & géométrie (avant tout “électronique”)

* **Règle d’or** : la **ligne optique** doit viser **perpendiculairement** le **centre** de l’image.
* **Privilégier le *lens shift*** (vertical/horizontal) pour centrer l’image **sans keystone**.
* **Éviter le keystone** (correction trapézoïdale) sauf rattrapage minimal : il dégrade la netteté.
* **Focus** : faites-le sur une **grille fine** (croix/texte petit) au **milieu de l’image** puis vérifiez les **coins**.

### 1.4 Luminance & uniformité

* En salle sombre : viser **40–80 cd/m²** (indicatif). En extérieur nocturne : le ratio **projection / ambiant** doit être très **net** (>4–5×).
* **Uniformité** : vérifier que le centre et les coins ont une luminance comparable (pas de point chaud, ni vignettage).

### 1.5 Multiproj / stacking / soft-edge

* **Empilement (stack)** pour gagner en luminance : alignez **à la mire** (grille fine), tolérance d’erreur **≤ 0,5 px perçu**.
* **Soft-edge** (juxtaposition) : prévoyez **10–20 %** de recouvrement pour des blends propres.

### 1.6 Alimentation, thermique, sécurité

* **Lignes dédiées** et **UPS** pour le contrôle & serveurs.
* **Ventilation** : dégagement autour des prises d’air ; filtres propres.
* **Rigging** : élingues de sécurité, points d’ancrage certifiés, protection pluie/poussière en extérieur.

### 1.7 Câblage (règles simples)

* **≤ 10–15 m** : HDMI/DP cuivre de qualité.
* **Jusqu’à 100 m** : **HDBaseT** (Cat 6a) ou **SDI** (coax 75 Ω).
* **> 100 m / EMI** : **fibre** (HDMI/SDI/DP optique).
* Évitez les boucles de masse, séparez puissance/vidéo, utilisez des cordons testés.

---

## 2) Contrôle qualité (physique)

### 2.1 Mires essentielles (à projeter)

* **Grille/croix** : centrage, perpendicularité, géométrie.
* **PLUGE** : réglage du **noir** (les barres proches du noir doivent être distinguables).
* **Rampe** (gris) : détecter **banding**/postérisation.
* **Zones** (blanc/mi-teintes) : vérifier **contraste** et **uniformité**.
* **Texte fin** : vérifier **piqué** et **focus uniforme**.

### 2.2 Procédure express

1. Centrer & mettre au carré (lens shift) → **zéro keystone** si possible.
2. Focus au centre → valider aux **4 coins**.
3. Ajuster **luminance** (gain/iris) selon lieu ; vérifier uniformité.
4. En multiproj : aligner contours, puis **blends** (plumes régulières, pas de surbrillance).

---

## 3) Composantes logicielles (ensuite)

### 3.1 Chaîne vidéo (OS/GPU/player)

* **Résolution/fréquence** : sortir **natif** (ex. 1920×1200 @ 60 Hz) ; désactiver l’upscaling du player/OS.
* **Mode plein écran exclusif**, **V-Sync** activé sur le serveur média.
* **Énergie** (OS) : jamais de mise en veille/économies GPU pendant le show.

### 3.2 Formats de lecture

* **Codecs intra-image** (ProRes, DNxHR, HAP) et **CFR** strict (25/50 ou 30/60 fps).
* **10 bits** si possible (sinon dither léger).
* Audio : **48 kHz**, boucle **seamless** si nécessaire.

### 3.3 Mapping, warping & blending

* **Warp** : utilisez des **maillages** fins plutôt que des keystones extrêmes.
* **Blends** : plume douce, courbe adaptée au **gamma réel** (2.2–2.4) pour éviter les “coutures”.
* **Masques** : créez des **masques par projecteur** à la **vraie résolution** (pas de rescale live).

### 3.4 Couleur & niveaux (calibration)

* **Balance des blancs** (D65) et gamma **2.2–2.4**.
* Ajuster **brightness/contrast** à la mire **PLUGE** et zones blanches (éviter clipping).
* Harmoniser l’image **entre projecteurs** (gain/bias RVB, LUT si disponible).
* Viser un **ΔE inter-projos < 3** (idéal < 2) si vous avez une sonde.

### 3.5 Synchronisation & déclenchement

* Idéal : **genlock**/blackburst (vidéo) ou **PTP** (AV-over-IP).
* Départs : **LTC**, **OSC** ou timecode interne ; prévoir **pré-roll** noir (2–5 s) pour l’alignement.

### 3.6 Test de robustesse

* Lecture **boucle** 15–30 min : vérifier **dropped frames**, stabilité audio/vidéo.
* Test **réseau** si AV-over-IP : IGMP snooping, QoS, pertes/jitter.
* **Plan B** : média de secours (fichier local), câbles de rechange, checklists imprimées.

---

## 4) Checklists (à cocher)

### 4.1 Physique — avant allumage

* [ ] Distance et **rapport de projection** validés (optique OK)
* [ ] Fixations, sécurité, ventilation
* [ ] Câblage adapté (cuivre/HDBaseT/SDI/fibre) et propre

### 4.2 Physique — mise au point & géométrie

* [ ] Image **centrée** via **lens shift**, **sans keystone**
* [ ] Focus net centre + coins
* [ ] Uniformité lumineuse satisfaisante
* [ ] (Multi) Alignement & **soft-edge** propres

### 4.3 Logiciel — signal & lecture

* [ ] Sortie **natif** (résolution/Hz), V-Sync, plein écran
* [ ] Médias **All-Intra**, **CFR**, 10 bits/dither
* [ ] Mires passées (PLUGE, rampes, grilles) → niveaux OK
* [ ] Couleur harmonisée (D65, gamma 2.2–2.4)
* [ ] Synchro (genlock/PTP/LTC/OSC) et **pré-roll** testés
* [ ] Run de **stabilité** (≥15 min) : 0 drop, latence stable

---

## 5) Raccourcis “décision”

* **Manque de recul** → optique **short-throw** ; **trop de recul** → **long-throw**.
* **Image pas carrée** → corriger **placement** / **lens shift**, pas le keystone.
* **Contraste faible** → réduire lumière ambiante, augmenter lumens, ajuster niveaux (PLUGE).
* **“Couture” visible** (multi) → re-régler **blends** et harmoniser **gamma/niveaux**.
* **Saccades** → vérifier **CFR**, codecs **intra**, V-Sync, perf disque/GPU.

