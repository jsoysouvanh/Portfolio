+++
title = "Turbo Engine"
slug = "Turbo Engine"
image = "TurboEngine/TurboEngineCover.png"
description = "Creation of a complete 3D Game Engine with editor and demonstration game."
date = 2019-06-13T15:19:20+02:00
disableComments = true
+++

## Details
- Headcount: 4 programmers
- Time period: 5 months
- Technologies / Languages: Visual Studio 2017, Git, Trello, C++17, Python 3.7
- Libraries: Qt, GLFW, PhysX, FMOD, nlohmann json, OpenGL, Freetype, stb_image, Glew, Autodesk FBX SDK, TinyObjLoader, SOL2, RuntimeCompiledCPlusPlus

---

## Introduction

This second-year end project was composed of three sub-projects:

- Development of a 3D game engine
- Development of an editor for this engine
- Development of a game using the engine

{{< youtube id="foICXHojFiI" >}}

<p> </p>

#### The Turbo Engine

![TurboEngine logo](/TurboEngine/TurboEngineStamp.png#center)

Turbo Engine is a 3D video game engine which allows a fast and smooth development. It implements a wide range of useful features such as physics with a customable layer system (PhysX 3.4), sound management (FMOD), a material editor, or a full PBR (Physically Based Rendering) rendering pipeline with a bunch of post-process effects. The reflection system allows to serialize data in binary (custom) or text format (json using nhlomann json library). Thanks to the hotreload mecanism, the user can add and/or modify scripts and add them right away to the scene entities. The scripting system (C++) was thought to be easy to use: the user just has to use special keywords above its functions / variables to notify the engine that they have something special (for example, notify the engine to reflect a variable). A Python 3.7 based software will then parse user scripts and generate new metadata files for the Engine.

#### The Turbo Editor

![TurboEditor screenshot](/TurboEngine/TurboEngineEditor.PNG#center)

The Turbo Editor is based on the Qt library. It is made of a bunch of widgets which are undockable, allowing the user to organize his/her own layout as pleased. Here is a list of the different available widgets:

- The file explorer to have a look on the project files
- The logger
- The Scene tree, to have an eye on the scene objects and how they are organized
- The inspector, which displays and allows the user to interact with entity components
- The Sound list, which displays all imported sounds and allows to listen them
- The Mixer, which allows to create and/or manage sounds channels
- The material editor, which allows to create and/or modify materials using all project textures and shaders
- The physics settings, which allow to manage physics layers and fixed time
- The game view
- The scene view, which can be opened up to 4 times simultaneously to edit or vizualize the scene from different point of views

We can create scripts with customised templates and compile them in a simple clic. Scripts can then be edited and added to scene entities, and variables which were labelled with the "Reflected" attribute should be available in the editor.

Here is an example of generated script with some variables:

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

And the corresponding .cpp, also generated without any user modification (except the RigidBody include):

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

As we can see here, we can call overriden functions in derived versions through the Parent0, Parent1, ... ParentN alias to extend behaviors.

#### The Turbo Game

![TurboGame screenshot](/TurboEngine/TurboGame.jpg#center)

The game we had to create had to show as much as possible all the possibilities of the engine. We also had to respect some constraints, like the fact that the game had to be a FPS-Puzzle. We opted for a narrative adventure game. In the game, we play an archeolog who explores an old temple, following the inscructions given by her mate through a talkie walkie. I won't say much more here to keep some surprises to the future players.

--- 

## Personal implication

During this project, I had the chance to work on all sub-projects. As the group leader, I had to face quite a lot of problems, like group cohesiveness or global tasks organization. I worked on a wide range of features which allows me to have a great global view of the engine:

- The maths library (Vector2-3-4, Matrix4, Quaternions...) + unit tests
- Custom callback and event system
- Global engine logic (main loop, scenes management, time management)
- The ECS (Entity Component System)
- Some basic components (Transform)
- Projects and assets management system
- Physic library wrapping and implementation
- The whole reflection and serialization system
- The Hotreload system
- Editor inspector (generic widgets generation for user scripts + engine specific components wrapping)
- Physics based picking, gizmos, multiple viewports handling and scene free controller
- A great part of the game (concept, riddles)

This project is without any doubt the more pleasant project I have worked on since I started programmation. I had the chance to discover what exactly was engine programmation, and I feel like I truly improved my programmation and management knowledge.