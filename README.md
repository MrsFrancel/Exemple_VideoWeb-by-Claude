# Exemple_VideoWeb-by-Claude

Scène 3D interactive WebGL — Airbus au coucher de soleil, générée entièrement par Claude via la compétence **video3d**.

---

## 🚀 Lancement

1. Cloner ou télécharger ce dépôt
2. **Double-cliquer sur `index.html`** (connexion internet requise pour charger Three.js depuis le CDN)
3. Aucune installation, aucun serveur local nécessaire

---

## 🎮 Contrôles

| Action | Effet |
|---|---|
| Déplacer la souris | L'avion suit le curseur |
| Clic maintenu | Active la trainée de condensation + boost d'accélération |

---

## 🛠️ Compétence Claude utilisée

Ce projet a été généré avec la compétence **`/video3d`** pour Claude Code.

👉 **Projet GitHub de la compétence** : [https://github.com/MrsFrancel/VideoWeb-by-Claude](https://github.com/MrsFrancel/VideoWeb-by-Claude)

---

## 📋 Prompt pour reproduire ce rendu

Lancez `/video3d` dans Claude Code, puis utilisez le brief suivant :

```
/video3d

Style : Cinéma Réaliste (Three.js + shaders GLSL, textures PBR, bloom,
référence Top Gun / Sully)

Qualité : Standard — 1080p

Brief :
- Ambiance     : Moyenne altitude, avion dans les nuages, ciel teinté
                 orangé/violet au coucher de soleil visible à l'horizon,
                 oiseaux en arrière-plan
- Objets/Décor : Airbus blanc détaillé (géométrie procédurale haute
                 résolution), seul, nuages volumétriques environnants,
                 pas de bâtiments
- Caméra       : Fixe, derrière et au-dessus de l'avion, distance moyenne,
                 avion entier visible
- Lumières     : Lumière dorée rasante du soleil couchant à l'horizon,
                 disque solaire et halo visibles au loin
- Animations   : Avion suit la souris (lerp). Nuages dérivent vers la
                 caméra. Oiseaux volent en battant des ailes.
                 Trainée de condensation derrière les deux réacteurs.
- Vidéo/Média  : Aucun, scène 100% 3D
- Son/Audio    : Son procédural (Web Audio API) — réacteurs + vent + afterburner
- Interactions : Clic maintenu → active la trainée + accélère tout
                 (boostFactor x6, FOV 55°→82°, lignes de vitesse,
                 turbulence légère, nuages x9 plus rapides,
                 nez de l'avion plonge)

Contraintes techniques :
- Fichier UNIQUE index.html, double-clic suffit (pas de serveur)
- Three.js r128 via CDN (scripts globaux, pas de modules ES)
- Bloom (UnrealBloomPass) avec fallback renderer.render() si échec
- Message d'erreur visible si Three.js ne charge pas (connexion requise)
- Pool de particules pour la trainée (pas de GC)
- Lignes de vitesse attachées à la caméra (camera.add)
- Particules de trainée avec dérive vz vers la caméra
- Géométrie haute résolution : fuselage 64 segments, ailes effilées
  sur mesure, réacteurs 32 segments avec tore d'entrée et pylônes
- Son procédural Web Audio API (aucun fichier audio externe)
- Résolution : pixelRatio jusqu'à 3, shadow map 2048x2048, précision highp
```

---

## 📦 Stack technique

- **Three.js r128** (CDN, scripts globaux)
- **WebGL** via `THREE.WebGLRenderer` (antialias, highp, ACESFilmic tone mapping)
- **GLSL inline** pour le shader de ciel dégradé
- **Web Audio API** pour le son procédural
- **UnrealBloomPass** (avec fallback automatique)
