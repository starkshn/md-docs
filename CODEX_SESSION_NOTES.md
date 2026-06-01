# Codex Session Notes

This file stores session-level notes for Codex/GPT/Claude handoff.

For global context, read:

- `C:\kny\CODEX_WORK_MEMORY.md`

## Current Baseline

The technical portfolio documentation workspace has been created at:

- `C:\kny\technical-portfolio-docs`

The main planning document is:

- `PortfolioStudyMasterPlanForGPT.md`

Claude entry point:

- `CLAUDE.md`

Operating guide:

- `RepositoryOperatingGuide.md`

## /save-md Rule

When the user says `/save-md`, update:

- `C:\kny\CODEX_WORK_MEMORY.md`
- `C:\kny\technical-portfolio-docs\CODEX_SESSION_NOTES.md`

Include session summary, paths, commits, decisions, open tasks, and warnings.

## Last Known State

- Root documentation repo exists and is committed.
- GunFireReborn docs are committed in the DX11 repo.
- AnimTool docs are committed in the DX11 repo.
- Existing source/binary changes in both DX11 repos are not Codex documentation work and should not be touched unless explicitly requested.

## Session Update - PlantUML Korean Label Localization

Date: 2026-05-31

User request:

- Convert PlantUML labels to Korean.
- Keep class names, variable names, file names, and technical identifiers in English where appropriate.

Completed:

- Localized user-facing PlantUML labels to Korean.
- Kept identifiers such as `CGameInstance`, `CModel`, `SkillFactory`, `SkillDefinitionSO`, `RuntimeSystems` aliases, and method names in English.
- Updated `.puml` files in the root documentation repository.
- Synced PlantUML changes into GunFireReborn docs and AnimTool docs.
- Updated embedded PlantUML blocks in `PortfolioStudyMasterPlanForGPT.md`.

Commits:

- `C:\kny\technical-portfolio-docs`
  - `93eea93 docs: localize PlantUML labels to Korean`
- `C:\kny\Project\DirectX\GunFireReborn\DX11_FrameWork`
  - `3920730 docs: localize PlantUML labels to Korean`
- `C:\kny\Project\DirectX\AnimTool`
  - `f391bdd docs: localize PlantUML labels to Korean`

Important note:

- Existing source/binary dirty changes in the DX11 repositories remain untouched.
- Only documentation and PlantUML files were committed.

## Session Update - MVP Scope And Showcase Feedback Applied

Date: 2026-05-31

User feedback:

- Overall direction is good, but the scope is too wide.
- First release should focus on Modular Skill System + Skill Editor + Technical Showcase Scene.
- Documentation should enforce a fixed feature folder template.
- Showcase Scene should be designed as a technical dashboard.
- Every feature must include Before / After proof.

Completed:

- Added MVP priority strategy.
- Added fixed feature documentation template.
- Added Technical Showcase Scene dashboard design.
- Added Before / After demonstration rule.
- Created MVP 1 feature folders:
  - `projects/unity-technical-showcase/skill-system/`
  - `projects/unity-technical-showcase/skill-editor/`
- Added template files:
  - `00_README.md`
  - `01_Concept.md`
  - `02_MiniExperiment.md`
  - `03_Architecture.md`
  - `04_Implementation.md`
  - `05_BlogDraft.md`
  - `06_Interview.md`
  - `07_BeforeAfter.md`
  - `uml/`
- Added PlantUML diagrams:
  - `MvpPriorityStructure.puml`
  - `ShowcaseDashboardLayout.puml`

Commits:

- `C:\kny\technical-portfolio-docs`
  - `docs: refine MVP scope and feature documentation structure`
- `C:\kny\Project\DirectX\GunFireReborn\DX11_FrameWork`
  - `docs: refine MVP scope and showcase documentation`
- `C:\kny\Project\DirectX\AnimTool`
  - `docs: add Unity showcase MVP reference docs`

Important decision:

