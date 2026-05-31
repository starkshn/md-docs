# Portfolio Automation Strategy

## 목적

Unity Technical Showcase 포트폴리오는 단순히 기능을 구현하는 프로젝트가 아니다.

이 프로젝트는 다음을 증명해야 한다.

- 설계 능력
- 유지보수 능력
- 확장성 고려 능력
- 기술 문서화 능력
- 품질 관리 능력

따라서 기능 구현뿐 아니라 개발 프로세스 자체를 자동화한다.

## Automation Overview

본 프로젝트는 다음 3개의 자동화 시스템을 운영한다.

```text
1. Architecture Governance Review
2. Unity CI/CD Pipeline
3. Weekly Technical Review
```

각 자동화는 기능 구현보다 우선순위가 낮지만, 포트폴리오 품질을 유지하는 핵심 시스템이다.

## 현재 Notion 문서와의 차이

현재 Notion 템플릿은 다음을 이미 포함한다.

- Master Dashboard
- Required Development Cycle
- Current Week Plan
- Daily Development Journal
- Weekly Review Template
- Feature Completion Gate
- Google Calendar Schedule Dashboard
- Patch Week No Development Rule

부족한 부분은 다음이다.

- Architecture Governance Review 결과를 누적 관리하는 표
- Unity CI/CD 상태를 한눈에 보는 표
- Weekly Technical Review 자동화 입력/출력 구조
- Build / Test / Docs / UML 실패를 기능 완료 Gate와 연결하는 규칙
- Calendar / Notion / GitHub Actions의 역할 분리

따라서 Notion에는 `Portfolio Automation Dashboard`를 추가한다.

## 1. Architecture Governance Review

### 목적

새로운 기능을 추가할 때마다 현재 아키텍처와 충돌하는지 검토한다. 기능을 무작정 추가하지 않고, 추가 전에 구조적 영향 분석을 수행한다.

### 동작 흐름

```text
새로운 기능 아이디어
↓
Architecture Review
↓
Dependency Analysis
↓
ModuleHub 영향 분석
↓
Assembly 영향 분석
↓
Feature Toggle 가능 여부
↓
Before/After 비교 가능 여부
↓
Blog 가치 평가
↓
Interview 가치 평가
↓
승인 또는 보류
```

### Codex 필수 체크리스트

Architecture:

- 기존 구조와 충돌하는가?
- ModuleHub에 등록 가능한가?
- 카테고리가 적절한가?

Dependency:

- 다른 모듈과 강하게 결합되는가?
- 제거 시 문제가 발생하는가?

Tool:

- Tool UI에서 제어 가능한가?

Comparison:

- Before / After 비교가 가능한가?

Metrics:

- 측정 가능한 데이터가 있는가?

Blog:

- 기술 블로그 주제로 가치가 있는가?

Interview:

- 면접에서 설명 가능한가?

### 평가 결과

```text
Approved
Conditional Approval
Rejected
```

## 2. Unity CI/CD Pipeline

### 목적

포트폴리오의 품질을 유지한다. 기능 추가 후 빌드가 깨지지 않도록 한다.

### 기술 스택

```text
GitHub Actions
Unity Test Runner
Unity Build
Artifact Upload
```

### 동작 흐름

```text
Git Push
↓
GitHub Actions
↓
Compile
↓
Unit Test
↓
Integration Test
↓
Build
↓
Artifact Upload
```

### Codex 요구사항

기능 구현 후 반드시 확인한다.

Build:

- 컴파일 성공

Test:

- 테스트 통과

Assembly:

- 순환 참조 없음

Docs:

- Markdown 존재

UML:

- PlantUML 존재

### 실패 상태

```text
Build Failed
Test Failed
Missing Documentation
Missing UML
```

실패가 있으면 기능 완료로 간주하지 않는다.

## 3. Weekly Technical Review

### 목적

프로젝트 진행 상황을 매주 점검한다. 기술 부채를 관리하고 블로그 후보를 선정한다.

### 실행 주기

```text
매주 일요일
```

### Review 입력 데이터

```text
GitHub
Markdown
PlantUML
Notion Journal
Blog Draft
Interview Notes
Google Calendar
```

### 생성 결과

Progress:

```text
Skill System
Skill Tool
Animation Tool
Shader Showcase
Optimization Showcase
Rendering Debug View
```

Documentation Coverage:

```text
구현 대비 문서화 비율
```

Blog Coverage:

```text
블로그 작성 비율
```

Interview Coverage:

```text
면접 정리 비율
```

Technical Debt 예시:

```text
Skill Validation 부족
Dependency 증가
Assembly 분리 필요
```

Next Week Goals 예시:

```text
Skill Tool 완성
Validation 추가
Skill Timeline 구현
```

## Notion 운영 방식

Notion에는 다음 정보를 유지한다.

```text
Portfolio Health Dashboard
Automation Dashboard
Architecture Review Log
CI/CD Status
Weekly Technical Review
```

## Calendar 운영 방식

Google Calendar에는 다음 반복 일정을 둔다.

- Weekly Planning
- Deep Work
- Weekly Technical Review
- Blog Draft Block

패치 전날/당일은 No Development Day로 유지한다.

## Codex 역할

Codex는 단순 코드 생성기가 아니다.

항상 아래 역할을 수행한다.

```text
Architect
Reviewer
Documentation Writer
UML Designer
Blog Assistant
Interview Coach
Technical Debt Reviewer
Schedule Reviewer
```

## 최종 규칙

새로운 기능을 구현하기 전에 반드시 수행한다.

```text
Architecture Governance Review
```

기능 구현 후 반드시 수행한다.

```text
Build
Documentation
PlantUML
Interview Notes
```

매주 반드시 수행한다.

```text
Weekly Technical Review
```

위 단계가 완료되지 않으면 해당 기능은 완료로 간주하지 않는다.
