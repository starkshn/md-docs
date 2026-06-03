# Git PlantUML Guide

## Purpose

이 문서는 포트폴리오 Git 저장소 구조를 PlantUML로 설명하기 위한 가이드다.

문서, Unity 프로젝트, 공개 포트폴리오 사이트를 어떤 기준으로 나누고, Codex / Claude / GitHub / Notion이 어떻게 연결되는지 한눈에 파악하는 것이 목적이다.

## Diagram Location

```text
C:\kny\technical-portfolio-docs\shared\uml\git
```

## Diagrams

### 1. PortfolioGitRepositoryMaster.puml

Purpose:

- 전체 Git 저장소 구조를 한눈에 보여준다.
- 로컬 저장소와 GitHub remote의 관계를 설명한다.
- Codex, Claude, NY, 면접관/방문자가 어떤 저장소를 바라보는지 설명한다.

Shows:

- `technical-portfolio-docs`
- `unity-technical-showcase`
- `starkshn.github.io`
- `md-docs`
- 향후 Unity GitHub repository
- Codex / Claude 협업 구조

### 2. PortfolioGitWorkflow.puml

Purpose:

- 작업 유형별 Git 흐름을 보여준다.
- 문서 작업, Unity 작업, 공개 사이트 작업을 분기해서 관리한다.

Shows:

- 문서 작업 시 `technical-portfolio-docs`에 commit / push
- Unity 작업 시 `unity-technical-showcase`에 commit
- 공개 페이지 작업 시 `starkshn.github.io`에 commit / push
- `/save-md`와 `CODEX_WORK_MEMORY.md` 갱신 흐름

### 3. ClaudeCodexGitSync.puml

Purpose:

- 집 Codex와 회사 Claude가 같은 문서 맥락을 공유하는 과정을 보여준다.

Shows:

- 집에서 Codex 작업
- `md-docs`로 push
- 회사에서 clone / pull
- Claude가 `CLAUDE.md`와 세션 문서를 읽고 작업
- 회사 작업 후 다시 push
- 집에서 pull 후 이어서 작업

### 4. GitRepositoryResponsibility.puml

Purpose:

- 각 Git 저장소의 책임 경계를 설명한다.

Shows:

- `technical-portfolio-docs`가 관리해야 하는 것
- `unity-technical-showcase`가 관리해야 하는 것
- `starkshn.github.io`가 관리해야 하는 것
- 각 저장소에 넣으면 안 되는 것

### 5. GitRemoteConnectionPlan.puml

Purpose:

- 현재 remote 연결 상태와 나중에 연결할 Unity remote 계획을 보여준다.

Shows:

- `origin`: 기존 계획 remote
- `md-docs`: 현재 활성 문서 remote
- Unity repository: 나중에 GitHub URL을 받아 연결
- `starkshn.github.io`: 이미 연결된 공개 사이트 remote

## Current Git Structure

```text
technical-portfolio-docs
  remote:
    origin  = https://github.com/starkshn/technical-portfolio-docs.git
    md-docs = https://github.com/starkshn/md-docs.git

unity-technical-showcase
  remote:
    not connected yet

starkshn.github.io
  remote:
    origin = https://github.com/starkshn/starkshn.github.io.git
```

## Operating Rule

```text
문서 / 설계 / PlantUML / Notion 규칙
→ technical-portfolio-docs

Unity C# / 씬 / 셰이더 / 에디터 툴
→ unity-technical-showcase

공개 포트폴리오 / 블로그 링크 / 데모 링크
→ starkshn.github.io
```

## Future Work

Unity 프로젝트 GitHub 저장소를 만들면 아래 다이어그램을 업데이트한다.

```text
shared/uml/git/GitRemoteConnectionPlan.puml
shared/uml/git/PortfolioGitRepositoryMaster.puml
```

업데이트할 내용:

- Unity repository GitHub URL
- Unity remote 이름
- Unity push 명령
- 실제 source / docs / site 간 연결 흐름