- MVP 1 is now limited to Skill System, Skill Editor, Technical Showcase Scene, Markdown Docs, and PlantUML.
- Animation, Shader, Optimization, Rendering Debug View, and full blog polish are later phases.

## 2026-05-31 - Feature Toggle / Before-After 비교 구조 추가

첨부 텍스트를 다시 참고해서 다음 내용을 문서화했다.

- 모든 기능을 `IFeatureModule` 기반 독립 모듈로 관리
- `FeatureToggleManager` 중심의 ON/OFF, 의존성, 상태, Metrics 구조
- `ComparisonViewSystem` 기반 Before/After RenderTexture 비교
- `ShowcaseControlPanel` 중심의 기술 시연 대시보드
- 인프런 스킬 시스템 강의를 그대로 복사하지 않고 포트폴리오 구조로 변환하는 규칙

새 문서 폴더:

- `projects/unity-technical-showcase/feature-toggle/`

다음 세션에서 이 폴더와 `PortfolioStudyMasterPlanForGPT.md`를 먼저 읽으면 전체 설계 방향을 빠르게 파악할 수 있다.

## 2026-05-31 15:11:26 +09:00 - /save-md 및 GPT 평가 요청 문서 생성

사용자가 /save-md를 요청했다. 현재 Unity Technical Showcase 포트폴리오 설계를 GPT에게 평가받을 수 있도록 GPT_EVALUATION_REQUEST.md를 생성했다.

주요 평가 요청 축:

- 2~5년차 게임 클라이언트 포트폴리오 경쟁력
- MVP 1순위 현실성
- Feature Toggle / Before-After 구조의 적절성
- Skill System / Skill Editor 우선순위
- Unity 숙련도 부족 상태에서의 학습 로드맵
- 면접 시연 흐름
- 6개월 / 12개월 버전

경로:

- C:\kny\technical-portfolio-docs\GPT_EVALUATION_REQUEST.md

## 2026-05-31 15:16:03 +09:00 - 학습 기반 개발 사이클 및 블로그/노션 연계 규칙 추가

사용자가 추가한 14~30번 규칙을 반영했다.

핵심 변경:

- 기능 구현보다 학습 과정과 설명 가능성을 우선하는 전략 명문화
- Concept Study -> Architecture Design -> Mini Experiment -> Implementation -> Verification -> Git Commit -> Markdown -> PlantUML -> Blog Draft -> Notion Journal -> Interview Notes 사이클 추가
- 기능 완료 체크리스트 추가
- 기술적 가치가 있는 기능만 블로그로 작성하는 기준 추가
- Notion Development Journal 및 Weekly Review 템플릿 추가
- 차별화 포인트 추적 시스템 추가
- Codex 역할을 Architect/Reviewer/Docs/UML/Blog/Interview Coach로 정의

다음 세션은 workflow 폴더의 4개 신규 문서와 GPT_EVALUATION_REQUEST.md를 먼저 확인하면 된다.

## 2026-05-31 15:19:06 +09:00 - KPI / Backlog / Risk / Recruiter Mode 추가

사용자 피드백을 반영해 strategy 폴더를 추가했다.

신규 문서:

- strategy/PortfolioKpiSystem.md
- strategy/FeatureBacklog.md
- strategy/PortfolioRiskLog.md
- strategy/PortfolioDashboard.md
- strategy/DX11ToUnityMapping.md
- strategy/DemoVideoPlan.md
- strategy/RecruiterMode.md

앞으로 모든 기능은 KPI, Backlog, Risk, DX11 매핑, 영상 계획, Recruiter Summary 기준을 통과해야 한다.

## 2026-05-31 15:22:46 +09:00 - /save-md checkpoint

사용자가 /save-md를 요청했다. 현재까지의 문서화/전략/마스터 플랜 상태를 CODEX_WORK_MEMORY.md에 저장했다.

현재 핵심 상태:

