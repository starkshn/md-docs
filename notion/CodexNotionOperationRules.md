# Codex Notion Operation Rules

## 목적

Codex와 사용자가 함께 작업한 결과를 Notion에서 누락 없이 추적하기 위한 운영 규칙이다. Codex는 작업 완료 후 단순히 “완료했다”고 말하지 않고, 어떤 항목이 완료되었고 어떤 산출물이 연결되었는지 남겨야 한다.

## Codex가 작업 후 반드시 남길 것

- 완료 체크 상태
- Git Commit 해시
- 생성 / 수정 파일
- 핵심 코드 요약
- 관련 Markdown 링크
- 관련 PlantUML 링크
- 관련 Blog Draft 또는 블로그 후보 제목
- 관련 Notion Journal 항목
- Interview Notes
- 다음 작업

## 완료 체크 규칙

기능은 아래 항목이 모두 연결되어야 완료다.

```text
Implementation
Verification
Git Commit
Markdown Documentation
PlantUML Update
Tistory Blog Draft
Notion Development Journal
Interview Notes
```

## 핵심 코드 정리 규칙

특정 기능의 핵심 코드는 다음 기준으로 정리한다.

- 문제를 해결하는 중심 클래스인가?
- 설계 패턴이 드러나는가?
- 면접관에게 보여줄 가치가 있는가?
- 일반 Unity 포트폴리오와 차별화되는가?
- 관련 문서와 UML이 있는가?

## Blog Link 규칙

블로그 링크는 Tistory 게시 전에도 추적한다.

상태 값:

- Idea
- Draft
- Review
- Published
- Update Needed

## Development Log 규칙

Codex가 의미 있는 작업을 한 날은 Development Log Index에 기록한다.

필수 항목:

- 날짜
- 주요 작업
- 배운 개념
- Git Commit
- 관련 Feature
- Journal 링크
- Blog 후보

## 최상위 질문

모든 작업은 아래 질문에 답해야 한다.

```text
이 기능이 일반 Unity 포트폴리오와 비교해서 어떤 차별성을 만들고 있는가?
```
