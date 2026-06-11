# Assembly Definition Plan

## Purpose

Assembly Definition, asmdef, is the Unity feature used to split C# code into separate assemblies.

For this portfolio project, asmdef is not just a compile-time convenience. It is a structural design tool used to prove that the Unity project is organized as a client system architecture instead of a single mixed script folder.

## Problem Without asmdef

Without asmdef, most scripts under `Assets` are compiled into one large assembly.

```text
Assets/*.cs
↓
Assembly-CSharp.dll
```

This is simple at first, but it creates problems as the project grows.

- Core, Runtime, Module, Tool, UI, and Debug code can easily mix.
- Any script change can trigger wider recompilation.
- Editor-only code can accidentally be placed near Runtime code.
- Dependency direction becomes unclear.
- It becomes harder to explain the architecture in an interview.

## What asmdef Does

An asmdef file turns a folder into a separate Unity C# assembly.

Example:

```text
Assets/00_Core
↓
NY.Core.dll

Assets/01_Runtime
↓
NY.Runtime.dll

Assets/02_Modules
↓
NY.Modules.dll
```

This allows the project to control which assembly can reference which other assembly.

## Recommended Structure

Current project folder structure:

```text
Assets/
  00_Core/
  01_Runtime/
  02_Modules/
  03_Tools/
  04_Showcase/
  05_Art/
  06_Shaders/
  07_Data/
  08_Scenes/
```

Recommended asmdef files:

```text
Assets/00_Core/NY.Core.asmdef
Assets/01_Runtime/NY.Runtime.asmdef
Assets/02_Modules/NY.Modules.asmdef
Assets/03_Tools/NY.Editor.asmdef
Assets/04_Showcase/NY.Showcase.asmdef
```

No asmdef is needed for these folders at the beginning:

```text
05_Art
06_Shaders
07_Data
08_Scenes
```

## Dependency Direction

Recommended dependency direction:

```text
NY.Core
↑
NY.Runtime
↑
NY.Modules
↑
NY.Showcase

NY.Editor → NY.Core, NY.Runtime, NY.Modules
```

Meaning:

- `NY.Core` references nothing from this project.
- `NY.Runtime` can reference `NY.Core`.
- `NY.Modules` can reference `NY.Core` and `NY.Runtime`.
- `NY.Showcase` can reference `NY.Core`, `NY.Runtime`, and `NY.Modules`.
- `NY.Editor` can reference runtime assemblies, but must be Editor-only.

## Assembly Roles

### NY.Core

Purpose: base layer.

Possible contents:

- `IModule`
- `IModuleLifecycle`
- `IService`
- `ILogger`
- `EventBus`
- result / utility types

References:

```text
None
```

### NY.Runtime

Purpose: runtime execution flow.

Possible contents:

- `GameBootstrap`
- `RuntimeContext`
- `ServiceRegistry`
- `ModuleRunner`

References:

```text
NY.Core
```

### NY.Modules

Purpose: feature modules.

Possible contents:

- Skill System
- Skill Factory
- Skill Instance
- Effect / Target / Condition / Cooldown
- later Animation / Debug / Optimization modules

References:

```text
NY.Core
NY.Runtime
```

### NY.Editor

Purpose: Unity Editor tools.

Possible contents:

- `SkillEditorWindow`
- custom inspectors
- validation tools
- asset creation utilities

References:

```text
NY.Core
NY.Runtime
NY.Modules
```

Required setting:

```text
Include Platforms: Editor
```

### NY.Showcase

Purpose: portfolio demo scene and UI.

Possible contents:

- `ShowcaseController`
- `FeatureTogglePanel`
- `MetricsPanel`
- `BeforeAfterView`

References:

```text
NY.Core
NY.Runtime
NY.Modules
```

## How To Create In Unity

For each code folder:

```text
Right click folder
→ Create
→ Scripting
→ Assembly Definition
```

Then rename the file:

```text
NY.Core
NY.Runtime
NY.Modules
NY.Editor
NY.Showcase
```

For references:

```text
Click asmdef file
→ Inspector
→ Assembly Definition References
→ Add reference
→ Apply
```

For `NY.Editor`:

```text
Click NY.Editor.asmdef
→ Include Platforms
→ Editor only
→ Apply
```

## Important Rules

Good:

```text
NY.Modules → NY.Core
NY.Modules → NY.Runtime
NY.Showcase → NY.Modules
```

Bad:

```text
NY.Core → NY.Modules
NY.Core → NY.Showcase
NY.Runtime → NY.Editor
```

Core must not know Skill, Tool, UI, or Showcase.

## Portfolio Value

This is useful for the portfolio because it shows:

- modular architecture
- dependency control
- Runtime / Editor separation
- compile boundary awareness
- Unity project structure discipline

Interview explanation:

```text
Unity's default Assembly-CSharp structure is convenient at first, but it makes module boundaries unclear as the project grows.
For this portfolio, I split Core, Runtime, Modules, Editor Tools, and Showcase into separate asmdef assemblies.
Core does not reference upper-level systems, and Editor tools are compiled only for the Unity Editor.
This keeps the runtime architecture clean and makes the dependency direction explicit.
```

## Next Task

Next working session:

1. Create the five asmdef files.
2. Set references according to the dependency direction.
3. Set `NY.Editor` to Editor-only.
4. Reopen / recompile Unity and check Console errors.
5. Commit the Unity project changes after verification.
