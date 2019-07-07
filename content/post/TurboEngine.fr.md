+++
title = "Turbo Engine"
slug = "Turbo Engine"
image = "TurboEngine/TurboEngineCover.png"
description = "Réalisation d'un moteur de jeu vidéo 3D complet avec éditeur et d'un jeu de démonstration."
date = 2019-06-13T15:19:20+02:00
disableComments = true
+++

## Détails
- Effectif : 4 programmeurs
- Délai : 5 mois
- Technologies / Langages : Visual Studio 2017, Git, Trello, C++17, Python 3.7
- Librairies : Qt, GLFW, PhysX, FMOD, nlohmann json, OpenGL, Freetype, stb_image, Glew, Autodesk FBX SDK, TinyObjLoader, SOL2, RuntimeCompiledCPlusPlus

---

## Présentation

Ce projet de fin de deuxième année était constitué d'un ensemble de trois sous-projets :

- Développement d'un moteur de jeu vidéo
- Développement d'un éditeur du moteur
- Développement d'un jeu à l'aide de l'éditeur

#### Le Turbo Engine

![TurboEngine logo](/TurboEngine/TurboEngineStamp.png#center)

Le Turbo Engine est un moteur de jeu vidéo 3D pensé pour permettre un développement rapide et confortable à la manière des plus grands. Il implémente les fonctionnalités de base telles que la physique avec un système de layer flexible (PhysX 3.4), la gestion du son (FMOD), un éditeur de material, ou un rendu PBR agrémenté de quelques effets de post-process. Le système de réflection permet la sérialisation au format binaire (custom) ou texte (json via la librairie nlohmann json). Grâce au hotreload, on peut ajouter et/ou modifier des scripts C++ utilisables par la suite en tant que component dans les entités de la scène. Le système de scripting C++ se veut agréable, et il suffit à l'utilisateur de spécifier certaines propriétés au dessus de ses variables pour les appliquer. Un outil tier développé en Python 3.7 parse les fichiers de scripts, puis génère des fichiers de métadonnées exploités par le moteur.

#### Le Turbo Editor

![TurboEditor screenshot](/TurboEngine/TurboEngineEditor.PNG#center)

Le Turbo Editor est un outil développé avec la librairie Qt. Il est composé d'un certain nombre de widgets qui sont détachables de la fenêtre principale, permettant à l'utilisateur de les réorganiser et de les déplacer sur plusieurs écrans. Les différents widgets sont les suivants :

- L'explorateur de fichiers pour avoir accès à tous les dossiers/fichiers du projet
- Le loggeur 
- Le Scene tree, qui permet de visualiser les entités présentes dans la scène ainsi que leur hiérarchie
- L'inspecteur, qui affiche et permet d'intéragir avec les components d'une entité
- La Liste de sons, qui affiche une liste de tous les fichiers audio du projet et permet de les écouter
- Le Mixeur, qui permet de créer et de mixer différents canaux de sons
- L'éditeur de material, pour créer et modifier les matérials à partir des shaders et textures du projet
- Les paramètres de physique qui permettent de gérer et configurer différents layers de physique
- La game view
- Les scene view, qui peuvent être ouvertes en 4 exemplaires simultanément pour éditer/visualiser la scène de différents points de vue

On peut créer des scripts avec des template personnalisables et les compiler d'un simple clic. Les scripts pourront par la suite être ajoutés aux entités de la scène, et les variables marquées comme "réfléchies" dans les scripts seront disponibles dans l'inspecteur.

Voici un exemple de script (header) généré auquel on aurait ajouté quelques variables :

```cpp
#pragma once

#include <TEConfig.hpp>
#include <Core/FundamentalTypes.hpp>
#include <Core/ECS/Components/BehaviorComponent.hpp>

#include <GameplayMinIncludes.hpp>

// * This include should always be the last one. moving it will cause conflicts
#include "Generated/TestScript.generatedhpp"

class [[ReflectedClass(Component)]] TestScript : public turbo::core::ecs::BehaviorComponent
{
	TURBO_CLASS_GENERATION()

	private:
		#pragma region Variables
		
		[[ReflectedAttr]]
		TEint16	m_testInt = 16u;

		[[ReflectedAttr]]
		Vector<math::Vector3f>	m_vector;

		[[ReflectedAttr]]
		RigidBody*	m_rigidBody;

		//This attribute will not be shown in the editor thanks to the HiddenInEditor attribute
		[[ReflectedAttr, HiddenInEditor]]
		TEfloat	m_hiddenAttribute;

		#pragma endregion

	protected:
		#pragma region Methods
		
		virtual void init()	noexcept override;
		virtual void update()	noexcept override;

		#pragma endregion
};

REGISTER_TO_REFLECTION()
```

Et le .cpp correspondant, lui aussi auto généré et sans modifications (excepté l'include de RigidBody) :

```cpp
#include "TestScript.hpp"

#include "Components/Physic/RigidBody.hpp"


void TestScript::init() noexcept
{
	Parent0::init();
}

void TestScript::update() noexcept
{
	Parent0::update();
}
```

Comme on peut le voir, de la même façon que Unreal Engine 4, on peut appeler dans les méthodes overridées la fonction base du ou des parents (via Parent0, Parent1, ... ParentN) pour étendre des comportements.

#### Le Turbo Game

![TurboGame screenshot](/TurboEngine/TurboGame.jpg#center)

Le jeu que nous avions à développer devait dans la mesure du possible servir de vitrine au moteur, pour en démontrer toutes les fonctionnalités. Certaines contraintes nous étaient aussi imposées, comme le fait que le jeu devait être un FPS-Puzzle. Nous avons donc opté pour un jeu d'aventure narratif parsemé d'énigmes. On incarne dans le jeu un archéologue qui s'aventure dans un temple ancien, guidé par la voix de sa coéquipière qui lui donne des informations par talkie walkie. Je n'en dirai pas plus ici pour garder quelques surprises pour les lecteurs voulant tester le jeu.

--- 

## Contribution personnelle

J'ai eu l'occasion lors de ce projet de travailler sur les 3 sous-projets que sont le moteur, l'éditeur et le jeu. En tant que chef de projet, j'ai pu être confronté à de nombreuses problématiques posées par le travail en équipe sur une relativement longue période. Les features que j'ai pu développer sont également très variées, ce qui me permet d'avoir une très bonne vision de l'ensemble du moteur.
J'ai notamment développé :

- La librairie de mathématiques (Vector2-3-4, Matrix4, Quaternion...) + tests unitaires
- Système de callbacks et d'events custom
- La logique globale du moteur (main loop, gestion des scènes, gestion du temps)
- L'ECS (Entity Component System)
- Certains components de base (Transform)
- Le système de gestion de projets et d'assets
- Le wrapping + implémentation de la librairie de physique
- L'ensemble du système de réflection et de sérialisation
- Le système de HotReload
- L'inspecteur de l'éditeur (génération de widgets générique pour les classes utilisateurs + wrapping des components spécifiques à l'Engine)
- Le picking, les gizmos, le multiple-viewports et le controlleur de la scène
- Une grande partie du jeu (concept, énigmes)

Ce projet est probablement le projet qui m'a le plus apporté mais aussi le plus plu depuis que j'ai commencé la programmation. J'ai pu découvrir de manière concrète en quoi consistait la programmation moteur, et j'ai le sentiment que mes compétences ont réellement évolué, que ce soit en programmation ou en gestion.