# Repository Split Strategy

## Purpose

Unity Technical Showcase 포트폴리오는 산출물이 여러 종류로 나뉜다.

하나의 Git 저장소에 전부 넣으면 관리가 편해 보이지만, 시간이 지나면 다음 문제가 생긴다.

- Unity 프로젝트 파일과 문서 변경 이력이 섞인다.
- 블로그/포트폴리오 사이트 배포 이력과 개발 이력이 섞인다.
- GPT, Claude, Codex에게 전달할 문서 원본을 찾기 어려워진다.
- Unity `Library`, `Temp`, 빌드 산출물, 대용량 에셋 관리 규칙이 문서 저장소와 충돌한다.

따라서 Git 저장소는 역할별로 분리한다.

## Recommended Repositories

### 1. technical-portfolio-docs

Recommended GitHub repository:

```text
https://github.com/starkshn/technical-portfolio-docs
https://github.com/starkshn/md-docs
```

Local path:

```text
C:\kny\technical-portfolio-docs
```

Role:

- 프로젝트 분석 문서
- Unity 포트폴리오 설계 문서
- Markdown Technical Docs
- PlantUML
- GPT / Claude / Codex 전달 문서
- Notion 운영 규칙
- 개발 로드맵
- 면접 정리

This repository is the source of truth for documentation.

Current push status:

```text
origin remains configured for technical-portfolio-docs.
md-docs is configured and pushed successfully.
```

Current active push command:

```powershell
git -C C:\kny\technical-portfolio-docs push md-docs main
```

### 2. unity-technical-showcase

Recommended GitHub repository:

```text
https://github.com/starkshn/unity-technical-showcase
```

Recommended local path:

```text
C:\kny\Project\Unity\unity-technical-showcase
```

Role:

- Actual Unity project
- C# source code
- Assembly Definition files
- Runtime modules
- Editor tools
- Demo scenes
- Shader assets
- Test scenes
- Package configuration

Rules:

- Use Unity `.gitignore`.
- Use Git LFS if large assets are added.
- Do not commit `Library`, `Temp`, `Obj`, `Build`, `Logs`, `UserSettings`.
- Keep documentation summaries in the repo, but keep full architecture docs in `technical-portfolio-docs`.

Current local status:

```text
Local Git repository initialized.
Branch: main
Remote: not connected yet
Initial commit: f4686dc chore: initialize unity technical showcase repo
```

### 3. starkshn.github.io

Existing GitHub repository:

```text
https://github.com/starkshn/starkshn.github.io
```

Local path:

```text
C:\kny\starkshn.github.io
```

Role:

- Portfolio website
- Project landing pages
- Blog index links
- Public portfolio navigation
- Demo video/GIF links

This repository should consume summaries and links from `technical-portfolio-docs`, not duplicate every document.

## Optional Repositories

### unity-technical-showcase-labs

Use only if mini experiments become noisy.

Role:

- Throwaway experiments
- Small test scenes
- Shader tests
- EditorWindow prototypes
- Playables API experiments

Recommendation:

Do not create this repository at the beginning.

Keep mini experiments inside the Unity project under a clear folder until they become too large.

### technical-portfolio-assets

Use only if videos, GIFs, screenshots, and large rendered assets become heavy.

Role:

- Demo GIFs
- Portfolio screenshots
- Rendered videos
- Blog images

Recommendation:

Avoid this repository unless GitHub Pages or the Unity repository becomes too heavy.

## Final Decision

Use three primary repositories:

```text
technical-portfolio-docs
unity-technical-showcase
starkshn.github.io
```

Do not split more than this at the MVP stage.

Blog drafts stay in `technical-portfolio-docs` during MVP.

Reason:

- Blog drafts are derived from study notes and architecture docs.
- Keeping them together avoids duplicated Markdown management.
- Public blog links can later be surfaced through `starkshn.github.io`.

## Responsibility Boundary

| Repository | Owns | Does Not Own |
| --- | --- | --- |
| technical-portfolio-docs | Markdown, PlantUML, plans, Notion rules, interview docs | Unity source, build output |
| unity-technical-showcase | Unity source, scenes, packages, tests, shaders | Long-form planning docs |
| starkshn.github.io | Public website, portfolio pages, blog links | Raw Unity project, internal work logs |

## Workflow

```text
Concept / Architecture
↓
technical-portfolio-docs
↓
Unity Implementation
↓
unity-technical-showcase
↓
Demo GIF / Blog Summary
↓
starkshn.github.io
```

## Codex Rule

When working with Git:

1. Documentation changes go to `technical-portfolio-docs`.
2. Unity source changes go to `unity-technical-showcase`.
3. Public portfolio site changes go to `starkshn.github.io`.
4. Do not mix Unity source code into the docs repository.
5. Do not use the website repository as the source of truth for technical documentation.

## Current Action Required

The docs repository is ready locally.

GitHub push target currently in use:

```text
https://github.com/starkshn/md-docs
```

Push command:

```powershell
git -C C:\kny\technical-portfolio-docs push md-docs main
```
