# AGENT HANDOFF

이 문서는 다른 Codex / Claude / GPT 세션에 넘기는 최소 전달 문서다.

## 먼저 읽을 문서

1. `CORE.md`
2. `PORTFOLIO_PLAN.md`
3. `DX11_UNITY_MAP.md`
4. `README.md`

## 프로젝트 요약

Unity 기반 클라이언트 시스템 연구 포트폴리오다.

목표는 게임 하나를 완성하는 것이 아니라, DX11 엔진 제작 경험을 Unity에서 재해석하고 클라이언트 구조 설계 능력을 보여주는 것이다.

## 현재 중요한 판단

문서가 너무 많아져서 관리 비용이 증가했다.

따라서 현재는 핵심 문서만 남기고 중복 운영 문서를 제거하는 중이다.

보존해야 할 것은 분석 자산이다.

- DX11 Engine DLL 분석
- DX11 Animation Tool 분석
- Gunfire Reborn Clone 분석
- Unity Technical Showcase 설계 자료

삭제 가능한 것은 중복 운영 문서다.

- 과도한 전략 문서
- 중복 Git 문서
- 중복 Notion 문서
- 중복 Workflow 문서
- 과도한 KPI / Risk / Recruiter / Video 문서

## 현재 우선순위

1. 문서 구조 간소화
2. Unity Core Framework 설계
3. Skill System 설계
4. Skill Tool 최소 구현
5. DX11 -> Unity 연구 주제 연결

## 작업 규칙

문서 작업은 자동 진행한다.

아래 작업은 사용자 확인 후 진행한다.

- 코드 수정
- 코드 생성/삭제
- 커밋
- Push
- ZIP 생성
- Release
- 패키지 설치
- 외부 서비스 연동
- CI/CD 변경

## 로컬 UML

사용자가 로컬에서 보기 위한 UML은 아래에 있다.

```text
C:\kny\plantuml-overview
```

계획이나 구조가 변경되면 관련 PlantUML도 같이 수정한다.

## Next Unity Task

Create asmdef files in the Unity project.

Reference:

```text
projects/unity-technical-showcase/AssemblyDefinitionPlan.md
```

Expected files:

```text
Assets/00_Core/NY.Core.asmdef
Assets/01_Runtime/NY.Runtime.asmdef
Assets/02_Modules/NY.Modules.asmdef
Assets/03_Tools/NY.Editor.asmdef
Assets/04_Showcase/NY.Showcase.asmdef
```

## Career Target Context

Current portfolio direction should prioritize Com2uS / mid-size Unity client positions first.

Reason:

- Current work experience is closer to mobile live service operations.
- Unity portfolio ROI is highest when focused on Skill System, Skill Tool, Addressables, UI, Debug, and Metrics.
- SHIFT UP-style Animation / Rendering / Combat content is useful, but should be a second-layer expansion after the first portfolio version is complete.

Do not over-expand Shader or Rendering early.

First portfolio completion should prove:

```text
data-driven skill architecture
+ planner-usable Unity Editor tool
+ live-service-friendly loading/debug structure
```

## Skill Course Workflow

User is currently learning from the Inflearn modular skill system course in:

```text
C:\kny\Project\Unity\SkillProject
```

This project is a learning / experiment project.

The final portfolio project is:

```text
C:\kny\Project\Unity\UnityTechnicalShowcase
```

Do not implement the final Skill System in TechShowcase before the course structure is completed and analyzed.

Reference:

```text
projects/skill-project/SkillCourseLearningWorkflow.md
```
