+++
title = "Gladiator"
slug = "Gladiator"
date = "2018-11-28T00:00:00"
image = 'Gladiator/GladiatorDemo.gif'
description = "Développement d'un Battle Royal en arène"
disableComments = true
draft = true
+++

## Détails
- Effectif : 2 programmeurs
- Délai : 1 mois
- Technologies / Langages : Unreal Engine 4, C++, Visual Studio 2017, Git, Trello
- Plateforme : PC

---

## Présentation

Le projet Gladiator était un projet qui avait pour premier objectif de nous faire découvrir UE4. L'idée était de créer un Battle Arena à la troisième personne avec les assets à notre disposition (meshs, animations, sons). Le jeu est jouable en solo (contre l'IA) mais aussi en multijoueur online (mode COOP et mode PvP).

---

## Contribution personnelle

Je me suis énormément investi sur ce projet, ce qui m'a permis d'arriver au bout de l'implémentation réseau de Gladiator dans le temps imparti. Une attention toute particulière a été portée à l'architecture qui a été recommencée de zéro pour faciliter la diversification des modes de jeu (dont le mode online). Je n'ai utilisé les blueprints que pour le développement de l'UI, tout le reste est développé en C++ pur. J'ai travaillé sur une grande majorité des features, dont voici une liste non exhaustive :

- Système d'IA complet (BehaviorTree et IA Manager)
- UI complète (menus, lobby, barres de vie...)
- Système de météo changeante (pluie puis beau temps, répliqué sur le réseau)
- Système de score
- Drop d'équipement ramassable
- Système de lock (les ennemis peuvent être verrouillés pour auto target)
- Outline de l'ennemi verrouillé et/ou des équipements ramassables
- Mode réseau PvP
- Mode réseau COOP