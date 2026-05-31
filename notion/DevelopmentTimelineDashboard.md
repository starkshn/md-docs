# Development Timeline Dashboard

## Purpose

This Notion dashboard exists to show the portfolio development history at a glance.

It answers the following questions:

- What was developed?
- When did it start and end?
- Which feature or system does it belong to?
- What phase was it in?
- What is the current status?
- Which Markdown, PlantUML, Git commit, blog draft, and interview notes are connected?
- Can the user click one item and move to the full development context?

## Notion Pages

### Schedule Dashboard

```text
https://www.notion.so/3714bccaf9eb81cabf9edec06dd3a6da
```

Role:

- Calendar planning
- Sprint planning
- Patch day / no development day management
- Reschedule history
- Development timeline dashboard

### Development Hub

```text
https://www.notion.so/3714bccaf9eb8020bc85e39638c56d7b
```

Role:

- Concept study
- Architecture design
- Implementation notes
- Core code summary
- Markdown / PlantUML links
- Blog draft
- Interview notes
- Weekly review

## Timeline Database

Database:

```text
포트폴리오 개발 타임라인
```

URL:

```text
https://www.notion.so/fa259baed449460693fcdfbd2d0dc4b2
```

Data Source:

```text
collection://99f867b4-09cd-43c3-9f47-0b5e86cde399
```

## Views

### 01 전체 일정 타임라인

Purpose:

- Shows all development work, No Development blocks, patch buffers, and milestone reviews in one timeline.
- This is the main visual dashboard for "what happened when".

### 02 MVP 1 로드맵

Purpose:

- Shows only MVP 1 work.
- Current MVP 1 scope is Skill System, Skill Tool, documentation, UML, blog draft, and interview readiness.

### 03 작업 큐

Purpose:

- Main editing table.
- Use this view when adding, modifying, prioritizing, or rescheduling work.

### 04 캘린더 연결됨

Purpose:

- Shows items already linked to Google Calendar.
- Used to confirm which Notion records have actual calendar references.

### 05 개발 금지 / 패치

Purpose:

- Shows patch days, patch -1 buffers, vacation days, and other blocked days.
- No implementation work should be scheduled here.

### 06 상태 보드

Purpose:

- Board grouped by `Calendar Status`.
- Useful for seeing whether a task is not scheduled, scheduled, linked, needs reschedule, blocked, or done.

### 08 캘린더 생성 큐

Purpose:

- Shows items where `Calendar Action = Create Event`.
- Codex can read this view and create Google Calendar events from it.

### 09 캘린더 이동 큐

Purpose:

- Shows items where `Calendar Action = Reschedule`.
- Codex can read this view and move existing Google Calendar events.

### Development Timeline

```text
view://3714bcca-f9eb-81f5-b331-000cbf492a5e
```

Purpose:

- Shows each development item by start and end date.
- Used as the main visual schedule and history view.
- The user can click each item to open the full development summary.

### Timeline Table

```text
view://3714bcca-f9eb-81be-bb8c-000cd7ab8f10
```

Purpose:

- Shows all timeline records in a dense table.
- Useful for editing status, links, commits, risk, and KPI level.

### By Feature

```text
view://3714bcca-f9eb-812e-b61f-000cf1e71fa2
```

Purpose:

- Groups development items by feature area.
- Useful for checking whether Skill System, Skill Tool, Animation Tool, Shader Showcase, Optimization, Rendering Debug, Lua Scripting, Docs, and Automation are balanced.

## Database Schema

| Property | Type | Purpose |
| --- | --- | --- |
| 작업명 | Title | Development item name |
| 항목 유형 | Select | 개발 작업, 학습, 문서화, 블로그, 리뷰, 일정 차단, 패치 버퍼, 마일스톤 |
| 기능 | Select | Feature category |
| 단계 | Select | 개념 학습, 아키텍처 설계, 미니 실험, 구현, 검증, 문서화, 블로그 초안, 면접 정리, 리뷰 |
| 상태 | Select | 예정, 진행 중, 차단됨, 검토 중, 완료, 보류 |
| 우선순위 | Select | P0, P1, P2, P3 |
| 스프린트 | Select | MVP 1, MVP 2, MVP 3, Backlog, Maintenance |
| 캘린더 상태 | Select | 미등록, 등록 예정, 캘린더 연결됨, 일정 변경 필요, 개발 금지, 완료 |
| 캘린더 작업 | Select | 없음, 일정 생성, 일정 수정, 일정 이동, 일정 취소 |
| 시작일 | Date | Start date |
| 종료일 | Date | End date |
| KPI 단계 | Select | Completion or maturity level from 0 to 5 |
| 개발 허브 | URL | Link to detailed Notion development page |
| Google Calendar 링크 | URL | Google Calendar event link |
| Google 이벤트 ID | Rich text | Google Calendar event ID when available |
| 문서 | URL | Link to Markdown document |
| PlantUML | URL | Link to PlantUML diagram |
| Git 커밋 | Rich text | Related commit hash or commit list |
| Calendar Event | URL | Related Google Calendar event link |
| 블로그 초안 | URL | Related Tistory blog draft |
| 면접 노트 | URL | Related interview summary |
| 예상 시간 | Number | Planned effort |
| 실제 시간 | Number | Actual effort |
| 다음 작업 | Rich text | Immediate next action |
| 완료 기준 | Rich text | Completion criteria |
| 개발 금지 | Checkbox | True for patch/vacation/no-dev blocks |
| 담당 | Select | NY, Codex, or NY + Codex |
| 일정 메모 | Rich text | Scheduling context |
| 리뷰일 | Date | Review date |
| 요약 | Rich text | Short explanation of what was done |
| 위험도 | Select | 낮음, 보통, 높음 |

