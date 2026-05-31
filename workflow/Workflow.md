# Documentation Workflow

This workflow defines how the technical portfolio documentation should be written, updated, reviewed, and published.

## Goal

The goal is to maintain one clean documentation source that can be reused across:

- GitHub repositories
- Technical blog posts
- Portfolio website pages
- Interview preparation notes
- PlantUML architecture diagrams

Markdown is the source of truth. PlantUML diagrams are derived from the Markdown architecture descriptions.

## Principles

1. One project, one folder.
2. One major topic, one Markdown file.
3. One diagram, one PlantUML file.
4. Markdown explains intent and trade-offs.
5. PlantUML explains structure and runtime flow.
6. Blog posts should be generated from polished Markdown, not from raw notes.
7. Portfolio pages should summarize the Markdown and link back to deeper technical documents.

## Standard Project Folder

Each project should follow this structure:

```text
projects/<project-name>/
  README.md                  # Short index for the project
  ProjectAnalysis.md          # Project overview, purpose, feature summary
  Architecture.md             # Runtime/module architecture if needed
  RenderingPipeline.md        # Rendering-specific analysis if needed
  AnimationSystem.md          # Animation-specific analysis if needed
  ResourceSystem.md           # Resource/loading system if needed
  DesignPatterns.md           # Pattern analysis if project-specific
  PerformanceOptimization.md  # Optimization notes if project-specific
  LessonsLearned.md           # What should be improved in the next project
  uml/
    ClassDiagram.puml
    SequenceDiagram.puml
    PackageDiagram.puml
```

Use only the files that are meaningful for the project. Do not create empty documents just to fill the template.

## Writing Process

### Step 1: Collect Evidence

Use source code, screenshots, videos, profiler captures, and commit history as evidence.

Recommended evidence:

- Important class names
- Module boundaries
- Runtime flow
- Tool screenshots
- Before/after performance numbers
- Known limitations
- Refactoring ideas

### Step 2: Write Technical Markdown

Each document should answer:

- What problem does this system solve?
- Why was it designed this way?
- Which modules own which responsibilities?
- What are the dependencies?
- What trade-offs exist?
- What would be improved in a production version?

### Step 3: Create PlantUML From Markdown

After the Markdown is stable, create diagrams from it.

Use these diagram types:

- Class diagram: static structure
- Sequence diagram: runtime flow
- Package diagram: module boundaries
- Component diagram: Unity assembly/module relationships
- Activity diagram: workflow or pipeline

### Step 4: Cross-Link Documents

Every project `README.md` should link to its Markdown files and UML files.

Use relative links:

```md
[Rendering Pipeline](RenderingPipeline.md)
[Rendering Sequence](uml/RenderingSequence.puml)
```

### Step 5: Review For Portfolio Quality

Before publishing, check:

- Can a recruiter understand the project in 30 seconds?
- Can an engineer understand the architecture in 5 minutes?
- Are claims backed by implementation details?
- Are diagrams consistent with the Markdown?
- Are limitations written honestly?

## Diagram Naming Rules

Use clear English names:

```text
EngineStructure.puml
ObjectCreationSequence.puml
RenderingSequence.puml
AnimationPlaybackSequence.puml
SkillExecutionSequence.puml
UnityPortfolioArchitecture.puml
```

Avoid vague names:

```text
diagram1.puml
new.puml
test.puml
architecture_final_final.puml
```

## Blog Conversion Workflow

1. Pick one Markdown document.
2. Rewrite the introduction for readers who do not know the project.
3. Keep deep implementation details in collapsible sections or linked documents.
4. Export PlantUML diagrams as PNG/SVG.
5. Add screenshots or GIFs from the project.
6. Publish as a focused article.

Recommended article series:

- Building a DX11 Component-Based Game Framework
- Designing a Prototype-Based Object Creation Pipeline
- Implementing a Deferred Renderer With MRT
- Building a DX11 Animation Tool With Bone and Event Debugging
- Translating DX11 Engine Experience Into a Unity Technical Showcase

## Portfolio Page Workflow

1. Start from the project `README.md`.
2. Reduce it to problem, role, core systems, and outcome.
3. Add one architecture diagram.
4. Add one short demo video or GIF.
5. Link to the full Markdown documents.
6. Link to the source repository if public.

## Update Cycle

Use this cycle whenever a project changes:

```text
Code change
-> Update Markdown
-> Update PlantUML
-> Export diagram image if needed
-> Update project README
-> Update blog/portfolio index
```

## Done Criteria

A documentation update is done when:

- The project README links to every important document.
- Markdown and PlantUML are in the correct project folder.
- The diagram names are stable.
- There are no broken relative links.
- The document can be reused in both GitHub and blog contexts.
