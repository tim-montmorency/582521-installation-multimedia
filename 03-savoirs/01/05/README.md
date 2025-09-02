<!-- %: BLOC1_SAVOIR5  -->
# Optimisation des médias pour la projection vidéo architecturale
<!-- %; -->

<!-- start-replace-subnav -->

<!-- end-replace-subnav -->


## Objectif

Obtenir une image **stable, lisible et synchronisée** sur de grandes surfaces, souvent avec plusieurs projecteurs, des angles complexes et un environnement lumineux variable. L’optimisation commence **au moment du rendu** (After Effects/Resolve/Blender) et se poursuit jusqu’au **format de lecture** (serveur média / player).

---

## Générer des médias compatible

* Mire PNG https://vioso.com/testpattern-generator/
* Timecode Audio (LTC) https://elteesee.pehrhovey.net/
* Générer des médias test via ffmpeg https://codeberg.org/gllm/ffmpeg-create-test-media

---

## Résolution, fréquence, cadrage


* **Résolution** : S'assurer d'avoir la bonne, éviter les redimensionnement
* **Fréquence d’images** : 30/60 fps pour mouvements nets et mapping vidéo; 
* **CFR (Constant Frame Rate)** : permet d'avoir une charge similaire constante au niveau du décodage.

---

## Couleur, gamma, dynamique

* **Espace colorimétrique** : travaillez en **Rec.709 / gamma 2.2–2.4**, sauf flots HDR spécifiques (rare en projection mapping live).
* **Profondeur** : privilégiez **10 bits** quand possible (dégradés, ciels, aplats). Sinon, **dithering** subtil pour éviter le banding.
* **Niveaux** : gardez des noirs **super-noirs** (légèrement au-dessus de 0) pour masquer les fuites lumineuses ; limitez les blancs brûlés (les projecteurs “clipent” différemment).
* **LUT & calibration** : si le parc le permet, générez une **3D LUT** par projecteur (ou par groupe) après mesures (sonde), et **bakez** les compensations globales dans vos rendus si le serveur n’applique pas de gestion colorimétrique.

---

## Codecs & conteneurs (lecture locale, latence faible)

**Règle d’or** : préférer des **codecs intra-image** (All-Intra), faciles à décoder, aux GOP longs (H.264/HEVC “streaming”) qui ajoutent latence et risques de saccades.

| Cas d’usage                           | Recommandé                | Pourquoi                                          | À noter                              |
| ------------------------------------- | ------------------------- | ------------------------------------------------- | ------------------------------------ |
| macOS / Apple M-series                | **ProRes 422** (MOV)   | Qualité, décodage matériel fluide                 | Poids élevé → SSD rapide             |
| Windows/NVIDIA/Resolume/TouchDesigner | **HAP Q** (MOV)           | Très fluide via GPU, parfait pour loops & couches | Fichiers volumineux                  |
| Cross-platform qualité/poids          | **DNxHR HQX** (MXF/MOV)   | 10 bits, intra                                    | Support variable selon players       |
| Simple & léger (non critique)         | **H.264 All-Intra** (MP4) | Bonne compatibilité                               | Éviter GOP longs/variable frame rate |

**Audio** : 48 kHz, PCM ou AAC (si besoin de légèreté). Boucles musicales → faites des **loops “seamless”** (points d’entrée/sortie exacts).

---

## Débits, disques, pipeline

* **Débit soutenu** : vérifiez le **throughput** de votre SSD/RAID vs. le cumul des fichiers lus en parallèle (ex. 3×4K60 HAP Q ≠ 1×4K30 ProRes).
* **Pré-rendu par projecteur** : évite le “split” en live et réduit la charge CPU/GPU (moins de scalings/warps en temps réel).
* **Longues séquences** : préférez **segments** (reels) enchaînés plutôt qu’un fichier monolithique gigantesque; facilite la reprise et la mise à jour.

---

## Synchronisation multi-projecteurs

* **Idéal** : serveurs/framebuffers **genlockés** (ou PTP si AV-over-IP), lecture **lockée au rafraîchissement**.
* **Fallback** : démarrez toutes les timelines via **timecode** (LTC) ou **OSC** + horloge partagée; utilisez des **pré-rolls** (quelques secondes noires) pour aligner.
* **Éviter** : pilotes/players qui “dropent” des frames à la volée; préférez **playback deterministe** (all-intra, CFR).

---

## Masques, blends, géométrie

* **Soft-edge** : générez des **masques alpha** dédiés à la résolution finale de chaque projecteur (plumes propres, sans modification d'échelle).
* **Warps** : si possibles, *cuire* les déformations lourdes dans le média (ou au moins pré-compensez certaines courbures) pour alléger le moteur temps réel.
* **Zones interdites** : créez un calque “no-go” (fenêtres, statues, zones légales) et **masquez** directement au rendu.

---

## Nommage & livraison

* **Convention claire** : `SITE_YYYYMMDD_PJ01_3840x2160p30_ProResHQ_v03.mov`
  (site/date/projecteur/résolution/fréquence/codec/version)
* **Dossiers** : `01_masters/`, `02_splitted_by_projector/`, `03_masks/`, `04_audio/`.
* **Fichier Documentation** : joignez un `README.md` avec **fps, codec, durée, point de départ, niveaux** et instructions de boucle.

---

## Check-list express (à cocher)

* [ ] Résolution/fréquence **validées** par le parc projecteurs/serveur
* [ ] **CFR** et **All-Intra** (pas de GOP longs)
* [ ] 10 bits ou dithering → **pas de banding** visible
* [ ] **Masques/blends** au bon pixel pitch, sans rescale live
* [ ] **Niveaux** maîtrisés (noirs non bouchés, blancs non clipsés)
* [ ] **Débit disque** suffisant pour le nombre de flux
* [ ] **Sync** testée (genlock/PTP/LTC/OSC) + pré-roll
* [ ] Nom de fichier & **README** complets


