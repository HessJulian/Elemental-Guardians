# Unity project conventions

When initializing or opening the Unity project, use the repository root so Unity owns `Assets/`, `Packages/` and `ProjectSettings/`; commit relevant Unity-generated `.meta` files. Do not fabricate `.unity`, `.asset`, `.prefab`, package manifests or `.meta` files. Prefer gameplay code under `Assets/Game/`, organized into cohesive modules as agreed in the architecture.

**Do not use this file to determine whether Unity, a scene or gameplay already exists.** Inspect the current checkout, Unity project configuration and relevant tests instead. Implement only the approved Issue scope; the current `main` branch is the source of truth for integrated code.
