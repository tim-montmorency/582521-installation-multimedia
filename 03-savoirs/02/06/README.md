<!-- %: BLOC2_SAVOIR6  -->
# Contrôle de la qualité du produit multimédia
<!-- %; -->

Cette fiche résume les contrôles essentiels pour valider une installation audiovisuelle réactive (clavier MIDI + microphone + diffusion stéréo + projection vidéo interactive).

<!-- start-replace-subnav -->

<!-- end-replace-subnav -->

### Objectifs du contrôle qualité
- Vérifier la complétude et la robustesse de la chaîne signal (entrée → traitement → sorties).
- S'assurer d'une réactivité suffisante (latence acceptable) et de l'absence d'artéfacts audio/visuels.
- Garantir la sécurité physique, électrique et la stabilité pendant l'exploitation.

### Checklist rapide (tests à faire)
1. Matériel et câblage
   - Le clavier MIDI, le micro, l'interface audio, les enceintes et le projecteur sont correctement alimentés et câblés.
   - Les câbles XLR/TRS/HDMI/Cat6 sont intacts et correctement verrouillés.
2. Fonctionnalité
   - Le logiciel reçoit bien les messages MIDI et le flux audio du micro.
   - Les sorties audio L/R fonctionnent (test de panning) et la projection affiche l'image attendue.
3. Qualité audio
   - Pas de clipping sur l'entrée micro ni sur la sortie master (mesure de niveau).
   - Bruit de fond tolérable ; appliquer gate/filtre si nécessaire.
4. Latence et réactivité
   - Mesurer délai entre action (touche MIDI ou son) et réaction visuelle/sonore ; viser < 10–60 ms.
   - Ajuster buffer audio et optimisations si latence trop élevée.
5. Synchronisation A/V
   - Vérifier que les événements son/visuel sont jugés cohérents lors d'une démonstration.
6. Stabilité
   - Faire tourner le patch 10–15 minutes en conditions réelles : pas de crash, pas de montée en charge CPU/GPU excessive.
7. Sécurité et déploiement
   - Les alimentations des extenders HDMI-over-Cat6 sont correctes (PoE/AC) ; câbles sécurisés et passages protégés.
   - Les élingues de sécurité sont toutes déployées et adéquatement fixée 

### Critères d'acceptation (minimum)
- Interaction visible et audible : le système réagit de façon stable et compréhensible aux entrées MIDI/micro.
- Latence perçue faible (idéal < 150 ms) ou justifiée techniquement.
- Pas de clipping audible ni d'erreurs fréquentes pendant la démonstration de 3 minutes.


### Notes pratiques
- Documenter les numéros de version du logiciel et les presets utilisés.
- Prévoir un plan de secours (fichier média local, preset de secours) en cas de défaillance réseau ou de streaming.

