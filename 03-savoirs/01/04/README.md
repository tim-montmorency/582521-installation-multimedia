  <!-- %: BLOC1_SAVOIR4  -->
# Emploi de protocoles pour transporter la vidéo en temps réel
<!-- %; -->

<!-- start-replace-subnav -->

<!-- end-replace-subnav -->

## Distribution inter-applications

De logiciel à logiciel, depuis la même carte graphique

* **Latence** : quasi nulle (< 5 ms)
* **Compression** : aucune
* **Altération** : aucune


* **[Spout](https://spout.zeal.co/)** (Windows)
  * TouchDesigner https://docs.derivative.ca/Syphon_Spout_Out_TOP
  * OBS https://github.com/Off-World-Live/obs-spout2-plugin
  * Unity https://github.com/keijiro/KlakSpout/
  * Godot https://github.com/you-win/spout-gd

* **[Syphon](http://syphon.v002.info/)** (macOS)

* **[PipeWire](https://pipewire.org/)** / **[DMA-BUF](https://www.kernel.org/doc/html/latest/driver-api/dma-buf.html)** (Linux)



## Distribution point-à-point 

### Grand public 

Proximité, usage courant, non-compressé 

#### HDMI

* **Câble / connecteur** : HDMI Type-A (cuivre).
* **Portée passive typique** : 5–10 m (jusqu’à \~15 m avec très bon câble).
* **Au-delà** : répéteurs ou **AOC HDMI** (fibre active) → 30–100 m.
* **Remarques** : sensible à la qualité; 4K60 4:4:4 exige des câbles haut débit.

#### DisplayPort

* **Câble / connecteur** : DP 20 broches (cuivre).
* **Portée passive typique** : 2–3 m (peut monter à 5 m selon débit).
* **Au-delà** : **AOC DP** (fibre active) → 30–100 m.
* **Remarques** : très répandu côté PC/médiserveurs.

#### (Héritage) DVI / VGA 

* **DVI-D** : \~5 m à 1920×1200 (10–15 m avec booster/AOC).
* **VGA** (analogique) : 7–15 m “propres” max en haute résolution; à éviter pour du mapping exigeant.

#### (Héritage) Analogue


---

### Semi-pro 

transport sur cuivre, longueurs modestes, cablages cat6 générique peu couteux


#### Extendeurs HDMI sur Cat6 (HDMI over Cat6 / adaptateurs)

HDMI sur Cat6 (propriétaires) : adaptateurs qui « mappent » le signal HDMI sur des paires torsadées RJ45; implémentations très variées — certaines proches de HDBaseT, d'autres simples/économiques (transmission TMDS ou compression propriétaire).

* **Câble / connecteur** : Cat5e/6 (RJ45) — parfois Cat6a recommandé pour meilleure marge.
* **Portée typique** : 20–100 m selon la qualité de l'extendeur et du câble (les adaptateurs non‑HDBaseT chutent souvent avant 70 m).
* **Types** : solutions "HDBaseT" pleinement conformes (latence très faible, features : réseau/IR/RS‑232/PoH) vs extendeurs propriétaires (simple paire adaptation TMDS, moins robustes).
* **Caractéristiques** : peuvent transmettre HDMI non compressé ou légèrement compressé; supports varient (1080p60 commun, 4K dépend du modèle — vérifier 4K60 4:4:4 si nécessaire).
* **Alimentation** : certains systèmes utilisent PoH/PoE pour alimenter la partie distante; d'autres nécessitent une alimentation locale.
* **Remarques d'installation** : utiliser des câbles de bonne qualité, éviter les longues multiprises/daisy‑chains, préférer des paires blindées (SF/FTP) dans les environnements fortement bruités; tester la configuration complète (résolution/fréquence) avant installation définitive.
* **Usage typique** : projection distante, murs d'images simplifiés, installations où la fibre/SDI n'est pas justifiée.
* **Conseil** : pour des distances >100 m ou en présence d'interférences électriques importantes, préférer la fibre ou des convertisseurs HDMI↔fibre; pour installations multi‑écrans et routage avancé, considérer AV‑over‑IP ou SDVoE.

#### HDBaseT (transport HDMI sur paires torsadées)

Une norme/plateforme (IEEE‑adjacente, consortium) conçue pour transporter simultanément vidéo HDMI non compressé, audio, Ethernet, contrôles (IR/RS‑232), et parfois alimentation (PoH) sur un seul câble Cat5e/6 jusqu'à 100 m. Interopérable entre équipements conformes.

* **Câble / connecteur** : Cat 5e/6/6a (RJ45).
* **Portée** : 100 m par segment.
* **Caractéristiques** : vidéo (jusqu’à 4K selon version), réseau/IR/RS-232, parfois alimentation (PoH).
* **Usage typique** : relier une régie à un projecteur éloigné sans passer à la fibre.



---

#### Broadcast / Pro 

point-à-point, câblage spécialisé, connecteur vérouillable  

### SDI (HD-SDI / 3G / 6G / 12G)

* **Câble / connecteur** : coaxial 75 Ω (RG-6/Belden), BNC.
* **Portées usuelles** (ordre de grandeur, câble premium + bons drivers) :
  * **HD-SDI / 3G-SDI** : \~70–100 m
  * **6G-SDI** : \~70 m
  * **12G-SDI** : \~70–100 m (très dépendant du câble)
* **Atouts** : robustesse, re-clocking possible, standard pro pour longues lignes terrain→projecteur.

---

###  Fibre optique 

(très longues distances / immunité EMI)

#### Extenders & AOC

* **AOC HDMI/DP** : câble “hybride” cuivre+fibre → 30–100 m plug-and-play.
* **Convertisseurs fibre** (HDMI↔fibre, SDI↔fibre) :
  * **Multimode** : quelques centaines de mètres.
  * **Monomode** : kilométrique (1–10 km+).
* **Connecteurs** : LC (courant), parfois ST/SC.
* **Atouts** : très longue portée, aucune interférence, idéal en environnement bruité (électricité, moteurs, DMX).

---

## Distribution via ip 

### AV-over-IP 

distribution, multiprojection, synchronisation à grande échelle

### NDI® / Dante AV (1 GbE)

* **Câble / connecteur** : Ethernet cuivre Cat 5e/6 (RJ45) → **100 m par segment**; fibre via SFP pour km+.
* **Atouts** : acheminement sur réseau existant, monitoring flexible; latence variable selon codec/profil (NDI HX plus compressé, NDI “full” plus gourmand).
* **Usage** : multi-écrans, retours, prévisualisations, certaines diffusions “soft-compressées”.

* 

### SDVoE (10 GbE, pro AVoIP “quasi sans latence”)

* **Câble / connecteur** : Cat 6a / 10 GbE ou fibre SFP+ pour distances longues.
* **Atouts** : latence très faible, qualité "visually lossless", switching/routage hardware pour grands dispositifs multi‑écrans.
* **Usage** : murs d'images, grands espaces nécessitant commutation/routage temps réel.

### SMPTE ST 2110 (flux essences séparées, pro)

* **Principe** : série SMPTE pour transport sur IP des essences vidéo, audio et metadata séparées (non encapsulées dans un conteneur unique). Conçu pour environnements broadcast pro.
* **Atouts** : latence faible, horloge et synchronisation (PTP), interopérabilité pro, convient pour workflows temps réel non compressés ou faiblement compressés.
* **Usage** : régies, centres de diffusion, interconnexion équipements broadcast sur réseau IP dédié.

### RTP / MPEG‑TS (transport traditionnel sur IP)

* **RTP / RTSP** : utile pour streaming temps réel point‑à‑point; faible overhead, compatible avec de nombreux décodeurs.
* **MPEG‑TS** : format encapsulé pour diffusion (ISO basé sur le standard MPEG‑2‑TS), encore très répandu pour contribution et distribution via CDN ou liaisons point‑à‑point.

### MPEG‑DASH / CMAF (ISO pour la distribution adaptative)

* **CMAF / MPEG‑DASH** : standards ISO pour la distribution adaptative sur HTTP (streaming adaptatif, supporte low‑latency variants).
* **Atouts** : interopérabilité, longévité, adapté aux CDN et au delivery internet à grande échelle.

### WebRTC (ultra faible latence, navigateurs)

* **Atouts** : latence très faible, peer‑to‑peer ou via SFU; natif dans navigateurs modernes, supporte audio/vidéo/data channel.
* **Usage** : interactions en temps réel, previews, retours de scène, petits dispositifs de collaboration.

* Implementation: https://vdo.ninja/


### SRT / RIST (transport résilient, ouvert ou open source)

* **SRT** : protocole open‑source (Haivision) pour transport vidéo fiable et sécurisé sur réseaux Internet non fiables (correction d'erreurs, chiffrement optionnel).
* **RIST** : initiative ouverte fournissant un transport fiable similaire, ciblant l'interopérabilité et la simplicité.
* **Usage** : contribution entre sites, backhaul sur Internet là où UDP seul est trop instable.

---

## Règles de pouce (projection architecturale)

* **≤ 15 m** : HDMI/DP cuivre de qualité; testez 4K60 en amont.
* **15–100 m** : Extendeurs HDMI sur Cat6(budget), **HDBaseT** (simple), ou **SDI** (pro, robuste).
* **> 100 m** ou environnement “bruité” : **fibre** (AOC ou convertisseurs HDMI/SDI↔fibre).
* **Multiproj / grandes façades** : **AV-over-IP** (SDVoE si budget/perfs, NDI/Dante AV si réseau 1 GbE existant), clock réseau soignée, switches adaptés.
* **Toujours** : vérifier résolution, fréquence (4K60 vs 4K30), sous-échantillonnage (4:4:4 vs 4:2:0), marge de qualité câble, et prévoir du **re-clocking**/des **répéteurs** si nécessaire.

---




Parfait 👍 Voici la version **synthétique avec liens officiels** (la première fois que chaque technologie est mentionnée) :

---

## ⚖️ Comparatif partage de textures vidéo 

| Contexte     | Protocoles    | Latence    | Compression | Altération |
| ------------ | ------------- | ---------- | ----------- | ---------- |
| **Local**    | Syphon, Spout | < 5 ms     | Aucune      | Nulle      |
| **LAN**      | NDI           | 16–40 ms   | Légère      | Faible     |
|              | SMPTE 2110    | < 1f       | Nulle/XS    | Nulle      |
|              | RTSP          | 200–500 ms | Forte       | Moyenne    |
| **Internet** | WebRTC        | 100–400 ms | Moyenne     | Moyenne    |
|              | SRT           | 200 ms–2s  | Variable    | Variable   |
|              | RTMP          | 2–5 s      | Forte       | Moyenne    |
|              | HLS/DASH      | 10–30 s    | Forte       | Moyenne+   |

---