- 전체 마스터 플랜 PlantUML: shared/uml/PortfolioMasterPlan.puml
- 전략 계층: strategy 폴더
- 학습/블로그/노션/면접 강제 사이클: workflow 폴더
- Feature Toggle 및 Before/After 구조: projects/unity-technical-showcase/feature-toggle 폴더
- GPT 평가 요청 파일: GPT_EVALUATION_REQUEST.md
- GPT 전체 전달 파일: PortfolioStudyMasterPlanForGPT.md
- Claude 전달 파일: CLAUDE.md

다음 작업 시 최상위 질문을 유지한다:

이 기능이 일반 Unity 포트폴리오와 비교해서 어떤 차별성을 만들고 있는가?

## 2026-05-31 15:26:59 +09:00 - Notion 템플릿 추가

사용자가 Notion Unity Project A-Z 페이지에서 Codex와 함께 작업한 내용, 개발 과정 일지, 진행률, KPI, Risk, Blog, Interview Notes를 한눈에 관리하고 싶다고 요청했다.

생성 문서:

- 
otion/UnityProjectAZ_NotionTemplate.md

직접 Notion 페이지에 자동 삽입하려면 Notion API/MCP 권한 또는 브라우저 조작 권한이 필요하다. 현재는 Notion에 붙여 넣기 쉬운 Markdown 템플릿으로 생성했다.

## 2026-05-31 15:29:38 +09:00 - Notion 완료 체크 / 핵심 코드 / 블로그 링크 추적 규칙 추가

사용자가 Codex와 작업한 완료 항목을 Notion에서 체크하고, 특정 기능 핵심 코드 요약, 개발일지, 기술 블로그 링크까지 관리해야 한다고 요청했다.

반영 내용:

- 
otion/UnityProjectAZ_NotionTemplate.md에 Codex Completion Tracker 추가
- Core Code Summary Tracker 추가
- Technical Blog Link Tracker 추가
- Development Log Index 추가
- Feature Completion Gate 추가
- Codex Work Result Template 추가
- 
otion/CodexNotionOperationRules.md 신규 생성

앞으로 Codex는 작업 완료 후 Git Commit, 관련 Markdown, PlantUML, Blog Draft, Journal, Interview Notes 상태를 같이 보고해야 한다.

## 2026-05-31 19:10:25 +09:00 - NY Modular Framework / Naming Convention 추가

첨부 텍스트를 분석해 네이밍 컨벤션과 모듈 거버넌스 문서를 추가했다.

결정 사항:

- 일반 C# PascalCase보다 프로젝트 검색성과 모듈 추적성을 우선한다.
- 최종 클래스 네이밍은 `NY_Category_Role`을 사용한다.
- 예: `NY_Core_ModuleHub`, `NY_Skill_SystemModule`, `NY_Skill_DefinitionSO`, `NY_Tool_ModuleDashboard`.
- Interface는 `INY_Module`, Enum은 `ENY_ModuleState`, Event는 `NYE_ModuleEnabled` 형태를 사용한다.
- 새 기능 추가 전 Architecture Governance Report를 작성한다.

신규 문서:

- `projects/unity-technical-showcase/framework/*.md`
- `projects/unity-technical-showcase/framework/uml/*.puml`
- `docs/conventions/*.md`

## 2026-05-31 19:16:23 +09:00 - /save-md naming governance checkpoint

사용자가 /save-md를 요청했다. NY 네이밍 컨벤션과 모듈 거버넌스 적용 상태를 CODEX_WORK_MEMORY.md에 저장했다.

현재 최종 네이밍 규칙:

- Class: `NY_Category_Role`
- Interface: `INY_Module`
- Enum: `ENY_ModuleState`
- Event: `NYE_ModuleEnabled`
- ScriptableObject: `NY_Skill_DefinitionSO`

다음 작업 시 새 기능 추가 전 Architecture Governance Report를 먼저 작성해야 한다.

## 2026-05-31 21:20:52 +09:00 - Selective Lua Scripting Layer 추가

사용자가 Lua를 전체 구조가 아닌 선택적 확장 포인트로만 사용하는 요구사항을 추가했다.

결정 사항:

