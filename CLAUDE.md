# CLAUDE.md

This repository is the source-of-truth documentation workspace for a Unity Technical Showcase portfolio.

## Primary Goal

Help build a portfolio that proves game client engineering ability through systems, tools, rendering, optimization, documentation, and blog-ready explanations.

The final portfolio is not a generic game project. It is a Unity Technical Showcase that connects:

- Unity runtime systems
- Unity editor tools
- DX11 engine experience
- Unreal experience
- Markdown technical documentation
- PlantUML diagrams
- Tistory blog drafts
- Interview talking points

## Most Important File

Start here:

- `PortfolioStudyMasterPlanForGPT.md`

This file summarizes the full learning and implementation strategy.

## Documentation Rule

Markdown is the source of truth. PlantUML diagrams are derived from Markdown.

When updating a feature:

1. Update concept notes in Markdown.
2. Update mini experiment plan.
3. Update implementation plan.
4. Update PlantUML.
5. Update blog draft topics.
6. Update interview talking points.

## Folder Structure

```text
projects/
  dx11-gunfire-reborn/
  dx11-animation-tool/
  common-engine-dll/
  unity-technical-showcase/
workflow/
shared/
```

## Expected Assistance

When asked to help with a feature, produce these outputs together:

- Concepts to study
- Concept explanations
- Unity API analysis
- DX11 / Unreal comparison
- Mini experiment plan
- Implementation plan
- Markdown document draft
- Tistory blog draft
- PlantUML diagram
- Interview explanation points

## Writing Style

- Prefer clear technical Korean for user-facing notes.
- Use English file names and folder names.
- Keep Markdown reusable for GitHub, portfolio website, and Tistory.
- Be honest about limitations and improvement plans.
- Avoid vague claims; connect claims to implementation evidence.

## Current Portfolio Direction

Main project:

- Unity Technical Showcase

Supporting projects:

- DX11 Gunfire Reborn Clone
- DX11 Animation Tool
- Common Engine DLL

Core showcase modules:

- Modular Skill System
- Skill Editor
- Animation Tool
- Shader Showcase
- Optimization Showcase
- Rendering Debug View

## Mandatory Learning-Based Development Rule

This portfolio must not be treated as a simple implementation task. Every meaningful feature must produce code, Git commits, Markdown docs, PlantUML, Tistory blog draft, Notion journal entry, and interview notes.

A feature is not considered complete until the following cycle is done:

```text
Concept Study -> Architecture Design -> Mini Experiment -> Implementation -> Verification -> Git Commit -> Markdown Documentation -> PlantUML Update -> Tistory Blog Draft -> Notion Development Journal -> Interview Notes
```

When continuing this project, always preserve the learning narrative: what was studied, why it matters, how Unity applies it, how it connects to DX11/Unreal experience, what was redesigned from lecture material, and why the final structure is stronger than a normal portfolio implementation.

## Strategy Layer Rule

Before adding or implementing any feature, check KPI, Backlog, Risk, DX11-to-Unity Mapping, Demo Video Plan, and Recruiter Mode.

The highest-priority question is:

```text
How does this feature differentiate this portfolio from a normal Unity portfolio?
```

If the feature cannot answer that question, do not add it. Keep server, DB, login, matchmaking, ECS, and DOTS out of scope for this portfolio unless the user explicitly changes the strategy.
