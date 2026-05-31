# Two Page Notion Management Structure

## 목적

기존 `UnityProjectAZ_NotionTemplate` 한 페이지에 일정, 학습, 개발일지, 자동화, 블로그, 면접 준비를 모두 넣는 구조는 장기적으로 무거워진다.

따라서 Notion 운영 구조를 2개 페이지로 분리한다.

```text
Schedule Dashboard = 언제 할 것인가
Development Hub = 무엇을 배웠고 무엇을 만들었는가
```

## Page 1. Schedule Dashboard

URL:

```text
https://www.notion.so/3714bccaf9eb81cabf9edec06dd3a6da
```

역할:

- 전체 일정 관리
- 이번 주 Calendar Plan
- Current Sprint
- Patch Schedule / No Development Days
- Calendar Changes
- Missed / Rescheduled Blocks
- Automation Schedule
- Calendar Event Naming Rule
- Codex Schedule Request Templates

## Page 2. Development Hub

URL:

```text
https://www.notion.so/3714bccaf9eb8020bc85e39638c56d7b
```

역할:

- 학습 내용
- 개발일지
- 핵심 코드 요약
- Markdown / PlantUML 링크
- Blog Draft
- Interview Notes
- Architecture Governance Review
- CI/CD Status
- Portfolio Automation Dashboard

## Coupling Rule

두 페이지는 강하게 병합하지 않고, 링크로 느슨하게 연결한다.

Schedule Dashboard에서 Development Hub로 연결:

```text
일정 결과 -> Development Log / Weekly Review / Risk Log
```

Development Hub에서 Schedule Dashboard로 연결:

```text
다음 작업 -> Calendar Event / Sprint Plan
```

## Codex 작업 규칙

Codex는 Notion을 업데이트할 때 먼저 어느 페이지에 기록할지 판단한다.

Schedule 관련:

- Calendar 일정
- Sprint Plan
- Patch No Development Day
- Reschedule
- Weekly Review 일정

Development 관련:

- Concept Study
- Architecture Design
- Implementation Notes
- Core Code Summary
- Blog Draft
- Interview Notes
- CI/CD 결과

## 현재 적용 상태

- `Unity Project A-Z - Schedule Dashboard` 페이지 생성 완료
- 기존 `UnityProjectAZ_NotionTemplate` 페이지 상단에 Navigation / Page Role 추가 완료
- 두 페이지 간 링크 연결 완료
