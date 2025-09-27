+++
title = "Poshon"
slug = "Poshon"
date = "2020-02-10T00:00:00"
image = 'Poshon/LevelSelection.png'
description = "Projet R&D sur Nintendo Switch"
disableComments = true
draft = true
+++

## Détails
- Effectif : 2 programmeurs
- Délai : 2 semaines
- Technologies / Langages : Unity 2019.3, C#, Visual Studio 2019, Git, Trello
- Plateforme : Nintendo Switch

---

## Présentation

Ce projet était un projet de R&D sur la Nintendo Switch.
Notre objectif était d'explorer les fonctionnalités proposées par la console en développant un party-game en multijoueur local.
Poshon (ポーション) est donc un party-game en multijoueur local dans lequel l'objectif est de reproduire des potions le plus fidèlement possible dans un temps imparti.
Pour faire changer les attributs d'une potion, il faut intéragir avec les machines du niveau et compléter des mini-jeux.

![Interactibles screenshot](/Poshon/Interactions.png#center)

---

## Contribution personnelle

- Création d'un framework style Game Mode / Game State / Character / Controller
- Gameflow
- Camera / Controller / Character
- Système d'objets avec lesquels on peut intéragir (il semblerait après recherche que le mot intéractible n'existe pas en français... ni en anglais)
- Mise en place des mini-jeux pour chaque... intéractible, en explorant les inputs proposés par la Switch (gyroscope, accéléromètre, différentes touches)
- Mise en place de la dimension multijoueur grâce au nouvel Input System de Unity
- Création des différents levels
- Loading screen
- Système de scoring