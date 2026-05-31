# Naming Convention

## 최종 규칙

Unity Technical Showcase의 프로젝트 고유 타입은 다음 규칙을 따른다.

```text
NY_Category_Role
```

이 규칙은 일반 C# 컨벤션보다 검색성, 모듈 추적성, 포트폴리오 설명 가능성을 우선한 프로젝트 컨벤션이다.

## 예시

```text
NY_Core_ModuleHub
NY_Core_ModuleRegistry
NY_Core_ModuleContext

NY_Skill_SystemModule
NY_Skill_EditorModule
NY_Skill_ValidationModule
NY_Skill_Factory
NY_Skill_Controller
NY_Skill_DefinitionSO

NY_Animation_PreviewModule
NY_Animation_EventModule

NY_Shader_ShowcaseModule
NY_Shader_DissolveModule

NY_Optimization_PoolingModule
NY_Optimization_LODModule

NY_RenderingDebug_DepthViewModule
NY_RenderingDebug_NormalViewModule

NY_Comparison_ViewSystem
NY_Tool_ModuleDashboard
```

## Interface

```text
INY_Module
INY_ToolModule
INY_ComparableModule
INY_SkillEffect
INY_TargetResolver
INY_SkillCondition
```

## Enum

```text
ENY_ModuleState
ENY_ModuleCategory
ENY_ComparisonMode
ENY_SkillTargetType
```

## Event

```text
NYE_SkillActivated
NYE_SkillFinished
NYE_ModuleEnabled
NYE_ModuleDisabled
```

## ScriptableObject

```text
NY_Skill_DefinitionSO
NY_Skill_EffectDefinitionSO
NY_Skill_TargetDefinitionSO
NY_Shader_ProfileSO
NY_Optimization_ConfigSO
```

## 금지 예시

```text
NY_Module_Manager
NY_Skill_System
NY_Animation_Tool
NY_Skill_System_Module
```

## Codex 규칙

Codex는 새 클래스를 만들기 전에 이 문서를 먼저 확인한다. 클래스명만 보고 카테고리, 역할, 데이터/툴/모듈 여부가 드러나야 한다.
