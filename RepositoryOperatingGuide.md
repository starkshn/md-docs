# Repository Operating Guide

## Purpose

This repository is designed to be shared with AI assistants such as Claude, GPT, or Codex while building a Unity Technical Showcase portfolio.

## How To Use With Claude

1. Open this repository as the working context.
2. Read `CLAUDE.md` first.
3. Read `PortfolioStudyMasterPlanForGPT.md` second.
4. For feature-specific work, open the matching folder under `projects/unity-technical-showcase`.
5. Update Markdown before PlantUML.

## Recommended Prompt

```text
Read CLAUDE.md and PortfolioStudyMasterPlanForGPT.md first.
Based on this documentation workspace, help me plan the next Unity Technical Showcase feature.
For the selected feature, produce:
- concepts to study
- Unity API analysis
- DX11 / Unreal comparison
- mini experiment plan
- implementation plan
- Markdown document draft
- Tistory blog draft
- PlantUML diagram
- interview talking points
```

## Git Workflow

Use small commits by documentation topic.

Examples:

```text
docs: add skill system learning plan
docs: add animation tool blog roadmap
docs: update PlantUML source map
docs: add optimization mini experiment plan
```

## Source Of Truth

- Markdown first
- PlantUML second
- Exported images later
- Blog/portfolio pages last
