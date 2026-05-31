# Diagram Source Map

This file maps Markdown source documents to PlantUML diagrams. Markdown is the source of truth; PlantUML should be updated after the relevant Markdown changes.

## Common Engine DLL

| Markdown | PlantUML |
|---|---|
| `projects/common-engine-dll/EngineArchitecture.md` | `projects/common-engine-dll/uml/EngineStructure.puml` |
| `projects/common-engine-dll/EngineArchitecture.md` | `projects/common-engine-dll/uml/ManagerStructure.puml` |
| `projects/common-engine-dll/EngineArchitecture.md` | `projects/common-engine-dll/uml/GameObjectStructure.puml` |
| `projects/common-engine-dll/EngineArchitecture.md` | `projects/common-engine-dll/uml/ComponentStructure.puml` |
| `projects/common-engine-dll/ResourceSystem.md` | `projects/common-engine-dll/uml/ObjectCreationSequence.puml` |

## DX11 Gunfire Reborn Clone

| Markdown | PlantUML |
|---|---|
| `projects/dx11-gunfire-reborn/RenderingPipeline.md` | `projects/dx11-gunfire-reborn/uml/RenderingSequence.puml` |
| `projects/dx11-gunfire-reborn/ProjectAnalysis.md` | `projects/dx11-gunfire-reborn/uml/PackageStructure.puml` |

## DX11 Animation Tool

| Markdown | PlantUML |
|---|---|
| `projects/dx11-animation-tool/AnimationSystem.md` | `projects/dx11-animation-tool/uml/AnimationPlaybackSequence.puml` |

## Unity Technical Showcase

| Markdown | PlantUML |
|---|---|
| `projects/unity-technical-showcase/ArchitectureDesign.md` | `projects/unity-technical-showcase/uml/UnityPortfolioArchitecture.puml` |
| `projects/unity-technical-showcase/ArchitectureDesign.md` | `projects/unity-technical-showcase/uml/SkillExecutionSequence.puml` |
| `projects/unity-technical-showcase/DevelopmentRoadmap.md` | `projects/unity-technical-showcase/uml/UnityWorkflow.puml` |

## Update Rule

When a Markdown file changes:

1. Check this map.
2. Update the mapped PlantUML files.
3. Export diagram images only after the `.puml` source is reviewed.
4. Update links in the project `README.md` if diagram names changed.
