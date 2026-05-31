# MVP Scope Strategy

## Why This Document Exists

The full Unity Technical Showcase plan is directionally correct, but the scope is too wide for the first release.

Skill System, Skill Editor, Animation Tool, Shader Showcase, Optimization Showcase, Rendering Debug View, Markdown docs, PlantUML, and blog series are all valuable. However, trying to complete all of them at once increases the risk of never reaching a polished portfolio milestone.

The first portfolio milestone must be smaller, demonstrable, and interview-ready.

## Final Priority

### MVP 1

The first complete version should focus on:

- Modular Skill System
- Skill Editor
- Technical Showcase Scene
- Markdown Docs
- PlantUML

Goal:

- Prove system design ability.
- Prove Unity Editor tooling ability.
- Prove data-driven runtime architecture.
- Show a working demo scene that an interviewer can understand quickly.

### MVP 2

After MVP 1 is stable:

- Animation Tool
- Animation Event and Skill integration
- Shader Showcase

Goal:

- Connect previous DX11 animation experience to Unity.
- Add visual polish and technical depth.
- Show animation-event-driven skill execution.

### MVP 3

After MVP 2 is stable:

- Optimization Showcase
- Rendering Debug View
- Tistory Blog Series polish

Goal:

- Add performance analysis depth.
- Add rendering debugging credibility.
- Convert accumulated Markdown docs into blog-ready posts.

## First Release Definition

The first public portfolio release is complete when the following are done:

- A character can execute at least 3 modular skills.
- Skills are defined by ScriptableObject data.
- Effects, Targets, Conditions, and Cooldowns are separated.
- Runtime Skill Assembly is visible in logs or debug UI.
- A Skill EditorWindow can create and edit skill data.
- A Validation System can detect invalid skill data.
- A Technical Showcase Scene demonstrates the system.
- Markdown docs explain the concept, architecture, and implementation.
- PlantUML diagrams explain structure and execution flow.
- Before / After examples show why the architecture matters.

## What Not To Do In MVP 1

Do not spend MVP 1 time on:

- Full RPG content
- Large map design
- Full animation editor
- Large shader library
- Full optimization dashboard
- Complex rendering debugger
- Large blog series polish

These can come later. MVP 1 must finish.

## MVP 1 Feature List

### Skill Runtime

Required:

- `SkillDefinitionSO`
- `EffectDefinitionSO`
- `TargetingDefinitionSO`
- `ConditionDefinitionSO`
- `CooldownDefinitionSO`
- `SkillFactory`
- `SkillInstance`
- `SkillController`
- Runtime execution log

### Skill Editor

Required:

- Skill list panel
- Skill creation
- Effect add/remove
- Target setting
- Condition setting
- Cooldown setting
- Save/load through Unity assets
- Validation panel

### Technical Showcase Scene

Required:

- Character
- Enemy dummy
- Skill selection panel
- Skill inspector panel
- Execution log
- Event timeline or simple runtime log
- Debug overlay

### Documentation

Required:

- Concept document
- Mini experiment document
- Architecture document
- Implementation document
- Blog draft
- Interview summary
- PlantUML diagrams

## Risk Control

If development slows down, reduce skill count before reducing architecture quality.

Keep:

- Data-driven design
- Module separation
- Editor validation
- Showcase scene clarity

Reduce first:

- Number of skills
- Visual effects
- Animation complexity
- UI polish
- Blog polish
