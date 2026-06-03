# Unity Technical Showcase Architecture

## Goal

Unity 기반 단일 프로젝트에서 클라이언트 시스템 설계 능력과 엔진 개념 이해도를 보여준다.

## Core Structure

```text
Unity Technical Showcase
├─ Core Framework
├─ ModuleHub
├─ Skill System
├─ Skill Tool
├─ Debug / Metrics View
├─ Before / After View
└─ DX11 Concept Research
```

## Module Principles

- 기능은 Module 단위로 분리한다.
- Runtime과 Editor 의존성을 분리한다.
- ScriptableObject는 데이터 원본으로 사용한다.
- Runtime 객체는 Factory / Instance 구조로 생성한다.
- Debug UI는 기능 검증과 면접 시연을 위한 도구로 사용한다.

## MVP Architecture

### Core Framework

- Module registration
- Lifecycle management
- Shared event channel
- Debug logging

### Skill System

- SkillDefinitionSO
- SkillFactory
- SkillInstance
- Target / Condition / Effect 분리
- Cooldown
- Runtime Assembly

### Skill Tool

- EditorWindow 기반 최소 툴
- Skill 데이터 생성
- Validation
- Save / Load

### Debug View

- Feature Toggle
- Metrics
- Before / After 비교
- RenderTexture 기반 확장 후보

## DX11 Connection

자세한 연결은 루트의 `DX11_UNITY_MAP.md`를 따른다.
