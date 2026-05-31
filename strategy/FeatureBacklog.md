# Feature Backlog

## 목적

기능 아이디어가 계속 늘어나면 포트폴리오가 완성되기 전에 범위가 무너진다. Backlog는 Must / Should / Could / Won't 기준으로 범위를 통제하기 위한 문서다.

## Must

반드시 MVP에 포함한다.

- Modular Skill System
- Skill Tool / Skill Editor
- Technical Showcase Scene
- Feature Toggle System
- Before/After Comparison System
- Metrics View
- Markdown Docs
- PlantUML
- Interview Notes

## Should

MVP 이후 우선 확장한다.

- Animation Tool MVP
- Animation Event와 Skill 연동
- Shader Showcase MVP
- Render Debug View 기본 구조
- Object Pooling Before/After
- DX11 -> Unity Mapping 문서
- Recruiter Summary 문서

## Could

시간이 충분할 때만 추가한다.

- Node Graph Skill Editor
- Visual Scripting 유사 구조
- 고급 Timeline Editor
- Overlay Difference 고도화
- GIF 자동 캡처 도구
- Addressables 심화 실험
- Shader Variant 관리 실험

## Won't

현재 포트폴리오 목적과 맞지 않으므로 넣지 않는다.

- 서버
- DB
- 로그인
- 매칭
- 멀티플레이
- 인벤토리 시스템 중심 포트폴리오
- 퀘스트 시스템 중심 포트폴리오
- ECS
- DOTS
- 대규모 Addressables 심화 구조

## Backlog 운영 규칙

- Must가 끝나기 전 Could를 시작하지 않는다.
- Won't 항목은 면접에서 물어보면 “이번 포트폴리오의 목적과 맞지 않아 제외했다”고 설명한다.
- 새 아이디어는 바로 구현하지 않고 먼저 Backlog에 넣는다.
- 매주 Weekly Review에서 Backlog 승격/보류/제외를 판단한다.

## Selective Lua Scripting Layer Backlog Rule

`Selective Lua Scripting Layer`는 MVP 필수 기능이 아니다. Skill System, Skill Tool, Before/After Comparison, ModuleHub가 안정화된 이후 확장 기능으로 구현한다.

우선순위:

1. Skill System
2. Skill Tool
3. Before / After Comparison
4. ModuleHub
5. Selective Lua Scripting Layer

Backlog 위치: `Should` 또는 `Could` 사이. 라이브 서비스 Hotfix / Script Layer 설명 가치가 있으므로 완전 제외하지는 않는다. 단, Core Framework나 Tool 구현보다 먼저 진행하지 않는다.

Lua 적용 대상:

- Skill Damage Formula
- Skill Condition
- Buff Trigger
- Effect Parameter Calculation
- AI Test Behavior
- Debug Command

Lua 제외 대상:

- ModuleHub
- Core Framework
- Rendering
- Animation Tool Core
- Editor Tool Core
- Optimization System
- Comparison Framework
