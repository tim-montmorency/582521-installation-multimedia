<!-- %: BLOC1_SAVOIR4  -->
# Emploi de protocoles pour transporter la vidéo en temps réel
<!-- %; -->

<!-- start-replace-subnav -->

<!-- end-replace-subnav -->


## 1) Grand public / usage courant

### HDMI

* **Câble / connecteur** : HDMI Type-A (cuivre).
* **Portée passive typique** : 5–10 m (jusqu’à \~15 m avec très bon câble).
* **Au-delà** : répéteurs ou **AOC HDMI** (fibre active) → 30–100 m.
* **Remarques** : sensible à la qualité; 4K60 4:4:4 exige des câbles haut débit.

### DisplayPort

* **Câble / connecteur** : DP 20 broches (cuivre).
* **Portée passive typique** : 2–3 m (peut monter à 5 m selon débit).
* **Au-delà** : **AOC DP** (fibre active) → 30–100 m.
* **Remarques** : très répandu côté PC/médiserveurs.

### (Héritage) DVI / VGA 

* **DVI-D** : \~5 m à 1920×1200 (10–15 m avec booster/AOC).
* **VGA** (analogique) : 7–15 m “propres” max en haute résolution; à éviter pour du mapping exigeant.

---

## 2) Semi-pro : transport cuivre longueurs modestes

### HDBaseT (transport HDMI sur paires torsadées)

* **Câble / connecteur** : Cat 5e/6/6a (RJ45).
* **Portée** : 100 m par segment.
* **Caractéristiques** : vidéo (jusqu’à 4K selon version), réseau/IR/RS-232, parfois alimentation (PoH).
* **Usage typique** : relier une régie à un projecteur éloigné sans passer à la fibre.

---

## 3) Broadcast / Pro point-à-point

### SDI (HD-SDI / 3G / 6G / 12G)

* **Câble / connecteur** : coaxial 75 Ω (RG-6/Belden), BNC.
* **Portées usuelles** (ordre de grandeur, câble premium + bons drivers) :

  * **HD-SDI / 3G-SDI** : \~70–100 m
  * **6G-SDI** : \~70 m
  * **12G-SDI** : \~70–100 m (très dépendant du câble)
* **Atouts** : robustesse, re-clocking possible, standard pro pour longues lignes terrain→projecteur.

---

## 4) Fibre optique (très longues distances / immunité EMI)

### Extenders & AOC

* **AOC HDMI/DP** : câble “hybride” cuivre+fibre → 30–100 m plug-and-play.
* **Convertisseurs fibre** (HDMI↔fibre, SDI↔fibre) :

  * **Multimode** : quelques centaines de mètres.
  * **Monomode** : kilométrique (1–10 km+).
* **Connecteurs** : LC (courant), parfois ST/SC.
* **Atouts** : très longue portée, aucune interférence, idéal en environnement bruité (électricité, moteurs, DMX).

---

## 5) AV-over-IP (distribution, multiproj, synchronisation à grande échelle)

### NDI® / Dante AV (1 GbE)

* **Câble / connecteur** : Ethernet cuivre Cat 5e/6 (RJ45) → **100 m par segment**; fibre via SFP pour km+.
* **Atouts** : acheminement sur réseau existant, monitoring flexible; latence variable selon codec/profil (NDI HX plus compressé, NDI “full” plus gourmand).
* **Usage** : multi-écrans, retours, prévisualisations, certaines diffusions “soft-compressées”.

### SDVoE (10 GbE, pro AVoIP “quasi sans latence”)

* **Câble / connecteur** : Cat 6a cuivre → **100 m**, fibre (SFP+) → km+.
* **Atouts** : qualité “visually lossless”, latence très faible, switching/routage puissant pour grands dispositifs.

---

## Règles de pouce (projection architecturale)

* **≤ 15 m** : HDMI/DP cuivre de qualité; testez 4K60 en amont.
* **15–100 m** : **HDBaseT** (simple), ou **SDI** (pro, robuste).
* **> 100 m** ou environnement “bruité” : **fibre** (AOC ou convertisseurs HDMI/SDI↔fibre).
* **Multiproj / grandes façades** : **AV-over-IP** (SDVoE si budget/perfs, NDI/Dante AV si réseau 1 GbE existant), clock réseau soignée, switches adaptés.
* **Toujours** : vérifier résolution, fréquence (4K60 vs 4K30), sous-échantillonnage (4:4:4 vs 4:2:0), marge de qualité câble, et prévoir du **re-clocking**/des **répéteurs** si nécessaire.

---

## Mini-lexique câbles & connecteurs

* **HDMI Type-A** : grand public/pro (cuivre, AOC).
* **DisplayPort** : PC/médiserveurs (cuivre, AOC).
* **BNC 75 Ω** : SDI sur coax.
* **RJ45 (Cat x)** : HDBaseT / AV-over-IP.
* **LC (fibre)** : petits modules optiques (multimode/monomode).
