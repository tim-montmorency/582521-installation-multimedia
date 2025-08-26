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

---

## Exemples rapides (terrain)

* **Un projecteur à 40 m de la régie** : HDBaseT sur Cat 6 **ou** SDI (avec convertisseurs HDMI↔SDI si besoin).
* **Trois projecteurs à 80–120 m** : SDI (12G si 4K60) **ou** fibre (HDMI/SDI↔fibre).
* **Façade complète avec 8–12 projos** : SDVoE (10 GbE) pour la matrice principale; NDI/Dante AV pour retours/monitoring; fibres entre baies/salles.


**1) IPMX (AIMS) — l’option ouverte la plus proche de SDVoE**

* **Ce que c’est** : un ensemble **ouvert** de spécifications basé sur **SMPTE ST 2110** (essences séparées), **AMWA NMOS** (découverte/contrôle), AES67, avec profils pour le Pro-AV (EDID/HDCP, etc.). ([ipmx.io][1])
* **Réseaux/latence** : fonctionne en **non compressé** (10/25 GbE) ou en **JPEG XS** (ST 2110-22) pour réduire le débit et garder une latence très faible; l’objectif est l’**interopérabilité multi-fournisseurs**. ([smpte.org][2], [AVNetwork][3])
* **Pourquoi pour la projection archi** : routing IP souple, synchro PTP, scénarios multiproj étendus — sans s’enfermer dans un écosystème propriétaire. ([smpte.org][2])

**2) SMPTE ST 2110 “pur” (broadcast)**

* **Ouvert, éprouvé** en TV; nécessite PTP, switches adaptés et débits élevés (souvent 10–25 GbE selon formats). Excellent pour la prod temps réel, mais plus exigeant à intégrer côté Pro-AV. ([smpte.org][2])

**3) RIST (VSF) — contribution fiable sur Internet**

* **Spécification ouverte** pour transporter des flux en **faible latence** sur réseaux non gérés (liaisons longue distance, backhaul). Moins fait pour remplacer une matrice locale “zero-latency” que pour les liens entre sites. ([RIST Forum][4], [static.vsf.tv][5])

**4) SRT — open-source (pas un standard ouvert)**

* Transport **open-source** pour la **faible latence** et la résilience (chiffrement, ARQ). Très utile en contribution/réplication, pas un équivalent de SDVoE pour un tissu 10 GbE “near-zero-latency”. ([GitHub][6], [haivision.github.io][7])

**5) AVB/TSN (IEEE 802.1) — compléments réseau ouverts**

* Famille **ouverte** (gPTP, QoS, réservation) donnant une **latence bornée** et de la synchro déterministe sur Ethernet. Sert de **socle** timing/qualité de service, mais n’est pas à lui seul un “remplaçant SDVoE”. ([1.ieee802.org][8], [IEEE Standards Association][9])

---

### Recommandation rapide (projection architecturale)

* **Dans un même lieu, multiproj, commutation IP à très faible latence** → **IPMX** (ou ST 2110) avec switches compatibles PTP; envisagez JPEG XS si le 10 GbE est contraint. ([smpte.org][2], [AVNetwork][3])
* **Entre sites / longues distances** → **RIST** ou **SRT** comme tuyau de contribution résilient; sur place, décodez puis distribuez en IPMX/2110. ([RIST Forum][4], [GitHub][6])

Si tu me donnes ton **débit cible** (4K60 4:4:4/4:2:2, nombre de projos) et l’**infrastructure réseau** dispo (1/10/25 GbE), je te propose un **schéma concret** (PTP, NMOS, codecs, SFP) et une short-list matériel compatible IPMX.

[1]: https://ipmx.io/?utm_source=chatgpt.com "IPMX"
[2]: https://www.smpte.org/standards/st2110?utm_source=chatgpt.com "ST 2110 Suite of Standards"
[3]: https://www.avnetwork.com/features/ipmx-the-next-great-av-standard?utm_source=chatgpt.com "IPMX: The Next Great AV Standard?"
[4]: https://www.rist.tv/?utm_source=chatgpt.com "RIST Forum"
[5]: https://static.vsf.tv/download/technical_recommendations/VSF_TR-06-4-Part-6_2024-07-22.pdf?utm_source=chatgpt.com "VSF_TR-06-4-Part-6_2024-07-22.pdf"
[6]: https://github.com/Haivision/srt?utm_source=chatgpt.com "Haivision/srt: Secure, Reliable, Transport"
[7]: https://haivision.github.io/srt-rfc/draft-sharabayko-srt.html?utm_source=chatgpt.com "The SRT Protocol - GitHub Pages"
[8]: https://1.ieee802.org/tsn/?utm_source=chatgpt.com "Time-Sensitive Networking (TSN) Task Group |"
[9]: https://standards.ieee.org/ieee/802.1BA/10547/?utm_source=chatgpt.com "IEEE 802.1BA-2021"
