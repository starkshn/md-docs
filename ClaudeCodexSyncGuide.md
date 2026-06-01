# Claude and Codex Sync Guide

## Purpose

집에서는 Codex를 사용하고, 회사에서는 Claude를 사용할 수 있다.

두 에이전트가 같은 포트폴리오 맥락을 이해하려면 GitHub 저장소와 공통 문서를 기준으로 동기화해야 한다.

## Source of Truth

현재 문서 원본 저장소:

```text
https://github.com/starkshn/md-docs
```

로컬 문서 저장소:

```text
C:\kny\technical-portfolio-docs
```

이 저장소가 다음 내용을 관리한다.

- 포트폴리오 전체 설계
- Markdown 기술 문서
- PlantUML
- Notion 운영 규칙
- Google Calendar 연동 규칙
- GPT / Claude / Codex 전달 문서
- 개발 로드맵
- 면접 정리

## Company PC Setup

회사 PC에서는 아래 저장소를 clone한다.

```powershell
git clone https://github.com/starkshn/md-docs.git
```

Claude 세션 시작 시 먼저 읽게 할 파일:

```text
CLAUDE.md
README.md
CODEX_SESSION_NOTES.md
LocalGitRepositoryMap.md
RepositorySplitStrategy.md
PortfolioStudyMasterPlanForGPT.md
notion/DevelopmentTimelineDashboard.md
```

## Claude Start Prompt

회사에서 Claude에게 처음 전달할 프롬프트:

```text
이 repo는 Unity Technical Showcase 포트폴리오 문서 원본이다.

먼저 아래 파일을 읽고 현재 운영 규칙과 프로젝트 상태를 파악해라.

- CLAUDE.md
- README.md
- CODEX_SESSION_NOTES.md
- LocalGitRepositoryMap.md
- RepositorySplitStrategy.md
- PortfolioStudyMasterPlanForGPT.md
- notion/DevelopmentTimelineDashboard.md

이후 작업은 기존 문서 구조, 네이밍 규칙, Notion/Calendar 운영 규칙을 유지해서 진행해라.
```

## Home Codex Workflow

집에서 Codex 작업 전:

```powershell
git -C C:\kny\technical-portfolio-docs pull md-docs main
```

작업 후:

```powershell
git -C C:\kny\technical-portfolio-docs add .
git -C C:\kny\technical-portfolio-docs commit -m "docs: ..."
git -C C:\kny\technical-portfolio-docs push md-docs main
```

또는 `/save-md`를 사용한다.

## Company Claude Workflow

회사에서 Claude 작업 전:

```powershell
git pull
```

Claude에게 요청:

```text
방금 pull 받은 최신 문서를 기준으로 현재 포트폴리오 상태를 요약하고,
오늘 작업해야 할 내용을 CODEX_SESSION_NOTES.md와 notion/DevelopmentTimelineDashboard.md 기준으로 정리해라.
```

작업 후:

```powershell
git add .
git commit -m "docs: ..."
git push
```

## Conflict Prevention

Codex와 Claude가 같은 파일을 동시에 수정하면 충돌이 발생할 수 있다.

역할을 나누어 충돌을 줄인다.

### Codex Main Role

- 구조 설계
- Notion / Calendar 운영
- Git 정리
- Unity 구현 준비
- Architecture / Implementation 문서
- 로컬 저장소 관리

Codex가 주로 관리하는 파일:

```text
CODEX_SESSION_NOTES.md
LocalGitRepositoryMap.md
RepositorySplitStrategy.md
notion/*
projects/.../03_Architecture.md
projects/.../04_Implementation.md
```

### Claude Main Role

- 문서 리뷰
- 블로그 초안 개선
- 면접 답변 정리
- 설명 흐름 다듬기
- 독자가 이해하기 좋은 문장 개선

Claude가 주로 관리하는 파일:

```text
projects/.../05_BlogDraft.md
projects/.../06_Interview.md
GPT_EVALUATION_REQUEST.md
PortfolioStudyMasterPlanForGPT.md
workflow/*
strategy/*
```

## Unity Project Repository

나중에 실제 Unity 프로젝트 GitHub 저장소를 만들면 별도로 연결한다.

현재 로컬 Unity 저장소:

```text
C:\kny\Project\Unity\unity-technical-showcase
```

현재 상태:

```text
Local Git repository exists.
Remote is not connected yet.
```

GitHub 저장소를 만든 뒤 연결:

```powershell
git -C C:\kny\Project\Unity\unity-technical-showcase remote add origin <Unity Project GitHub URL>
git -C C:\kny\Project\Unity\unity-technical-showcase push -u origin main
```

## Final Rule

문서 동기화는 `md-docs`를 기준으로 한다.

Unity 실제 소스 동기화는 나중에 별도 Unity 프로젝트 GitHub 저장소를 만든 뒤 연결한다.

```text
md-docs = 문서 / 설계 / 블로그 초안 / 면접 정리
unity-technical-showcase = 실제 Unity 프로젝트 / C# / 씬 / 에셋
starkshn.github.io = 공개 포트폴리오 사이트
```
