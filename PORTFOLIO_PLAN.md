# PORTFOLIO PLAN

## 한 줄 정의

Unity 기반 클라이언트 시스템 연구 프로젝트를 통해 게임 클라이언트 개발 역량과 엔진 시스템 이해도를 보여주는 장기 포트폴리오 프로젝트.

## 프로젝트 성격

이 프로젝트는 하나의 Unity 프로젝트로 관리한다.

목적은 3개다.

1. 포트폴리오용
2. 연구용
3. 개발 학습용

게임 하나를 완성하는 것이 아니라, 클라이언트 시스템 구조와 엔진 개념 이해도를 보여주는 것이 목표다.

## 핵심 방향

DX11에서 직접 구현했던 엔진 개념을 Unity에서 다시 해석한다.

중점 연구 주제:

- Rendering Pipeline
- Animation System
- Resource Management
- Scene Management
- State Machine
- Object Pooling
- Event System
- Tool Framework
- Debug Framework
- Data Pipeline
- Runtime Architecture

## MVP 범위

### MVP 1: Core + Skill

목표: 가장 먼저 시연 가능한 기술 구조를 만든다.

포함:

- Core Framework
- ModuleHub
- Skill System
- Skill Tool 최소 버전
- Data Driven Skill
- Before / After 비교 최소 버전

### MVP 2: Tool + Debug

목표: 면접관이 실행해서 구조를 볼 수 있는 대시보드를 만든다.

포함:

- Showcase Scene
- Debug Panel
- Metrics Panel
- Feature Toggle
- 간단한 RenderTexture Debug View

### MVP 3: DX11 개념 재해석

목표: 기존 엔진 경험을 Unity 개념으로 연결한다.

포함 후보:

- Animation Preview
- Bone Viewer
- Playables 기반 Animation 실험
- Shader / Render Debug 실험
- Resource Loading 실험
- Object Pooling 실험

### MVP 4: 포트폴리오 정리

목표: 결과물을 설명 가능한 형태로 정리한다.

포함:

- README
- 핵심 설계 문서
- PlantUML
- 기술 블로그 초안
- 면접 설명 포인트
- 간단한 시연 영상 후보

## 후순위 기능

아래 기능은 Skill System과 Tool 구조가 안정화된 후 진행한다.

- Selective Lua Scripting Layer
- Shader Showcase 전체 구성
- Optimization Showcase 전체 구성
- Rendering Debug View 확장
- CI/CD
- Addressables 심화

## 제외 범위

초기에는 아래를 하지 않는다.

- 서버
- DB
- 로그인
- 매칭
- 멀티플레이
- 인벤토리 대규모 시스템
- 퀘스트 시스템
- DOTS / ECS
- 과도한 콘텐츠 제작

## 개발 사이클

각 기능은 아래 흐름을 따른다.

```text
개념 학습
↓
미니 실험
↓
Unity 통합
↓
문서 정리
↓
PlantUML 갱신
↓
면접 설명 포인트 정리
```

블로그는 모든 기능에 대해 강제로 쓰지 않는다.

기술적으로 설명 가치가 있는 주제만 작성한다.

## 성공 기준

완성 기준은 기능 개수가 아니다.

아래 질문에 답할 수 있으면 성공이다.

- 어떤 개념을 공부했는가?
- 왜 이 구조가 필요한가?
- DX11에서는 어떻게 구현했는가?
- Unity에서는 어떻게 다르게 처리하는가?
- 어떤 문제를 발견했는가?
- 어떤 구조로 해결했는가?
- 면접에서 무엇을 증명할 수 있는가?

## 현재 우선순위

1. 문서 구조 간소화
2. Core Framework 설계
3. Skill System 설계
4. Skill Tool 최소 구현
5. Showcase Scene 구성
6. DX11 -> Unity 연구 주제 연결

## Next Technical Concept: Assembly Definition

Next Unity task is to create asmdef files for the current folder structure.

Reference document:

```text
projects/unity-technical-showcase/AssemblyDefinitionPlan.md
```

Planned assemblies:

```text
NY.Core
NY.Runtime
NY.Modules
NY.Editor
NY.Showcase
```

Goal:

- separate Core / Runtime / Modules / Editor / Showcase boundaries
- prevent wrong dependency direction
- keep Editor code out of runtime builds
- make the portfolio architecture explainable in interviews
