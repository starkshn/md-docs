# Feature Documentation Template

Every feature folder must follow this structure.

```text
<feature-name>/
  00_README.md
  01_Concept.md
  02_MiniExperiment.md
  03_Architecture.md
  04_Implementation.md
  05_BlogDraft.md
  06_Interview.md
  07_BeforeAfter.md
  uml/
```

## File Purpose

### 00_README.md

Feature index.

Must include:

- Feature goal
- Current status
- Related documents
- Related UML
- MVP priority

### 01_Concept.md

Concept study document.

Must include:

- Why this feature is needed
- Core concepts
- Unity API analysis
- DX11 / Unreal comparison
- Practical production problems

### 02_MiniExperiment.md

Small experiment plan before main integration.

Must include:

- Experiment goal
- Test scene name
- Minimal implementation scope
- Expected result
- Failure criteria
- Screenshot/GIF checklist

### 03_Architecture.md

Architecture decision document.

Must include:

- Module responsibility
- Dependency direction
- Assembly Definition plan
- Data structure
- Runtime flow
- PlantUML links

### 04_Implementation.md

Implementation record.

Must include:

- Main classes
- Main interfaces
- Key code flow
- Problems encountered
- Solutions
- Remaining technical debt

### 05_BlogDraft.md

Tistory blog draft.

Must follow this structure:

1. Why I studied this concept
2. Concept explanation
3. Unity implementation approach
4. DX11 / Unreal comparison
5. Actual implementation structure
6. Problems and solutions
7. Result
8. Lessons learned and improvement plan

### 06_Interview.md

Interview explanation document.

Must include:

- 3-line summary
- Architecture explanation
- Trade-offs
- Failure cases
- Improvement direction
- Expected interview questions

### 07_BeforeAfter.md

Before / After demonstration document.

Must include:

- Before state
- After state
- What changed technically
- Why the change matters
- Visual or measurable proof
- Demo checklist

## Required Rule

Markdown first. PlantUML second. Implementation third only after a mini experiment is validated.
