+++
title = "Kodgen & Refureku"
slug = "Kodgen & Refureku"
date = "2020-07-03T00:00:00"
image = ''
description = "Librairie de réflexion dynamique C++17"
disableComments = true
draft = false
+++

## Détails
- **Technologies / Langages :** C++17, libclang, [toml11](https://github.com/ToruNiina/toml11), Visual Studio 2019, Git, Trello
- **Plateforme :** Windows / Linux

---

## Présentation

A l'origine, Kodgen et Refureku étaient une seule librairie, mais je me suis rendu compte qu'une partie du code pouvait être réutilisée pour des besoins autres, c'est pourquoi j'ai décidé de séparer le code initial en 2 librairies distinctes.

[Kodgen](https://github.com/jsoysouvanh/Kodgen) est une librairie qui permet de générer des fichiers à partir de données extraites de fichiers C++. Elle sert de base à Refureku en parsant et générant le code de réflexion pour chaque entité c++ taggée. La manière dont sont taggées les entités dans le code C++ est personnalisable en modifiant un fichier de configuration, ou en modifiant le main du parser/générateur directement.

[Refureku](https://github.com/jsoysouvanh/Refureku) est une librairie de réflexion dynamique c++17. Elle permet d'accéder aux informations d'entités C++ comme les classes ou les enums.

## Motivation

J'ai écrit cette librairie d'abord car la réflexion est un sujet qui m'attire beaucoup en programmation. Mon expérience passée sur le [Turbo Engine](https://juliensoy.netlify.app/post/turbo-engine/) m'a donné envie de continuer à explorer et améliorer ce qu'on avait déjà pu mettre en place.
La réflexion n'est à ce jour pas supportée nativement par le C++, et les premières ébauches n'arriveront pas avant C++23. La réflexion en C#, au contraire, est extrêmement poussée et agréable à utiliser. Je me suis donc inspiré de l'architecture C# pour développer Refureku.

Il existe déjà un certain nombre de librairies de réflexion C++, mais la plupart ont des défauts que je voulais éviter dans mon implémentation. Par exemple, dans certaines implémentations il faut réécrire toutes les informations des entités réfléchies une seconde fois après la déclaration de l'entité en question. Cela peut ressembler à quelque chose comme :

```cpp
class ExampleClass
{
	private:
		int i;
};

REFLECT_CLASS("ExampleClass", (int) i)
```

Écrire les choses 2 fois est 1. fastidieux et 2. source d'erreur quand on modifie les entités. L'avantage de ce type d'implémentation cependant est que l'on a le contrôle sur ce qui est réfléchi et ce qui ne l'est pas. Il serait certes plus agréable encore que toute la base de code soit réfléchie automatiquement, mais cela aurait un impact non négligeable sur la mémoire utilisée (notamment à cause des includes de librairies externes ou de la STL). Il est donc intéressant de pouvoir choisir ce qui doit être réfléchi dans le programme. Un deuxième avantage de pouvoir sélectionner les entités est que l'on peut ajouter un système d'attributs pour chaque entité réfléchie. Cela peut être très utile pour développer l'éditeur d'un moteur de jeu.

Avec Refureku, il suffit de tagger une entité avec une macro pour la réfléchir, et on peut fournir des attributs supplémentaires dans la macro pour ajouter des informations sur l'entité. De cette façon, on n'écrit l'entité qu'une seule fois, et il est facile de modifier le code par la suite sans générer d'erreur.

```cpp
#include "Generated/ExampleClass.rfk.h"

class ReflectedClass(ExampleClassAttribute1) ExampleClass
{
	private:
		ReflectedField(ExampleFieldAttribute1, ExampleFieldAttribute2)
		int i;

	ExampleClass_GENERATED
};
```