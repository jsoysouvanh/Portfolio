+++
title = 'Slide Slide Little Penguin'
slug = 'SSLP'
image = 'SSLP/SSLPScreen.jpg'
description = "Réalisation d'un jeu mobile type Tiny Wings / Dune"
date = '2019-05-20T00:00:00'
disableComments = true
+++

## Détails
- Effectif : 2 programmeurs
- Délai : 1 mois (en parallèle avec d'autres projets)
- Technologies / Langages : Unity 2018, C#, Visual Studio 2017, Git, Trello
- Plateforme : Android

---

## Présentation

Ce projet avait pour objectif de mettre en application un système de génération procédurale de terrain en 2D. Nous n'avions aucune contrainte particulière de production, si ce n'est d'implémenter et de faire apparaître un terrain 2D généré procéduralement. Slide Slide Little Penguin reprend donc le concept de base de Tiny Wings, mais les règles sont différentes : le but est de parcourir la plus longue distance possible en 30 secondes. Le meilleur score du joueur est enregistré et affiché sur l'écran titre.

Les défis proposés par ce projet étaient multiples : on retrouve notamment la problématique des performances mobiles, et un challenge mathématique non négligeable. La physique est elle aussi complètement custom, pour éviter d'utiliser ceux de Unity trop coûteux pour l'effet recherché.

---

## Contribution personnelle

<img src="/SSLP/SSLPEditorView.png" alt = "EditorView" style = "float: right; margin: 0.7rem; max-width: 70%;" />

Je me suis personnellement occupé du développement des courbes mathématiques et de la physique. L'idée était de transformer des courbes connues pour les faire tenir dans des rectangles générés aléatoirement, avec une contrainte supplémentaire cependant : avoir des tangentes plates aux extremités (coefficient directeur nul) pour que le terrain soit continu. Sur l'image ci-contre, on peut voir dans la vue éditeur (viewport supérieur) les rectangles générés aléatoirement. Les rectangles verts représentent des portions de courbes ascendantes, tandis que les rectangles rouges représentent eux des portions de courbes descendentes. Les courbes implémentées ont toutes demandé un travail préparatoire, à savoir la résolution des équations. Une fois les équations résolues, l'implémentation en code a été relativement simple. Au final, ont été implémenté les fonctions sinusoïdales, les fonctions polynomiales de degré 3, l’arc de cercle ou elliptique, ainsi que la fonction "Tangente Hyperbolique".
En ce qui concerne la physique, l'idée était d'avoir une sensation de glisse agréable donc les calculs réalisés ne sont pas du tout réalistes. Des calculs de pénétration sont réalisés avec les portions de terrain proches, et s'il y a pénétration on replace le pingouin sur la courbe en plus d'ajuster sa vélocité en fonction de son angle d'impact et de la tangente du terrain.

Ce projet a été ma première expérience sur mobile, et le rendu final est vraiment au rendez-vous, bien que la feature de base soit vraiment simple. 