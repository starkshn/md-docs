# Technical Showcase Scene Design

## Goal

The portfolio must be centered around a Technical Showcase Scene, not a list of isolated features.

An interviewer will not read all code first. The first question is:

- What is visible when the project runs?
- Can the technical value be understood in a few minutes?
- Can the user interact with the systems?

Therefore the showcase scene must work like a technical dashboard.

## Layout

```text
+--------------------------------------------------------------------------------+
| Top Bar: Main View | Debug View | RenderTexture View | Reset | Capture         |
+----------------------+--------------------------------------+------------------+
| Left Panel           | Center View                          | Right Panel      |
| Feature Selection    | Character / Combat Demo              | Inspector        |
|                      |                                      |                  |
| - Skill System       | - Character                          | Skill Inspector  |
| - Skill Editor       | - Enemy Dummy                        | Animation Panel  |
| - Animation Tool     | - Skill Runtime Preview              | Shader Options   |
| - Shader Showcase    | - VFX Preview                        | Optimization     |
| - Optimization       |                                      | Debug Options    |
| - Debug View         |                                      |                  |
+----------------------+--------------------------------------+------------------+
| Bottom Panel: Runtime Log | Performance Metrics | Event Timeline              |
+--------------------------------------------------------------------------------+
```

## MVP 1 Layout

For MVP 1, only these panels are required:

### Left Panel

- Skill list
- Skill category filter
- Selected skill display

### Center View

- Character
- Enemy dummy
- Skill cast preview
- Basic hit/effect feedback

### Right Panel

- Skill Inspector
- Target module display
- Effect module display
- Condition module display
- Cooldown display

### Bottom Panel

- Runtime execution log
- Skill event log
- Cooldown log
- Validation warnings

### Top Bar

- Main View
- Reset Scene
- Toggle Debug Overlay

## MVP 2 Extensions

- Animation preview panel
- Animation event timeline
- Shader parameter panel
- VFX preview selector

## MVP 3 Extensions

- Performance metrics
- Pooling ON/OFF
- LOD/Culling ON/OFF
- RenderTexture multi view
- Depth/Normal/Overdraw debug views

## Scene Design Rule

Every feature must answer this question in the scene:

> What changed compared to the naive implementation?

If the scene cannot show the difference, the feature is not portfolio-ready.

## Showcase Interaction Flow

1. User selects a skill from the left panel.
2. Right panel displays skill modules.
3. User presses execute or input hotkey.
4. Character casts skill in center view.
5. Bottom log shows condition check, target resolve, effect apply, cooldown consume.
6. Before / After toggle shows hardcoded vs modular execution if available.

## Interviewer-Friendly Demo Flow

The first 3 minutes should show:

1. Open Showcase Scene.
2. Select a skill.
3. Show that skill is assembled from data modules.
4. Execute skill.
5. Modify effect or cooldown in editor.
6. Re-run and show changed behavior.
7. Open Markdown/PlantUML briefly to show documentation discipline.

## Implementation Priority

Do not build all UI at once.

Build in this order:

1. Runtime log panel
2. Skill selection panel
3. Skill inspector panel
4. Character / enemy demo area
5. Debug overlay
6. Before / After toggle
7. Visual polish