- C#이 기본 구현 언어다.
- Core Framework, ModuleHub, Rendering, Animation Tool Core, Editor Tool Core, Optimization, Comparison Framework에는 Lua를 적용하지 않는다.
- Lua는 Skill Damage Formula, Condition, Trigger, Formula 같은 작은 Gameplay Logic에만 적용한다.
- 모든 Lua 호출은 `NY_Scripting_Gateway`를 통과한다.
- Lua 실패 시 C# Core가 깨지면 안 되며 fallback, error, timeout, metrics를 둔다.
- MVP 필수 기능이 아니며 Skill System/Tool 안정화 이후 확장 기능으로 둔다.

신규 문서:

- `projects/unity-technical-showcase/scripting/SelectiveLuaScriptingLayer.md`
- `projects/unity-technical-showcase/scripting/LuaSkillFormulaExperiment.md`
- `projects/unity-technical-showcase/scripting/uml/*.puml`

## 2026-05-31 - Google Calendar + Notion 일정 관리 구조 추가

사용자가 Google Calendar와 Notion 조합으로 개발 일정을 직관적으로 관리하고, Calendar 일정을 보고 항상 수정할 수 있는 기능을 추가하자고 요청했다.

반영 내용:

- Google Calendar는 실제 시간 블록 관리
- Notion은 개발 상태, 일지, 산출물, Risk, Weekly Review 관리
- Codex는 Calendar 일정 확인, 현실성 분석, 수정안 제안, 명확한 지시가 있을 때 Calendar 수정
- Notion 템플릿에 Calendar Schedule Dashboard 추가
- `notion/GoogleCalendarNotionScheduleSystem.md` 추가
- `notion/GoogleCalendarNotionScheduleWorkflow.puml` 추가

## 2026-05-31 - Patch Week No Development Rule 추가

사용자가 패치 당일과 패치 전날은 야근 가능성이 높으므로 개발하지 않는 규칙을 추가하자고 요청했다.

반영 내용:

- Google Calendar + Notion 일정 관리 문서에 Patch Week Rule 추가
- Notion 템플릿에 Patch Schedule / No Development Days 표 추가
- 패치 전날/당일에는 구현, 긴 문서 작성, 고집중 작업 금지
- 허용 작업은 10분 메모, 일정 확인, 휴식 정도로 제한
- Calendar에서 해당 날짜에 Portfolio 일정이 있으면 Buffer / Deep Work / Review 이후로 이동 제안

## 2026-05-31 - Portfolio Automation Strategy 추가

사용자가 Architecture Governance Review, Unity CI/CD Pipeline, Weekly Technical Review를 포함한 자동화 전략을 제안하고, 현재 Notion 문서와 비교해 어떻게 관리하고 자동화할지 고려해달라고 요청했다.

반영 내용:

- `workflow/PortfolioAutomationStrategy.md` 추가
- `workflow/PortfolioAutomationWorkflow.puml` 추가
- Notion 템플릿에 `Portfolio Automation Dashboard` 추가
- Architecture Governance Review Log 추가
- Unity CI/CD Pipeline Status 추가
- CI/CD Failure Log 추가
- Weekly Technical Review Automation 추가
- GPT/Claude/마스터 전달 문서에 자동화 전략 반영

운영 기준:

- 새 기능 구현 전: Architecture Governance Review
- 기능 구현 후: Build / Test / Docs / UML / Interview Notes 확인
- 매주 일요일: Weekly Technical Review

## 2026-05-31 21:39:41 +09:00 - Actual Notion page automation dashboard sync

실제 Notion 페이지 `UnityProjectAZ_NotionTemplate`를 fetch해 확인했다.

확인 결과:

- 실제 Notion 페이지는 `Final Interview Package`까지만 있었고, 로컬 Markdown의 이후 섹션은 아직 반영되지 않은 상태였다.
- Notion update tool이 정상 동작하여 실제 페이지 끝에 `Portfolio Automation Dashboard` 섹션을 추가했다.

추가한 섹션:

