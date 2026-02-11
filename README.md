# Simulation de Trafic Urbain par IA Générative Hybride

## Présentation du Projet
Ce projet implémente un framework hybride capable de transformer des scènes urbaines fluides en scénarios de congestion dense.  
L'objectif est de générer des données synthétiques photoréalistes pour l'entraînement d'algorithmes de conduite autonome.

### Pourquoi une approche hybride ?
- CycleGAN : Maîtrise la structure géométrique et le placement des véhicules (Stabilité).
- Stable Diffusion (LDM) : Raffine les textures, les reflets et l’éclairage (Réalisme).

---

## Étapes du Pipeline

### 1. Préparation des Données
- Utilisation du dataset Cityscapes.
- Tri sémantique :
  - Images Fluides : ratio voiture < 0.01
  - Images Congestion : ratio voiture > 0.08

### 2. Étape de Structure (CycleGAN)
- Entraînement de 40 heures sur GPU NVIDIA Tesla T4.
- Utilisation de la Cycle Consistency Loss pour garantir que le décor (bâtiments, routes) reste inchangé.
- Génération d’une base structurelle en 256x256.

### 3. Étape de Raffinement (Stable Diffusion)
- Utilisation de Stable Diffusion v1.5 (Img2Img).
- Injection de la sortie du CycleGAN comme image initiale.
- Rendu final en 512x512 avec ajout de détails photoréalistes (ombres, textures).

---

## Résultats
Les performances ont été évaluées sur un échantillon de test de 50 images.

---

## Installation et Utilisation

Le projet est optimisé pour Kaggle avec un accélérateur GPU T4.

### 1. Installation des dépendances
Installer les bibliothèques nécessaires via le notebook ou votre environnement Python.

### 2. Exécution
- Lancer le notebook : ia-generative.ipynb
- Le script génère automatiquement :
  - MON_PROJET_TRAFFIC_MORPH_FINAL.zip : contient les simulations générées.
  - rapport_metrics.png : rapport graphique pour visualiser la stabilité des résultats.

---
