# Google Calendar + Notion Schedule System

## 목적

Unity Technical Showcase 개발 일정은 Google Calendar와 Notion을 함께 사용해서 관리한다.

| 도구 | 역할 |
| --- | --- |
| Google Calendar | 실제 시간 블록, 반복 일정, 일정 수정 |
| Notion | 작업 상태, KPI, 개발일지, 산출물, 회고 |
| Codex | 일정 확인, 현실성 분석, 수정안 제안, 문서/일지 반영 |

## 핵심 원칙

- Calendar는 “언제 할 것인가”를 관리한다.
- Notion은 “무엇을 왜 했고 어떤 산출물이 남았는가”를 관리한다.
- Codex는 Calendar 일정을 보고 현재 계획이 현실적인지 검토한다.
- 일정이 밀리면 Calendar를 수정하고, Notion의 Risk / Weekly Review에도 반영한다.

## Calendar Event Naming

Google Calendar 일정 이름은 아래 형식을 따른다.

```text
[Portfolio][Type] Phase - Task
```

예시:

```text
[Portfolio][Study] Skill System - Data Driven Design
[Portfolio][Experiment] Lua Damage Formula
[Portfolio][Implement] NY_Skill_SystemModule MVP
[Portfolio][Docs] Feature Toggle Architecture
[Portfolio][Review] Weekly Portfolio Review
```

## Event Type

| Type | Calendar Prefix | Notion 연결 |
| --- | --- | --- |
| Concept Study | `[Study]` | 공부한 개념 |
| Mini Experiment | `[Experiment]` | 실험 결과 |
| Implementation | `[Implement]` | 구현 기록 |
| Verification | `[Verify]` | 검증 결과 |
| Documentation | `[Docs]` | Markdown / PlantUML |
| Blog Draft | `[Blog]` | Tistory 초안 |
| Notion Journal | `[Journal]` | 개발일지 |
| Weekly Review | `[Review]` | 주간 리뷰 |
| Buffer | `[Buffer]` | 밀린 작업 보정 |

## Weekly Schedule Template

| 요일 | 권장 작업 | 목적 |
| --- | --- | --- |
| 월 | Concept Study / 주간 계획 | 새 개념 진입, 일정 확정 |
| 화 | Mini Experiment | 작은 검증 |
| 수 | Implementation | 포트폴리오 통합 |
| 목 | Documentation / PlantUML | 구조 정리 |
| 금 | Buffer / Review | 밀린 작업 정리 |
| 토 | Deep Work | 구현 집중 |
| 일 | Weekly Review / Blog Draft | 회고와 블로그 초안 |

## Calendar ↔ Notion Sync Rule

| Calendar 변경 | Notion 반영 |
| --- | --- |
| 일정 완료 | Development Log Index에 기록 |
| 일정 연기 | Risk Log 또는 Weekly Review에 사유 기록 |
| 일정 삭제 | Backlog 또는 Won't 사유 확인 |
| 일정 추가 | Backlog 위치와 KPI Level 확인 |
| 주간 계획 변경 | Current Week Plan 갱신 |

## Codex Calendar Review Flow

```text
Google Calendar 일정 조회
↓
이번 주 Portfolio 일정 필터링
↓
Notion Dashboard / Backlog / KPI와 비교
↓
과한 일정 또는 누락된 일정 탐지
↓
수정안 제안
↓
사용자 지시 또는 승인 시 Calendar 일정 수정
↓
Notion Journal / Weekly Review 반영
```

## Schedule Update Policy

### 바로 수정 가능한 경우

사용자가 명확히 요청한 경우:

```text
오늘 Skill System 공부 일정을 내일 같은 시간으로 옮겨줘.
이번 주 Portfolio Review를 일요일 21시로 바꿔줘.
토요일 14시에 Skill Tool Mini Experiment 일정 추가해줘.
```

### 수정 전 확인이 필요한 경우

- 업무/개인 일정과 충돌 가능성이 있는 경우
- 시간대가 애매한 경우
- 반복 일정 변경 범위가 불명확한 경우
- 삭제가 필요한 경우

## Calendar Event Description Template

```text
Goal:
- 

Notion:
- UnityProjectAZ_NotionTemplate

Docs:
- C:\kny\technical-portfolio-docs\...

Completion Gate:
- Concept Study
- Mini Experiment
- Markdown
- PlantUML
- Blog Draft
- Interview Notes

Codex Note:
- 이 일정 완료 후 Development Log Index 업데이트 필요
```

## Recommended Recurring Events

| 일정 | 반복 | 목적 |
| --- | --- | --- |
| Portfolio Weekly Planning | 매주 월요일 | 이번 주 목표 설정 |
| Portfolio Deep Work | 매주 토요일 | 구현 집중 |
| Portfolio Weekly Review | 매주 일요일 | KPI / Risk / Blog / Interview 정리 |
| Blog Draft Block | 격주 일요일 | Tistory 초안 정리 |

## 면접 설명 포인트

이 일정 관리 구조는 단순 시간표가 아니다. 포트폴리오 개발을 실제 업무처럼 운영하기 위한 시스템이다.

- Calendar로 실제 작업 시간을 확보했다.
- Notion으로 작업 결과와 의사결정을 기록했다.
- Git / Docs / PlantUML / Blog / Interview Notes를 일정과 연결했다.
- 일정이 밀릴 때 Risk Log와 Weekly Review에 사유를 남겼다.
