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

## Portfolio Master Plan

- Source: `shared/uml/PortfolioMasterPlan.puml`
- Purpose: 전체 프로젝트 관리, 개발 사이클, 전략 계층, MVP 우선순위, 산출물 연결 구조를 한 장으로 요약한다.

## NY Modular Portfolio Framework

- Source: `projects/unity-technical-showcase/framework/uml/NYModularPortfolioFramework.puml`
- Source: `projects/unity-technical-showcase/framework/uml/NYModuleLifecycle.puml`
- Source: `projects/unity-technical-showcase/framework/uml/NYModuleDependencyGraph.puml`
- Purpose: NY Core Framework, Module Hub, Module Registry, Tool Module, Comparable Module, Metrics 흐름을 정의한다.

## Selective Lua Scripting Layer

- Source: `projects/unity-technical-showcase/scripting/uml/SelectiveLuaScriptingLayer.puml`
- Source: `projects/unity-technical-showcase/scripting/uml/LuaSkillFormulaSequence.puml`
- Purpose: C# Core 위에서 Lua를 선택적 Gameplay Logic 확장 포인트로만 사용하는 구조를 정의한다.

## Google Calendar + Notion Schedule

- Source: `notion/GoogleCalendarNotionScheduleWorkflow.puml`
- Purpose: Google Calendar 일정, Notion 개발일지, Codex 일정 검토/수정 흐름을 정의한다.

## Portfolio Automation Strategy

- Source: `workflow/PortfolioAutomationWorkflow.puml`
- Purpose: Architecture Governance Review, Unity CI/CD Pipeline, Weekly Technical Review 자동화 운영 흐름을 정의한다.

## Git Repository Management

- Source: `shared/uml/git/PortfolioGitRepositoryMaster.puml`
- Source: `shared/uml/git/GitPlantUMLIndex.puml`
- Source: `shared/uml/git/PortfolioGitWorkflow.puml`
- Source: `shared/uml/git/ClaudeCodexGitSync.puml`
- Source: `shared/uml/git/GitRepositoryResponsibility.puml`
- Source: `shared/uml/git/GitRemoteConnectionPlan.puml`
- Purpose: 문서 저장소, Unity 프로젝트 저장소, 공개 포트폴리오 사이트 저장소의 역할, remote 연결, Codex/Claude 동기화, 작업 흐름을 정의한다.