- Automation Overview
- Portfolio Health Dashboard
- Architecture Governance Review Log
- Unity CI/CD Pipeline Status
- Weekly Technical Review Automation
- Calendar / Notion 운영 규칙
- Codex Request Templates

## 2026-05-31 21:44:41 +09:00 - Notion 2 Page Management Structure 적용

사용자가 한 페이지에 일정과 세부 내용을 모두 넣는 구조는 장기적으로 적합하지 않다고 판단했다.

새 구조:

- Schedule Dashboard: 전체 일정, Calendar Plan, Patch No Development Day, Calendar Changes 관리
- Development Hub: 학습, 개발일지, 핵심 코드, 문서, 블로그, 면접, 자동화 관리

생성/수정:

- 새 Notion 페이지 생성: `Unity Project A-Z - Schedule Dashboard`
- URL: `https://www.notion.so/3714bccaf9eb81cabf9edec06dd3a6da`
- 기존 페이지 상단에 Navigation / Page Role 추가
- 로컬 문서 추가: `notion/TwoPageNotionManagementStructure.md`

## 2026-05-31 22:05:00 +09:00 notion development timeline dashboard

Created a Notion timeline database to make the portfolio development process visible at a glance.

- Schedule Dashboard: https://www.notion.so/3714bccaf9eb81cabf9edec06dd3a6da
- Development Hub: https://www.notion.so/3714bccaf9eb8020bc85e39638c56d7b
- Timeline Database: https://www.notion.so/fa259baed449460693fcdfbd2d0dc4b2
- Data Source: collection://99f867b4-09cd-43c3-9f47-0b5e86cde399

Views:

- Development Timeline: timeline view by Start -> End
- Timeline Table: editable management table
- By Feature: board grouped by feature category

Initial completed records added:

- Portfolio Documentation Foundation
- MVP Scope and Learning Workflow
- Feature Toggle and Before/After Architecture
- NY Module Naming Governance
- Selective Lua Scripting Layer
- Google Calendar and Notion Schedule Workflow
- Portfolio Automation Strategy

Rule: every meaningful development item must be added as a timeline record and linked to docs, PlantUML, commits, blog drafts, and interview notes when available.

## 2026-05-31 22:30:00 +09:00 notion timeline db operational cleanup

Portfolio Development Timeline DB was expanded into an operational schedule dashboard.

Added DB properties:

- Item Type
- Priority
- Sprint
- Calendar Status
- Calendar Action
- Google Calendar
- Google Event ID
- Planned Hours
- Actual Hours
- Next Action
- Done Criteria
- No Development
- Owner
- Schedule Note
- Review Date

Added Notion views:

- 01 All Schedule Timeline
- 02 MVP 1 Roadmap
- 03 Work Queue
- 04 Calendar Linked
- 05 No Development / Patch
- 06 Status Board
- 07 Review Queue
- 08 Calendar Create Queue
- 09 Calendar Reschedule Queue

Google Calendar reflected blocks:

- 2026-06-05: 이사 + 휴가
- 2026-06-09: 마루패치 -1 buffer
- 2026-06-10: 마루패치
- 2026-06-30: 커피패치 -1 buffer
- 2026-07-01: 커피패치
- 2026-07-21: 마루 패치 -1 buffer
- 2026-07-22: 마루 패치

MVP 1 draft schedule was added from 2026-06-01 to 2026-07-05, avoiding vacation and patch NoDev dates.

Operating rule: Notion DB is the schedule intent source, Google Calendar is the actual time-block source, and Codex syncs rows marked by Calendar Action.

## 2026-05-31 22:55:00 +09:00 notion timeline korean localization

Portfolio Development Timeline DB was localized for Korean management use.

Renamed database:

- Portfolio Development Timeline -> 포트폴리오 개발 타임라인

Localized visible properties:

- Task -> 작업명
- Item Type -> 항목 유형
- Feature -> 기능
- Phase -> 단계
- Status -> 상태
- Priority -> 우선순위
- Sprint -> 스프린트
- Calendar Status -> 캘린더 상태
- Calendar Action -> 캘린더 작업
- Start / End -> 시작일 / 종료일
- Summary -> 요약
- Next Action -> 다음 작업
- Done Criteria -> 완료 기준
- Risk -> 위험도

