# Module Governance System

## 목적

기능 욕심으로 프로젝트가 비대해지는 것을 막기 위해, 새로운 기능을 추가하기 전에 아키텍처 충돌과 의존성 영향을 검토한다.

## 문제 정의

포트폴리오를 진행하다 보면 Node Graph, Behavior Tree, AI, VFX, Addressables 심화 같은 기능 아이디어가 계속 생긴다. 검토 없이 기능을 추가하면 MVP가 무너지고, 모듈 간 결합도가 높아지며, 문서화와 면접 설명도 산만해진다.

## Architecture Governance 프로세스

```text
새로운 기능 추가 요청
↓
Backlog 위치 결정
↓
현재 구조와 충돌 검사
↓
ModuleHub 등록 가능 여부 확인
↓
Assembly Definition 영향 분석
↓
기존 Feature와 결합도 분석
↓
Before/After 및 Metrics 가능 여부 확인
↓
Docs / Blog / Interview 가치 판단
↓
추가 승인 또는 보류
↓
구현
```

## 기능 추가 전 필수 질문

- 이 기능은 Must / Should / Could / Won't 중 어디에 속하는가?
- `NY_Core_ModuleHub`에 등록 가능한가?
- `INY_Module` 생명주기를 따를 수 있는가?
- Runtime / Editor 책임이 분리되는가?
- 기존 모듈을 직접 참조하지 않고 연결 가능한가?
- Assembly Definition 참조 방향을 깨지 않는가?
- Before/After 비교가 가능한가?
- Metrics로 차이를 증명할 수 있는가?
- 기술 블로그로 쓸 가치가 있는가?
- 면접관에게 1분 안에 설명 가능한가?
- 일반 Unity 포트폴리오와 비교해 어떤 차별성을 만드는가?

## 승인 기준

기능은 다음 조건을 만족해야 구현에 들어간다.

- Backlog 위치가 명확하다.
- KPI Level 1~5가 정의되어 있다.
- 모듈 인터페이스가 정해져 있다.
- Assembly 참조 방향이 명확하다.
- 기존 모듈과 직접 결합하지 않는다.
- 최소 하나 이상의 문서/블로그/면접 포인트가 있다.

## 보류 기준

다음에 해당하면 구현하지 않고 Backlog에 둔다.

- 기존 Must 기능 완료를 방해한다.
- 핵심 포트폴리오 목표와 직접 관련이 약하다.
- 서버, DB, 로그인, 매칭, ECS, DOTS처럼 현재 제외 범위에 해당한다.
- Before/After 또는 Metrics로 차이를 보여주기 어렵다.
- 구현 대비 면접 설명 가치가 낮다.

## Codex 작업 규칙

Codex는 새 기능 추가 요청을 받으면 구현 전에 먼저 Architecture Governance Report를 작성한다.

보고서에는 다음을 포함한다.

- 기능 요약
- Backlog 위치
- 관련 모듈
- 필요한 인터페이스
- Assembly 영향
- 의존성 위험
- Before/After 가능성
- Metrics 가능성
- 문서/블로그/면접 가치
- 승인/보류 판단
