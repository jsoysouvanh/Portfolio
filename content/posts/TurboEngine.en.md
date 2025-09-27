---
title: "Turbo Engine"
slug: "turbo-engine"
date: 2019-06-13
description: "Dev of a 3D Game Engine with editor and game"
tags: ["C++", "Git", "School"]
categories: ["Projects"]
cover: "/TurboEngine/logo.png"
showCoverInPost: false
draft: false

lightbox:
  enabled: true
justified_gallery:
  enabled: true
---

![TurboEngine logo](/TurboEngine/TurboEngineStamp.png)

## Overview
- **Team project:** 4 programmers
- **Dev time:** 5 months (school)
- **Tech stack:** C++17, Visual Studio 2017, Git, Trello, Python 3.7, Qt, GLFW, PhysX, FMOD, nlohmann json, OpenGL, Freetype, stb_image, Glew, Autodesk FBX SDK, TinyObjLoader, SOL2, RuntimeCompiledCPlusPlus
- **Platforms:** Windows

The Turbo Engine is a 3D game engine 3 amazing teammates and I developed as third year students. We also developed an editor, and made a small game with it.

{{< youtube id="foICXHojFiI" >}}

---

{{< masonry columns=2 gutter=15 >}}
![In-game screenshot](/TurboEngine/TurboEngineCover.png)
![Turbo Engine editor](/TurboEngine/TurboEngineEditor.png)
![In-game screenshot](/TurboEngine/TurboGame.jpg)
![Turbo Engine editor splash screen](/TurboEngine/splash.png)
{{< /masonry >}}

--- 

## Personal contribution

- Maths library (Vector2-3-4, Matrix4, Quaternions...) and its unit tests
- C++ callback and event system
- Global engine logic (main loop, scene management, time management)
- ECS (Entity Component System)
- Some basic components (Transform)
- Projects and assets management system
- Physics library wrapping and implementation
- Reflection and serialization system
- Hotreload system
- Editor inspector (generic widgets generation for user scripts + engine specific components wrapping)
- Physics based picking, gizmos, multiple viewports handling and scene free controller
- A great part of the game (concept, riddles)