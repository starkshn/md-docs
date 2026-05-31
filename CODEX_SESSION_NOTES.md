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
