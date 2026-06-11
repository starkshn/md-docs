# CORE

이 문서는 다른 Codex / Claude / GPT 세션이 공통으로 따라야 하는 단일 기준 문서다.

## 최종 목표

Unity 기반 클라이언트 시스템 연구 프로젝트를 통해 게임 클라이언트 개발 역량과 엔진 시스템 이해도를 보여주는 장기 포트폴리오 프로젝트.

## 현재 관리 원칙

관리 구조는 4개만 유지한다.

1. Unity Project: 실제 구현과 실험
2. Documentation: 설계 이유와 학습 기록
3. Git Repository: 문서 / 코드 / 블로그 저장소 분리
4. Schedule Journal: 일정과 개발 일지

## 세션 시작 시 읽는 문서

기본적으로 아래 4개만 읽는다.

1. `CORE.md`
2. `PORTFOLIO_PLAN.md`
3. `DX11_UNITY_MAP.md`
4. `AGENT_HANDOFF.md`

프로젝트 상세 분석이 필요할 때만 `projects/` 아래 문서를 읽는다.

## 보존해야 하는 분석 자료

아래 자료는 삭제하지 않는다.

- `projects/common-engine-dll/`
- `projects/dx11-animation-tool/`
- `projects/dx11-gunfire-reborn/`
- `projects/unity-technical-showcase/`
- 위 폴더 안의 Markdown 분석 문서
- 위 폴더 안의 PlantUML

이 자료들은 DX11 경험, 엔진 구조, Animation Tool, Unity 포트폴리오 설계의 근거다.

## 삭제하거나 기본 관리에서 제외한 것

아래 항목은 별도 문서로 계속 관리하지 않는다.

- KPI 상세 문서
- Risk Log 상세 문서
- Recruiter Mode 문서
- Demo Video Plan 문서
- 과도한 Blog Roadmap
- 중복 Git 전략 문서
- 중복 Notion 템플릿 문서
- 기능별 01~07 문서 강제 규칙
- CI/CD 상세 자동화 계획

필요한 내용은 `PORTFOLIO_PLAN.md` 또는 `AGENT_HANDOFF.md`에 짧게 흡수한다.

## 작업 권한 규칙

사전 확인 없이 진행 가능:

- Markdown 읽기
- 파일 구조 분석
- grep/search
- 포트폴리오 문서 수정
- 계획 문서 수정
- Git 운영 문서 수정
- README 수정
- PlantUML 수정
- 문서 링크 정리
- 중복 문서 정리
- 작업 로그 정리

사전 확인 필요:

- 실제 소스 코드 수정
- 코드 생성 또는 코드 삭제
- 커밋 생성
- Push 수행
- Release 생성
- 실제 ZIP 생성 또는 배포 파일 변경
- 시스템 설정 변경
- 패키지 설치/삭제
- 외부 서비스 연동
- CI/CD 설정 변경
- 데이터 손실 가능성이 있는 작업

단, 사용자가 명시적으로 삭제를 지시한 문서는 삭제 가능하다. 분석 자료는 보존한다.

## Git 운영 기준

현재 문서 원격 저장소:

```text
https://github.com/starkshn/md-docs.git
```

로컬 문서 저장소:

```text
C:\kny\technical-portfolio-docs
```

Unity 프로젝트 로컬 저장소:

```text
C:\kny\Project\Unity\unity-technical-showcase
```

GitHub 블로그 / 포트폴리오 사이트:

```text
C:\kny\starkshn.github.io
```

문서 수정은 가능하지만 commit / push는 사용자 확인 후 진행한다.

## 로컬 PlantUML 기준

로컬에서만 빠르게 보는 UML은 아래에 둔다.

```text
C:\kny\plantuml-overview
```

계획, Git 구조, 일정 구조, 포폴 구조가 바뀌면 관련 PlantUML도 같이 수정한다.

## Notion / Calendar 기준

Notion은 일정과 개발 일지 중심으로 사용한다.

Google Calendar는 실제 시간 제약 확인용이다.

패치 당일과 전날은 개발하지 않는 것을 기본 규칙으로 한다.

## 문서 추가 기준

새 문서는 아래 조건일 때만 만든다.

- 실제 구현 기능의 설계 문서가 필요하다.
- DX11 분석과 Unity 연결을 설명해야 한다.
- 다른 에이전트에게 넘길 독립 요약이 필요하다.
- PlantUML 구조도가 필요하다.

그 외에는 기존 문서에 흡수한다.

## Project Learning Rule

When a Unity feature or project setting is introduced, record the concept before implementing it.

For each important Unity concept, document:

- what it is
- why it exists
- how it affects project structure
- how it supports the portfolio goal
- what the next implementation step is

Current example:

```text
Assembly Definition → projects/unity-technical-showcase/AssemblyDefinitionPlan.md
```

## Career Portfolio Direction Rule

포트폴리오의 1차 타깃은 컴투스 / 중견 Unity 클라이언트 회사에 맞춘다.

우선순위:

1. Skill System
2. Skill Editor Tool
3. Addressables / Data Loading
4. UI / Debug / Metrics
5. 간단한 Animation Event 연동
6. Shader는 후순위 예제

시프트업 / 넥슨 / 스마일게이트 대응은 1차 완성 후 Animation / Rendering / Combat 설명력을 추가하는 방식으로 확장한다.

새 기능을 제안할 때는 먼저 아래 질문에 답한다.

- Unity 라이브 서비스 포폴에 직접 도움이 되는가?
- Skill / Tool / Addressables / UI / Debug 중 하나를 강화하는가?
- 면접에서 실무적인 구조로 설명 가능한가?
- 단순 시각 효과나 과시용 기능에 과하게 시간을 쓰는 것은 아닌가?

## Skill Learning Project Rule

`C:\kny\Project\Unity\SkillProject` is the learning and experiment project for the Inflearn modular skill system course.

`C:\kny\Project\Unity\UnityTechnicalShowcase` is the final portfolio project.

Do not copy course code directly into the portfolio project.

First complete the course in SkillProject, then analyze the completed structure, extract useful concepts, discard weak structures, and redesign the system for UnityTechnicalShowcase.

Reference document:

```text
projects/skill-project/SkillCourseLearningWorkflow.md
```