Localized select options:

- Planned -> 예정
- In Progress -> 진행 중
- Blocked -> 차단됨
- Done -> 완료
- Concept Study -> 개념 학습
- Architecture Design -> 아키텍처 설계
- Mini Experiment -> 미니 실험
- Implementation -> 구현
- Documentation -> 문서화
- Not Scheduled -> 미등록
- Create Event -> 일정 생성
- Reschedule -> 일정 이동
- No Development -> 개발 금지

Localized views:

- 기본 관리 테이블
- 전체 개발 타임라인
- 전체 작업 테이블
- 기능별 보기
- 01 전체 일정 타임라인
- 02 MVP 1 로드맵
- 03 작업 큐
- 04 캘린더 연결됨
- 05 개발 금지 / 패치
- 06 상태 보드
- 07 리뷰 큐
- 08 캘린더 생성 큐
- 09 캘린더 이동 큐

Rule: keep Git, PlantUML, Google Calendar, MVP, ModuleHub, Before/After, Lua as English technical nouns when useful.

## 2026-05-31 23:05:00 +09:00 save-md checkpoint

/save-md checkpoint saved.

Current portfolio management state:

- Main docs repo: C:\kny\technical-portfolio-docs
- Global memory: C:\kny\CODEX_WORK_MEMORY.md
- Schedule Dashboard: https://www.notion.so/3714bccaf9eb81cabf9edec06dd3a6da
- Development Hub: https://www.notion.so/3714bccaf9eb8020bc85e39638c56d7b
- Timeline DB: https://www.notion.so/fa259baed449460693fcdfbd2d0dc4b2
- Timeline DB name: 포트폴리오 개발 타임라인

Latest confirmed Git commit:

```text
c54d29e docs: localize notion timeline database
```

Current Notion DB rule:

- Visible management labels are Korean-first.
- Keep technical nouns in English when useful: Git, PlantUML, Google Calendar, MVP, ModuleHub, Before/After, Lua.
- Use `03 작업 큐` for adding/editing schedule rows.
- Use `08 캘린더 생성 큐` for rows Codex should create in Google Calendar.
- Use `09 캘린더 이동 큐` for rows Codex should reschedule in Google Calendar.
- Use `05 개발 금지 / 패치` to check patch/vacation/no-development days.

Current primary operating flow:

```text
Notion DB = 계획과 상태 원본
Google Calendar = 실제 시간 블록
Codex = 캘린더 작업 큐를 읽고 일정 생성/수정/이동
```

Next sessions should read this file first, then inspect:

1. C:\kny\technical-portfolio-docs\CODEX_SESSION_NOTES.md
2. C:\kny\technical-portfolio-docs\notion\DevelopmentTimelineDashboard.md
3. C:\kny\technical-portfolio-docs\notion\TwoPageNotionManagementStructure.md

## 2026-06-01 save-md checkpoint

/save-md checkpoint saved.

Current active management state:

- Main docs repo: C:\kny\technical-portfolio-docs
- Global memory: C:\kny\CODEX_WORK_MEMORY.md
- Schedule Dashboard: https://www.notion.so/3714bccaf9eb81cabf9edec06dd3a6da
- Development Hub: https://www.notion.so/3714bccaf9eb8020bc85e39638c56d7b
- Timeline DB: https://www.notion.so/fa259baed449460693fcdfbd2d0dc4b2
- Timeline DB name: 포트폴리오 개발 타임라인

Current Notion operation rule:

```text
Notion DB = 계획과 상태 원본
Google Calendar = 실제 시간 블록
Codex = 캘린더 작업 큐를 읽고 일정 생성/수정/이동
```

Important Korean views:

