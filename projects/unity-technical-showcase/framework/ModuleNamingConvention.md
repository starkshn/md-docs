# Module Naming Convention

## 최종 추천

이 프로젝트는 일반적인 C# 컨벤션만 따르기보다 포트폴리오 운영 목적, 검색성, 모듈 추적성을 우선한다.

최종 클래스 네이밍은 다음 규칙을 사용한다.

```text
NY_Category_Role
```

예시:

```text
NY_Core_ModuleHub
NY_Skill_SystemModule
NY_Skill_DefinitionSO
NY_Animation_PreviewModule
NY_Shader_DissolveModule
NY_Optimization_PoolingModule
NY_RenderingDebug_DepthViewModule
NY_Comparison_ViewSystem
NY_Tool_ModuleDashboard
```

## 왜 일반 C# 방식이 아닌가

일반 C# 관점에서는 `NYSkillSystemModule`처럼 PascalCase만 사용하는 방식이 더 자연스럽다. 그러나 이 포트폴리오는 다음 목적을 가진다.

- 혼자 개발하면서 빠르게 검색해야 한다.
- 모듈 카테고리를 클래스명만 보고 알아야 한다.
- Notion, Blog, Docs, PlantUML에서 모듈을 추적해야 한다.
- 포트폴리오가 “모듈형 기술 쇼케이스 프레임워크”로 보여야 한다.

따라서 클래스명에 `_`를 허용한다. 단, 무분별하게 쓰지 않고 `NY_Category_Role` 구조로만 사용한다.

## Prefix

모든 프로젝트 고유 타입은 `NY_`로 시작한다.

## Category

허용 카테고리:

- Core
- Skill
- Animation
- Shader
- Optimization
- RenderingDebug
- Comparison
- Tool
- Metrics
- Editor
- Documentation

## Role

허용 Role 예시:

- Module
- SystemModule
- EditorModule
- ToolModule
- Factory
- Registry
- Context
- Service
- Controller
- Presenter
- View
- ViewSystem
- Dashboard
- Descriptor
- Metrics
- Data
- ConfigSO
- DefinitionSO

## Interface

인터페이스는 `I` + `NY_` + Role 구조를 사용한다.

```text
INY_Module
INY_ToolModule
INY_ComparableModule
INY_SkillEffect
INY_TargetResolver
INY_SkillCondition
```

## Enum

Enum은 `ENY_` Prefix를 사용한다.

```text
ENY_ModuleState
ENY_ModuleCategory
ENY_ComparisonMode
ENY_SkillTargetType
```

## Event

Event payload 또는 event type은 `NYE_` Prefix를 사용한다.

```text
NYE_SkillActivated
NYE_SkillFinished
NYE_ModuleEnabled
NYE_ModuleDisabled
```

## ScriptableObject

ScriptableObject는 `SO` suffix를 사용한다.

```text
NY_Skill_DefinitionSO
NY_Skill_EffectDefinitionSO
NY_Skill_TargetDefinitionSO
NY_Shader_ProfileSO
NY_Optimization_ConfigSO
```

## 파일 탐색 규칙

폴더와 네임스페이스로 1차 구분하고, 클래스명으로 2차 구분한다.

```text
Assets/_Project/Modules/Skill/Runtime/NY_Skill_SystemModule.cs
Assets/_Project/Modules/Skill/Editor/NY_Skill_EditorModule.cs
Assets/_Project/Modules/Shader/Runtime/NY_Shader_DissolveModule.cs
```

## 금지 규칙

다음 형식은 사용하지 않는다.

```text
NY_Module_Manager
NY_Skill_System
NY_Animation_Tool
NY_Skill_System_Module
```

이유:

- Role 위치가 일정하지 않다.
- `Module` 의미가 불명확하다.
- 검색성은 있지만 구조적 의미가 약하다.
- 클래스명이 과도하게 길어진다.

## 클래스명만 보고 알 수 있어야 하는 것

새 클래스명은 다음 정보를 드러내야 한다.

1. 어떤 카테고리인가
2. Runtime / Editor / Data / Tool 중 어디에 가까운가
3. Module인가 Tool인가
4. Factory인가 Service인가
5. ScriptableObject인가

예시:

```text
NY_Skill_SystemModule
```

- Skill 카테고리
- Runtime 기능
- Module

```text
NY_Skill_DefinitionSO
```

- Skill 카테고리
- Data
- ScriptableObject

```text
NY_Tool_ModuleDashboard
```

- Tool 카테고리
- Editor Tool
- Dashboard
