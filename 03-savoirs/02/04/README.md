<!-- %: BLOC2_SAVOIR4  -->
# Intégration des médias pour la spatialisation sonore
<!-- %; -->

<!-- start-replace-subnav -->

<!-- end-replace-subnav -->



La spatialisation sonore consiste à organiser et diffuser des sons dans l’espace afin de créer une expérience immersive. Pour un intégrateur multimédia, cela implique de comprendre les standards de diffusion, de savoir préparer et normaliser les médias, et de maîtriser aussi bien la lecture de fichiers audio que la synthèse sonore en temps réel.

⸻

1. Standards de diffusion audio

Mono
	•	Une seule piste sonore.
	•	Utilisé pour voix ou sons ponctuels.
	•	Peu adapté à l’immersion, mais utile dans des systèmes simples.

Stéréo
	•	Deux canaux : gauche (L) et droite (R).
	•	Standard le plus répandu dans la production multimédia.
	•	Permet des panoramiques simples et un effet de largeur sonore.

Multicanaux
	•	5.1 (six canaux : L, R, C, LFE, Ls, Rs) : cinéma, installations immersives.
	•	7.1 (huit canaux) : variantes cinéma et home-cinéma.
	•	Ambisonie / binaural / WFS (Wave Field Synthesis) : standards pour la spatialisation avancée en 3D.
	•	Adaptés aux dômes, installations VR, ou environnements immersifs.

⸻

2. Préparation et normalisation des médias

Formats audio
	•	Non compressé : WAV, AIFF (qualité maximale, poids élevé).
	•	Compressé sans pertes : FLAC, ALAC (qualité identique à l’original, poids réduit).
	•	Compressé avec pertes : MP3, AAC, OGG (poids réduit mais perte de qualité perceptible).

Normalisation
	•	Objectif : assurer un niveau sonore uniforme entre les fichiers.
	•	Méthodes :
	•	Peak normalization : aligne le niveau maximal.
	•	Loudness normalization (LUFS) : standard actuel (EBU R128, ITU-R BS.1770).
	•	Exemple pratique : normaliser à -23 LUFS pour la télévision, -14 LUFS pour le streaming.

Traitement des médias
	•	Vérifier taux d’échantillonnage (44.1 kHz pour musique, 48 kHz pour audiovisuel).
	•	Vérifier profondeur de bits (16 bits = CD, 24 bits = studio).
	•	Nettoyer bruits parasites, couper silences inutiles.
	•	Rendre cohérents les noms et métadonnées pour faciliter l’intégration.

⸻

3. Diffusion et rendu spatial

Lecture de médias pré-enregistrés
	•	Utilisation de lecteurs multipistes (DAW, QLab, Ableton, Reaper).
	•	Intégration dans des moteurs multimédias (Godot, Unity, TouchDesigner).
	•	Routage via cartes son multicanaux ou protocoles réseau (Dante, AVB).

Synthèse sonore temps réel
	•	Génération et traitement des sons directement lors de l’exécution.
	•	Utilisation de moteurs comme Pure Data, Max/MSP, SuperCollider.
	•	Permet :
	•	Adaptation dynamique aux actions du public.
	•	Effets spatiaux en temps réel (réverbération, mouvement circulaire, etc.).

⸻

4. Bonnes pratiques d’intégration
	1.	Choisir le bon standard selon le dispositif (stéréo pour web, multicanal pour installation).
	2.	Préparer les fichiers en amont (format, taux d’échantillonnage, normalisation).
	3.	Prévoir des versions fallback en cas de limitation technique (ex. stéréo dérivée d’un mix 5.1).
	4.	Optimiser la taille et la qualité pour respecter les contraintes du système (CPU, stockage).
	5.	Documenter l’arborescence des médias : nommage clair, numérotation cohérente.
	6.	Tester dans le lieu de diffusion et ajuster la spatialisation aux contraintes acoustiques.

