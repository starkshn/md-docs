# Blog And Portfolio Publishing Workflow

This document describes how to reuse the Markdown and PlantUML documentation for a technical blog and a portfolio website.

## Source Of Truth

The source files are managed in:

```text
C:\kny\Project\포트폴리오\technical-portfolio-docs
```

Do not write separate versions of the same technical explanation in the blog repository and the portfolio repository. Instead, copy, transform, or import from this documentation workspace.

## Target Outputs

The same source documents can become:

- GitHub README sections
- Blog articles
- Portfolio project pages
- Interview preparation notes
- PDF portfolio extracts
- PlantUML diagram images

## Recommended Publishing Pipeline

```text
Markdown source
-> PlantUML source
-> Export PNG/SVG diagrams
-> Add project screenshots/GIFs
-> Publish blog article
-> Publish portfolio summary page
-> Link back to detailed docs
```

## Blog Article Format

Recommended structure:

```md
# Title

## Problem
## Context
## Architecture
## Implementation Details
## Trade-offs
## What I Would Improve
## Result
## Related Links
```

Blog posts should be narrower than project documents. A good blog post explains one technical decision or one system.

## Portfolio Page Format

Recommended structure:

```md
# Project Name

## One-Line Summary
## My Role
## Core Technical Highlights
## Architecture Diagram
## Demo Media
## Key Challenges
## Result
## Links
```

A portfolio page should be shorter than a blog post. It should make the value visible quickly.

## PlantUML Export Guideline

Keep `.puml` files in the project folder. Exported images can be generated later into a website asset folder.

Recommended output layout for a static site:

```text
public/assets/diagrams/
  dx11-gunfire-reborn/
  dx11-animation-tool/
  common-engine-dll/
  unity-technical-showcase/
```

## Suggested Blog Series

1. DX11 Game Framework Architecture
2. Prototype-Based Object Creation Pipeline
3. DirectX 11 Deferred Rendering With MRT
4. Animation Tool: Bone, Channel, KeyFrame, Event
5. Unity Skill System: Data-Driven Runtime Assembly
6. Unity Skill Editor: Tooling For Designers
7. Unity Optimization Showcase: Measuring Before Optimizing

## Portfolio Integration Strategy

Use the Unity Technical Showcase as the main portfolio project. Use the DX11 projects as proof of low-level understanding.

Recommended portfolio hierarchy:

```text
Main Portfolio Project
  Unity Technical Showcase
Supporting Technical Background
  DX11 Game Framework
  DX11 Animation Tool
  Gunfire Reborn Clone
```

This makes the portfolio easier to understand for Unity-focused hiring while still preserving the value of the DirectX engine work.
