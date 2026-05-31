# Before After Demonstration Rule

## Why Before / After Matters

Technical ability is easier to understand when the improvement is visible.

A portfolio feature should not only say:

- I implemented a system.

It should show:

- What was the naive or hardcoded approach?
- What problem did it create?
- What changed after the new architecture?
- Why is the new approach better?

## Required Before / After Examples

### Skill System

Before:

- Hardcoded skill class
- Targeting, cooldown, condition, and effect mixed in one class
- New skill requires new code branch or class duplication

After:

- Skill data is defined by ScriptableObject
- Target, Condition, Effect, and Cooldown are separate modules
- Runtime Skill Assembly creates executable skill instances
- New skill can be created by combining modules

Proof:

- Show two skills sharing the same Effect but different Targeting
- Show one skill changing cooldown without code change
- Show runtime log of module execution order

### Skill Editor

Before:

- Skill data edited manually in Inspector or code
- Invalid combinations are discovered only at runtime

After:

- EditorWindow creates and edits skill assets
- Validation catches missing Effect, invalid Target, negative Cooldown, etc.

Proof:

- Create invalid skill and show validation warning
- Fix it and show successful runtime execution

### Animation Tool

Before:

- Animator plays clips without detailed preview/debugging
- Events are hard to inspect in runtime context

After:

- Playables-based preview
- Bone viewer
- Animation Event to Skill bridge

Proof:

- Show clip blend
- Show event marker triggering skill impact

### Shader Showcase

Before:

- Default Material only

After:

- Rim Light, Dissolve, Outline, Fresnel, Toon, Distortion variants

Proof:

- Toggle base material vs shader effect
- Show exposed parameters

### Optimization Showcase

Before:

- No pooling
- Many allocations and frame spikes

After:

- Object Pooling
- Reduced GC allocation
- More stable frame time

Proof:

- Show Profiler metrics or runtime metric overlay
- Toggle Pooling ON/OFF

### Rendering Debug View

Before:

- Only final camera output

After:

- Main View, Depth View, Normal View, Overdraw View, RenderTexture View

Proof:

- Show multiple debug views in the showcase scene

## Required Document Per Feature

Each feature must have:

```text
07_BeforeAfter.md
```

It must include:

- Before state
- After state
- Technical difference
- Proof method
- Demo checklist
- Screenshot/GIF checklist

## Rule

If there is no Before / After, the feature is not ready for portfolio presentation.
