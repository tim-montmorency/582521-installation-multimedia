<!-- %: BLOC1_SAVOIR7  -->
# Documentation du produit multimédia
<!-- %; -->

<!-- start-replace-subnav -->

<!-- end-replace-subnav -->


# Documentation du produit multimédia

## (Projection vidéo & projection architecturale)

## 1) Pourquoi documenter ?

* **Transférabilité** : permettre à un tiers d’installer/opérer le projet sans auteur·e.
* **Traçabilité** : garder l’historique des versions, décisions et calibrations.
* **Maintenance** : accélérer les mises à jour, le dépannage et la reprise après incident.
* **Conformité** : sécurité, permissions, crédits et droits d’utilisation.

---

## 2) Dossier-type (arborescence)

```
PROJET_NOM/
├─ 00_admin/            # Contrats, droits, assurances, autorisations
├─ 01_conception/       # Intentions, scénarisation, moodboard, storyboards
├─ 02_site/             # Relevé architectural, photos, mesures, plans
│  ├─ mesures/          # Distances, hauteurs, lux, coordonnées
│  ├─ plans/            # PDF/DWG, zones interdites
│  └─ repérage/         # Photos annotées, POV projecteur(s)
├─ 03_tech/             # Ingénierie & déploiement
│  ├─ mapping/          # Warps, meshes, blends, masques
│  ├─ couleur/          # LUT, profils, rapports de calibration
│  ├─ signal/           # Schémas câblage, patch, IP plan, PTP, VLAN
│  ├─ projecteurs/      # Optiques, throw, lens shift, settings
│  └─ qc/               # Protocoles de tests, rapports & checklists
├─ 04_medias/           # Masters & exports finaux
│  ├─ masters/          # Rendus sources (ex : 16-bit, sans comp.)
│  ├─ playback/         # Fichiers de lecture (ProRes/HAP/DNxHR)
│  ├─ audio/            # Musiques/ambiences (48 kHz), stems
│  └─ docs/             # README_media.md, MediaInfo/ffprobe
├─ 05_logiciels/        # Projets Resolve/AE/Touch/Resolume, versions
├─ 06_exploitation/     # Runbook, démarrage/arrêt, plan de secours
├─ 07_communication/    # Crédits, visuels presse, panneaux
└─ CHANGELOG.md
```

---

## 3) Conventions de nommage

**Règle** : nom clair, stable, triable, contenant les infos clés.

```
SITE_YYYYMMDD_PJ01_3840x2160p30_ProRes422HQ_v03.mov
[Site]_[Date]_[Projecteur]_[Résolution+fps]_[Codec]_[Version]
```

* **Répertoires** : `PJ01`, `PJ02`… pour chaque projecteur.
* **Masques/warps/blends** : `PJ01_mask_v02.png`, `PJ01_blend_v03.png`, `PJ01_warp_v05.mesh`.
* **Audio** : `MUSIC_main_48k_stereo_v01.wav`, `AMB_loop_48k_v02.wav`.

---

## 4)  Planification Réseau / IP plan (CSV)

```
device,role,ip,mask,gateway,vlan,ptp_role,notes
SwitchCore,Layer2,10.10.0.1,255.255.255.0,10.10.0.254,20,GM,IGMP snooping on
PJ01_Decoder,AV-IP,10.10.0.21,255.255.255.0,10.10.0.254,20,Slave,PTP Locked
```

---

## 5) Schémas et documents techniques essentiels

* **Plan de projection** : positions, cônes, surfaces cibles, zones interdites.
* **Schéma de signal** : source → distribution → extenders/fibre → projecteurs (inclure **longueurs de câble**, types et références).
* **Plan réseau** (si AV-over-IP) : topologie, VLAN, QoS, **PTP** (GM/Boundary/Ordinary clocks), IGMP.
* **Fiches projecteur** : modèle, lampes/heures, firmware, réglages (gamma 2.2–2.4, iris, gains/bias).
* **Calibration couleur** : procédure, LUT (.cube), rapports ΔE avant/après.
* **Warps & blends** : fichiers **par projecteur**, captures d’écran “avant/après”, notes de tolérance (ex. convergence ≤ 0,5 px perçu).

---

## 6) Spécifications média (claires, au même endroit)

