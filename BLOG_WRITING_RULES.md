# Technical Blog Writing Rules

이 문서는 기술 블로그용 Markdown을 작성하거나 수정할 때 적용하는 공통 규칙이다.

## 기본 방향

기술 블로그 글은 개인 포트폴리오 문서가 아니라 공개 학습/기술 정리 글로 작성한다.

따라서 글의 중심은 다음이다.

- 개념 설명
- 동작 원리
- 예제 코드
- 구조 비교
- 시행착오와 정리
- 참고 문서

## 제외할 내용

기술 블로그용 Markdown에서는 아래 내용을 제거한다.

- 개인 포트폴리오 프로젝트명
- 개인 이름 또는 이니셜 기반 접두사
- 특정 개인 저장소/로컬 경로
- 면접에서 말하기 좋은 답변 같은 면접 전용 섹션
- 채용/이직 전략 문구
- 내부 작업 관리 문구

예시:

```text
제거 대상:
NY.Core
UnityTechnicalShowcase에서는 어떻게 쓸까
면접에서 말하기 좋은 답변
현재 포트폴리오 프로젝트에서는

블로그용 대체:
Core.dll
일반적인 asmdef 구성 예시
마무리
Unity 프로젝트에서는
```

## PlantUML 규칙

블로그에 들어가는 PlantUML은 다크 모드에서도 읽히도록 색상을 명시한다.

공통 설정:

```plantuml
skinparam backgroundColor #0D1117
skinparam shadowing false
skinparam dpi 180
skinparam defaultFontName Malgun Gothic
skinparam defaultFontColor white
skinparam ArrowColor #58A6FF
skinparam ArrowFontColor white
skinparam ArrowThickness 3
skinparam rectangle {
    BackgroundColor #161B22
    BorderColor #58A6FF
    BorderThickness 2
    FontColor white
    FontSize 16
    RoundCorner 15
}
skinparam title {
    FontColor white
    FontSize 22
}
```

주의사항:

- 화살표 라벨이 검은색으로 보이면 `ArrowFontColor white`를 추가한다.
- 클래스명, 변수명, API 이름은 영어를 유지한다.
- 설명 문구는 한국어로 작성해도 된다.
- 개인 접두사는 사용하지 않는다.

## 글 구조 권장안

```text
1. 들어가며
2. 용어 정리
3. 기본 동작 흐름
4. 예제 코드
5. 내부 동작 설명
6. 비교 정리
7. 주의할 점
8. 마무리
9. 참고 문서
```

## 포트폴리오 문서와의 구분

포트폴리오 문서에는 개인 프로젝트 구조, 설계 의도, 면접 설명 포인트를 포함할 수 있다.

기술 블로그 문서에는 그런 내용을 직접 넣지 않는다.

필요하다면 같은 주제를 아래처럼 분리한다.

```text
포트폴리오 문서:
projects/unity-technical-showcase/AssemblyDefinitionPlan.md

블로그 문서:
projects/unity-technical-showcase/UnityCSharpCompilationRuntimeBlogDraft.md
```