## Initial Records

### Portfolio Documentation Foundation

Status: Done

Connected commits:

```text
a0f6342, 0128bf2, 66cf663
```

Page:

```text
https://www.notion.so/3714bccaf9eb81b88aaec4325f65af35
```

### MVP Scope and Learning Workflow

Status: Done

Connected commits:

```text
4b7cb37, 5187b73
```

Page:

```text
https://www.notion.so/3714bccaf9eb81878796dcf6f6955503
```

### Feature Toggle and Before/After Architecture

Status: Done

Connected commit:

```text
95e53af
```

Page:

```text
https://www.notion.so/3714bccaf9eb81469c52c1ca4804c725
```

### NY Module Naming Governance

Status: Done

Connected commits:

```text
73dee5a, 4ddfba7
```

Page:

```text
https://www.notion.so/3714bccaf9eb819caa7ce0cdfa06c3ca
```

### Selective Lua Scripting Layer

Status: Done

Connected commit:

```text
9832585
```

Page:

```text
https://www.notion.so/3714bccaf9eb810e96b4face76831b98
```

### Google Calendar and Notion Schedule Workflow

Status: Done

Connected commits:

```text
77630e9, 98fb355, 0777d4f
```

Page:

```text
https://www.notion.so/3714bccaf9eb813e81a1ee6af0ec5034
```

### Portfolio Automation Strategy

Status: Done

Connected commits:

```text
180bceb, dc52721
```

Page:

```text
https://www.notion.so/3714bccaf9eb819fb8a7eace8dcbf666
```

## Google Calendar Reflected Blocks

The following Google Calendar events were reflected into the timeline database as No Development items:

| Date | Type | Calendar Event |
| --- | --- | --- |
| 2026-06-05 | Calendar Block | 이사 + 휴가 |
| 2026-06-09 | Patch Buffer | 마루패치 -1 |
| 2026-06-10 | Calendar Block | 마루패치 |
| 2026-06-30 | Patch Buffer | 커피패치 -1 |
| 2026-07-01 | Calendar Block | 커피패치 |
| 2026-07-21 | Patch Buffer | 마루 패치 -1 |
| 2026-07-22 | Calendar Block | 마루 패치 |

## MVP 1 Draft Schedule

The following draft schedule was added to the database:

| Date | Task | Purpose |
| --- | --- | --- |
| 2026-06-01 to 2026-06-02 | MVP1 - Skill System Concept Study | Study core concepts |
| 2026-06-03 to 2026-06-04 | MVP1 - Skill System Architecture Design | Define runtime architecture |
| 2026-06-06 to 2026-06-07 | MVP1 - Skill System Mini Experiment | Validate one small data-driven skill |
| 2026-06-08 | MVP1 - Skill System Implementation A | Start runtime skeleton before patch buffer |
| 2026-06-11 to 2026-06-14 | MVP1 - Skill System Implementation B | Implement runtime assembly |
| 2026-06-15 to 2026-06-16 | MVP1 - Skill System Verification and Docs | Verify and document Skill System |
| 2026-06-17 to 2026-06-18 | MVP1 - Skill Tool Concept and Architecture | Design EditorWindow workflow |
| 2026-06-19 to 2026-06-21 | MVP1 - Skill Tool Mini Experiment | Validate editor experiment |
| 2026-06-22 to 2026-06-27 | MVP1 - Skill Tool Implementation | Implement usable Skill Tool |
| 2026-06-28 to 2026-06-29 | MVP1 - Skill Tool Verification and Docs | Verify and document Skill Tool |
| 2026-07-02 to 2026-07-05 | MVP1 - Milestone Review | Review MVP 1 readiness after patch day |

## Calendar Sync Workflow

Notion is the source of schedule intent.

Google Calendar is the source of real time blocks.

Codex acts as the sync operator.

```text
Notion Work Queue
↓
Calendar Action = Create Event / Reschedule / Update Event / Cancel
↓
Codex reads the queue
↓
Codex checks Google Calendar conflicts and patch blocks
↓
Codex creates or updates Google Calendar
↓
Codex writes Google Calendar URL and Event ID back to Notion
```

## User Editing Rule

When manually editing the database:

1. Use `03 작업 큐`.
2. Edit `작업명`, `시작일`, `종료일`, `우선순위`, `스프린트`, and `다음 작업`.
3. If the task should appear in Google Calendar, set `캘린더 작업 = 일정 생성`.
4. If an existing calendar event should move, set `캘린더 작업 = 일정 이동`.
5. Never schedule implementation work on rows where `개발 금지 = checked`.

## Korean Management Naming

The Notion database is a management surface, so visible database names, view names, property names, and option labels are Korean-first.

Technical proper nouns remain in English when that improves recognition:

- Git
- PlantUML
- Google Calendar
- MVP
- ModuleHub
- Before/After
- Lua

## Operating Rule

Every meaningful development item must be recorded in this database.

A record is valid only when it has at least:

- Task
- Feature
- Phase
- Status
- Start
- End
- Summary

When the work becomes explainable as a portfolio asset, also add:

- Docs
- PlantUML
- Git Commit
- Blog Draft
- Interview Notes

## Codex Update Rule

When Codex completes or plans a development item:

1. Update the Notion timeline database.
2. Link the item to the Development Hub when detailed notes exist.
3. Update the local Markdown docs.
4. Update `CODEX_WORK_MEMORY.md`.
5. Commit the documentation update.

## User Workflow

Use `Development Timeline` when you want to see the schedule visually.

Use `Timeline Table` when you want to edit metadata quickly.

Use `By Feature` when you want to check feature balance.

Click a timeline item to see:

- What was developed
- Why it was developed
- Related commits
- Related docs
- Related architecture notes
- Blog and interview follow-up