* **FPS** : Déterminer le FPS (30 ou 60)
* **Codecs** : intra-image (ProRes/DNxHR/HAP) + **10 bits** si possible.
* **Audio** : 48 kHz, marges -1 dBFS max, boucles “seamless” si besoin.
* **Noirs/Blancs** : PLUGE validée, pas de clipping.
* **Export par projecteur** : éviter le split “on the fly” quand c’est possible.

Inclure un `README_media.md` avec : specs, tailles, poids, checksums, et **comment tester** (commandes `ffprobe`/`mediainfo`).

---

## 7) Procédures (runbook)

### 7.1 Démarrage minimal

1. Allumer l’infrastructure (switches/serveurs), attendre PTP lock si AV-IP.
2. Allumer projecteurs (ordre, warm-up).
3. Vérifier résolutions/Hz, synchro, V-Sync/plein écran.
4. Lancer **mires** (grille, [PLUGE](https://en.wikipedia.org/wiki/Picture_line-up_generation_equipment), rampes) → focus/alignement/niveaux.
5. Lancer médias (pré-roll noir 2–5 s) → vérifier coutures/latence.

### 7.2 Arrêt

1. Stop médias → noir propre.
2. Éteindre projecteurs (cooldown).
3. Éteindre serveurs/switches dans l’ordre.

### 7.3 Plan de secours

* **Fallback** : clip “bandeau” local par projecteur (+clé USB), routing alternatif.
* **Câbles de rechange** (HDMI/SDI/fibre), SFP/SFP+ spare, alimentation/UPS.
* **Procédure “dégradée”** imprimée (1 page).

---

## 8) Contrôle qualité (QC) — modèles rapides

### 8.1 Checklist site (extrait)

* [ ] Image au carré (lens shift, **zéro keystone** si possible)
* [ ] Focus centre + coins ; convergence (multi)
* [ ] Blends neutres, pas de surbrillance au recouvrement
* [ ] Niveaux validés (PLUGE) ; gamma uniforme
* [ ] ΔE inter-projecteurs < 3 (si sonde)
* [ ] Latence stable ; 0 drop frame sur 15 min
* [ ] PTP/Genlock OK ; pertes réseau < 0,01 % (AV-IP)
* [ ] Sécurité/rigging/ventilation validés

### 8.2 Rapport QC (gabarit)

```
# QC Rapport – [Site], [Date]
- Parc/projecteurs :
- Luminance mesurée (centre/coins) :
- Réglages clés (gamma, iris, gains/bias) :
- ΔE moyen / max :
- Convergence & blends :
- FPS/latence/drops :
- Incidents & correctifs :
- Statut : OK / Réserves / À corriger
```

---

## 9) Versioning, dépôts & traçabilité

* **Version sémantique** : `vMAJEUR.MINEUR.PATCH` pour médias & docs.
* **CHANGELOG.md** : chaque modification résumée (qui, quoi, pourquoi).
* **Git (+ LFS)** : pour projets et gros médias ; tags par jalons (`v1.0.0_siteA`).
* **Checksums** (SHA-256) : fournis avec les livrables.
* **Export “gelé”** : ZIP/7z des dossiers `04_medias/playback/` + `03_tech/` + `06_exploitation/`.

---

## 10) Crédits, droits & conformité

* **Crédits** : artistes, musique, partenaires, licences (logos, police).
* **Droits** : territoire, durée, supports, restrictions horaires (façades).
* **Permissions** : autorisations municipales/propriétaires, assurance, sécurité publique.

---

## 11) Livrable final (checklist “package”)

* [ ] `README_global.md` (plan, contacts, versions, sommaire)
* [ ] Dossier **site** complet (mesures, plans, repérage)
* [ ] Schémas **signal & réseau** (PDF) + liste câbles (longueurs/réfs)
* [ ] **Warps/blends/masques** par projecteur
* [ ] **LUT** + rapport calibration
* [ ] **Médias** de lecture + checksums + `README_media.md`
* [ ] **Runbook** (démarrage/arrêt), **plan de secours**
* [ ] **QC** (rapports + checklists signées)
* [ ] **Crédits & droits**

---

## 12) Erreurs fréquentes à éviter

1. Fichiers en **VFR** ou GOP longs → saccades/latence.
2. Warps/blends non versionnés → impossible de revenir en arrière.
3. Niveaux non validés (noirs bouchés, couture visible).
4. Absence de plan réseau/PTP → instabilités en AV-IP.
5. Arborescence & noms incohérents → pertes de temps en urgence.

---