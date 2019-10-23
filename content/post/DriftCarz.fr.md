+++
title = "DriftCarz"
slug = "DriftCarz"
date = "2018-10-19T00:00:00"
image = 'DriftCarz/DriftCarzMenu.gif'
description = "Développement d'une librarie réseau C++ et intégration dans un jeu Unity"
disableComments = true
+++

## Détails
- Effectif : 2 programmeurs
- Délai : 2 semaines
- Technologies / Langages : Unity 2018, C#, C++, Visual Studio 2017, Git, Trello
- Plateforme : PC

---

## Présentation

L'objectif de ce projet était de passer un jeu de course simple développé sous Unity en multijoueur online. Pour ce faire, nous avons dans un premier temps développé une librairie réseau (C++) en utilisant Winsock2 que nous avons importée dans Unity. Nous avons ensuite revu un petit peu l'architecture du jeu de course initial, pour faciliter l'implémentation du réseau. Enfin, nous avons implémenté la couche réseau dans le jeu. Nous recherchions cependant un petit peu de challenge et nous sentions qu'il était possible de faire quelque chose de bien polish en poussant le vice un peu plus loin. Nous avons donc étendu le jeu avec un certain nombre de nouvelles features :

- Un Master Server nous permettant de gérer un système de Lobby avec un listing des rooms existantes. Le joueur a alors la possibilité de host une partie en créant une room, ou rejoindre une partie existante
- Lorsqu'on est dans une room et que la partie n'a pas commencé, le host peut modifier les paramètres de la course (nombre de tours, nombre de joueurs). Lorsque tous les joueurs ont indiqué qu'ils étaient prêts, la partie commence
- Un chat disponible quand on a rejoint une room
- Un système de leaderboard qui affiche le temps que chaque joueur a mis pour compléter la course avec un classement

{{< youtube id="mVXk2ly4Lh4" >}}

---

## Contribution personnelle

Dans ce projet je me suis occupé de toute la partie librairie réseau dans un premier temps, puis de son implémentation dans le jeu.
J'ai ensuite développé le système de Master Server (C#) et de chat. Mon collègue s'est quant à lui occupé de la partie purement Unity, à savoir de l'UI (menu / lobby UI, Chat UI, Leaderboard UI), du bind UI / MasterServer / Chat, de la refactorisation du code de départ et de la modification des assets.