- 기본 관리 테이블
- 전체 개발 타임라인
- 전체 작업 테이블
- 기능별 보기
- 01 전체 일정 타임라인
- 02 MVP 1 로드맵
- 03 작업 큐
- 04 캘린더 연결됨
- 05 개발 금지 / 패치
- 06 상태 보드
- 07 리뷰 큐
- 08 캘린더 생성 큐
- 09 캘린더 이동 큐

Important rule:

- Visible management labels are Korean-first.
- Keep Git, PlantUML, Google Calendar, MVP, ModuleHub, Before/After, Lua as English technical nouns when useful.
- Patch day and patch -1 day are no-development days.
- Use `03 작업 큐` for adding/editing work.
- Use `08 캘린더 생성 큐` for Google Calendar creation candidates.
- Use `09 캘린더 이동 큐` for Google Calendar reschedule candidates.

Latest saved Git commit before this checkpoint:

```text
d5c3a70 docs: save notion timeline checkpoint
```

## 2026-06-01 repository push and split strategy

User requested GitHub upload and repository split review.

Checked docs repository:

- Local repo: C:\kny\technical-portfolio-docs
- Branch: main
- Working tree was clean before strategy doc update.
- No remote existed initially.

Configured intended remote:

```text
origin https://github.com/starkshn/technical-portfolio-docs.git
```

Push attempt:

```text
git -C C:\kny\technical-portfolio-docs push -u origin main
```

Result:

```text
remote: Repository not found.
fatal: repository 'https://github.com/starkshn/technical-portfolio-docs.git/' not found
```

Conclusion:

- GitHub repository `starkshn/technical-portfolio-docs` does not exist yet.
- The local remote is already set to the intended URL.
- After creating an empty GitHub repository with that name, push can be retried.

Repository split decision:

Use three primary repositories:

1. `technical-portfolio-docs` for Markdown, PlantUML, GPT/Claude/Codex handoff docs, Notion rules, roadmap, interview notes.
2. `unity-technical-showcase` for the actual Unity project and source code.
3. `starkshn.github.io` for public portfolio site, blog index, demo links.

Do not split into more repositories during MVP unless assets or mini experiments become too heavy.

Added document:

```text
C:\kny\technical-portfolio-docs\RepositorySplitStrategy.md
```

## 2026-06-01 local repository split setup

User requested local Git repositories to be split if that is better for Markdown and project management.

Decision:

Use three local repositories only:

1. Documentation: C:\kny\technical-portfolio-docs
2. Unity Project: C:\kny\Project\Unity\unity-technical-showcase
3. Public Website: C:\kny\starkshn.github.io

Do not create a separate blog repository during MVP.
Blog drafts remain in `technical-portfolio-docs` because they are derived from study notes and architecture docs.

Created local Unity repository:

```text
C:\kny\Project\Unity\unity-technical-showcase
```

Initialized files:

- README.md
- .gitignore

Initial Unity repo commit:

```text
f4686dc chore: initialize unity technical showcase repo
```

Unity repo branch:

```text
main
```

Unity repo remote:

```text
not connected yet
```

Added docs:

```text
C:\kny\technical-portfolio-docs\LocalGitRepositoryMap.md
C:\kny\technical-portfolio-docs\RepositorySplitStrategy.md updated
```

When user provides GitHub repo URLs later, connect remotes and push.

## 2026-06-01 md-docs remote connected

User created GitHub repository:

```text
https://github.com/starkshn/md-docs.git
```

Important correction:

- Do not replace the existing `origin` remote.
- Keep the original `origin` remote for the originally planned docs repository.
- Add the new repository as an additional remote named `md-docs`.

Current remotes:

```text
origin  https://github.com/starkshn/technical-portfolio-docs.git
md-docs https://github.com/starkshn/md-docs.git
```

Push completed:

```text
git -C C:\kny\technical-portfolio-docs push -u md-docs main
```

Result:

```text
main -> md-docs/main
```

Current active GitHub docs repository:

```text
https://github.com/starkshn/md-docs
```

Future docs push command:

```powershell
git -C C:\kny\technical-portfolio-docs push md-docs main
```
