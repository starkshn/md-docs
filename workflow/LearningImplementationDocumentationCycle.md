# Learning Implementation Documentation Cycle

This workflow defines the required cycle for every portfolio feature.

## Step 1. Concept Study

Before implementation, document the required concepts.

Questions:

- Why is this feature needed?
- Which Unity APIs are involved?
- How was a similar concept handled in DX11 or Unreal?
- What problems happen in production?
- Which design pattern or architecture fits this feature?

Output:

- Concept summary
- Unity API notes
- DX11 / Unreal comparison
- Design decision notes

## Step 2. Mini Experiment

Do not integrate directly into the main portfolio scene. First, prove the concept in a small test scene.

Examples:

- Create one SkillDefinition ScriptableObject
- Output one camera to RenderTexture
- Compare LOD on/off
- Implement one shader in isolation
- Play one clip with PlayableGraph

Output:

- Test scene
- Minimal code
- Screenshot or GIF
- Notes about what worked and what failed

## Step 3. Portfolio Integration

Only verified experiments are integrated into the main Unity Technical Showcase.

Checkpoints:

- Module dependency
- Assembly Definition boundary
- Interface separation
- Data structure
- Extensibility
- Runtime performance impact
- Debug UI visibility

Output:

- Integrated runtime feature
- Editor or debug control
- Demo scene interaction

## Step 4. Documentation

After implementation, update GitHub docs.

Required sections:

- Concept summary
- Design intent
- UML
- Core code structure
- Problem-solving process
- Performance result if relevant
- Improvement plan

Output:

- Markdown technical document
- PlantUML diagram
- Updated project README

## Step 5. Tistory Blog Draft

Write a blog draft based on the Markdown document.

Blog structure:

1. Why I studied this concept
2. Concept explanation
3. How Unity handles it
4. Comparison with DX11 / Unreal experience
5. Actual implementation structure
6. Problems and solutions
7. Result
8. Lessons learned and improvement plan

Output:

- Tistory-ready draft
- Diagram image plan
- Screenshot/GIF checklist

## Step 6. Interview Summary

Condense the feature into interview talking points.

Output:

- 3-line summary
- Architecture explanation
- Trade-off explanation
- Failure or limitation explanation
- Improvement direction
