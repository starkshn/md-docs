# Local Git Repository Map

## Purpose

이 문서는 로컬에서 분리 관리하는 Git 저장소의 역할을 정의한다.

Codex, Claude, GPT 또는 다른 에이전트가 작업을 이어받을 때 먼저 이 문서를 확인한다.

## Repository Layout

### 1. Documentation Repository

Local path:

```text
C:\kny\technical-portfolio-docs
```

Current branch:

```text
main
```

Remote:

```text
origin https://github.com/starkshn/technical-portfolio-docs.git
```

Current status:

```text
Remote is configured, but GitHub repository does not exist yet.
```

Role:

- Markdown technical docs
- PlantUML
- GPT / Claude / Codex handoff docs
- Notion 운영 규칙
- Google Calendar 연동 규칙
- 포트폴리오 로드맵
- 면접 정리
- 개발 전략 문서

When to edit:

- 설계 문서를 수정할 때
- Notion 운영 규칙을 수정할 때
- `/save-md` 체크포인트를 저장할 때
- GPT/Claude에게 전달할 문서를 만들 때

### 2. Unity Project Repository

Local path:

```text
C:\kny\Project\Unity\unity-technical-showcase
```

Current branch:

```text
main
```

Remote:

```text
not connected yet
```

Initial commit:

```text
f4686dc chore: initialize unity technical showcase repo
```

Role:

- Actual Unity project
- C# runtime source
- Unity Editor tool source
- Assembly Definition files
- Demo scenes
- Shader assets
- Optimization experiments
- Rendering debug views
- Unity tests

When to edit:

- Unity 프로젝트를 생성하거나 수정할 때
- C# 코드를 작성할 때
- Unity EditorWindow를 만들 때
- Shader, scene, prefab, ScriptableObject asset을 추가할 때

### 3. Portfolio Website Repository

Local path:

```text
C:\kny\starkshn.github.io
```

Remote:

```text
origin https://github.com/starkshn/starkshn.github.io.git
```

Role:

- Public portfolio website
- Project summary pages
- Blog index links
- Demo image / video links
- Recruiter-facing portfolio navigation

When to edit:

- 공개 포트폴리오 페이지를 수정할 때
- 기술 블로그 링크를 연결할 때
- 데모 영상/GIF를 연결할 때

## Current Split Decision

Use three repositories:

```text
technical-portfolio-docs
unity-technical-showcase
starkshn.github.io
```

Do not create more repositories during MVP unless there is a clear scaling problem.

## Not Creating Separate Blog Repository Yet

Blog drafts stay inside:

```text
C:\kny\technical-portfolio-docs
```

Reason:

- 블로그 초안은 설계 문서와 강하게 연결되어 있다.
- Tistory에 옮기기 전까지는 문서 원본과 같이 관리하는 편이 좋다.
- 별도 블로그 저장소를 만들면 초반 관리 비용이 증가한다.

## Remote Connection Plan

When the user creates GitHub repositories, connect them like this:

### Documentation Repository

```powershell
git -C C:\kny\technical-portfolio-docs push -u origin main
```

### Unity Repository

```powershell
git -C C:\kny\Project\Unity\unity-technical-showcase remote add origin <Unity GitHub URL>
git -C C:\kny\Project\Unity\unity-technical-showcase push -u origin main
```

### Website Repository

Already connected:

```powershell
git -C C:\kny\starkshn.github.io remote -v
```

## Agent Rule

Before editing files, choose the repository by output type:

| Work Type | Repository |
| --- | --- |
| Architecture docs | `technical-portfolio-docs` |
| PlantUML | `technical-portfolio-docs` |
| GPT/Claude handoff | `technical-portfolio-docs` |
| Notion operation docs | `technical-portfolio-docs` |
| Unity C# code | `unity-technical-showcase` |
| Unity scenes/assets | `unity-technical-showcase` |
| Unity editor tools | `unity-technical-showcase` |
| Public site pages | `starkshn.github.io` |
| Blog/public links | `starkshn.github.io` |

## Save Rule

When the user says `/save-md`:

1. Update `C:\kny\CODEX_WORK_MEMORY.md`.
2. Update `C:\kny\technical-portfolio-docs\CODEX_SESSION_NOTES.md`.
3. Commit documentation changes in `technical-portfolio-docs`.
4. If Unity source changed, commit `unity-technical-showcase` separately.
5. If website changed, commit `starkshn.github.io` separately.
