# Portfolio Risk Log

## 목적

이 포트폴리오의 가장 큰 위험은 기술 난이도보다 범위 증가와 완성 실패다. Risk Log는 위험을 미리 기록하고 대응 방안을 정하기 위한 문서다.

## Risk 001 - 기능 범위가 계속 증가함

문제:

```text
Skill, Editor, Animation, Shader, Optimization, Debug View가 모두 중요해 보여서 범위가 계속 늘어날 수 있다.
```

대응:

```text
MVP 1순위는 Skill System, Skill Tool, Showcase Scene, Feature Toggle, Before/After, Docs로 제한한다.
Backlog의 Must가 끝나기 전 Could 기능을 시작하지 않는다.
```

## Risk 002 - Shader 공부에 시간 과다 소모

문제:

```text
Shader는 깊게 들어가면 URP, SRP Batcher, RenderPass, Variant까지 확장되어 시간이 많이 든다.
```

대응:

```text
Shader Showcase는 초기에는 Rim, Fresnel, Dissolve, Outline, Toon 중 3개만 구현한다.
SRP Batcher는 문서화와 간단 검증 수준으로 제한한다.
```

## Risk 003 - Unity 숙련도 부족으로 Tool 구현이 지연됨

문제:

```text
EditorWindow, SerializedObject, UI Toolkit, UGUI, AssetDatabase 개념이 부족하면 Tool 구현이 지연될 수 있다.
```

대응:

```text
먼저 런타임 Skill Panel로 MVP를 만들고, EditorWindow는 별도 미니 실험 후 통합한다.
```

## Risk 004 - 문서화가 구현 속도를 과하게 늦춤

문제:

```text
모든 내용을 완성도 높은 블로그 글로 만들려고 하면 구현이 멈출 수 있다.
```

대응:

```text
구현 중에는 Blog Draft 수준으로만 작성한다. 최종 게시용 글은 MVP 기능 단위가 닫힌 뒤 정리한다.
```

## Risk 005 - Before/After RenderTexture 구조가 초기 MVP를 늦춤

문제:

```text
RenderTexture, Camera, URP RenderPass 구조가 Skill System MVP보다 먼저 복잡해질 수 있다.
```

대응:

```text
초기에는 UI 상태 비교와 Metrics 비교로 시작하고, RenderTexture 비교는 Phase 1.5로 분리한다.
```

## Risk 006 - 포트폴리오가 개발자에게만 이해되고 면접관에게는 복잡함

문제:

```text
구조가 강해도 실행 화면에서 무엇이 중요한지 바로 보이지 않을 수 있다.
```

대응:

```text
각 기능마다 Recruiter Summary와 30초 GIF, 3분 영상 흐름을 만든다.
```

## Risk 007 - 강의 구조를 따라치기로 오해받음

문제:

```text
Inflearn 강의를 참고한 Skill System이 단순 클론으로 보일 수 있다.
```

대응:

```text
강의 원본 구조, 우리 프로젝트 적용 구조, 변경 이유, Feature Module 통합, Before/After 비교를 반드시 문서화한다.
```
