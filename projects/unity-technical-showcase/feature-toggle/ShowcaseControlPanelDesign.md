# Showcase Control Panel Design

## 목적

`ShowcaseControlPanel`은 Unity Technical Showcase의 메인 조작 UI다. 모든 기능 모듈을 이 패널에서 켜고 끄며, 설정을 바꾸고, Before/After View Mode를 전환하고, Metrics와 로그를 확인한다.

## 문제 정의

기술 기능이 많아질수록 시연자가 어디를 눌러야 하는지, 면접관이 무엇을 봐야 하는지 흐려진다. 따라서 포트폴리오는 기능 목록이 아니라 하나의 기술 시연 대시보드로 구성해야 한다.

## 화면 구조

```text
Top    : Main View / Debug View / RenderTexture View 선택
Left   : Feature Module 목록과 ON/OFF Toggle
Center : Character / Combat / Shader / Animation 시연 영역
Right  : 선택 모듈 Inspector와 설정값
Bottom : Log / Metrics / Event Timeline
```

## 주요 패널

```text
ShowcaseControlPanel
 ├─ FeatureToggleView
 ├─ ModuleSettingView
 ├─ ComparisonViewPanel
 ├─ MetricsView
 ├─ SkillEditorPanel
 ├─ SkillRuntimePanel
 ├─ SkillValidationPanel
 └─ SkillEventTimeline
```

## Tool UI 요구사항

- Feature Module 목록
- ON/OFF Toggle
- Before/After View Mode 선택
- 각 모듈 설정값 실시간 변경
- 현재 활성 RenderTarget 표시
- 모듈별 Metrics 표시
- Reset 버튼
- Screenshot/GIF 캡처용 상태 고정

## Skill System 패널 연결

Skill System은 강의 예제를 그대로 복사하지 않고 Showcase Control Panel의 일부로 통합한다.

- `SkillEditorPanel`: SkillDefinitionSO 생성, Effect 추가, Targeting 선택, Condition 추가, Cooldown 설정, Preview 실행
- `SkillRuntimePanel`: 장착 스킬, 실행 버튼, 쿨타임, 타겟, 실행 중 Effect 표시
- `SkillValidationPanel`: 누락 Effect, Targeting 오류, Condition 순서, Cooldown 값 검증
- `SkillEventTimeline`: 입력, 타겟 탐색, 조건 검사, Effect 실행, Animation Event, 쿨타임 시작/종료 표시
- `MetricsView`: 실행 횟수, Effect 생성 수, GC Alloc, 평균 실행 시간, 활성 스킬 수 표시

## Unity API 후보

- UGUI 또는 UI Toolkit
- `Toggle`, `Button`, `Dropdown`, `Slider`, `RawImage`
- `EditorWindow`는 Skill Editor 전용 실험 단계에서 사용하고, 런타임 시연은 인게임 패널로 구성
- `ProfilerRecorder` 기반 Metrics
- `ScriptableObject` 기반 설정 데이터

## 구현 단계

1. MVP에서는 UGUI 기반으로 빠르게 구성한다.
2. 좌측 Feature Toggle, 중앙 시연, 우측 Inspector, 하단 Log/Metrics 구조를 먼저 만든다.
3. Skill System과 Skill Editor를 연결한다.
4. Before/After Comparison View를 연결한다.
5. Animation, Shader, Optimization 모듈을 같은 패널 구조로 확장한다.

## 확장 포인트

- 모듈별 UI Presenter 분리
- Tool Preset 저장/로드
- 블로그 캡처용 UI 상태 고정
- 면접 시연용 Demo Scenario 버튼

## 면접에서 설명할 포인트

Showcase Control Panel은 포트폴리오의 UX 중심이다. 면접관이 코드를 보기 전에도 모듈 설계, 데이터 흐름, Before/After 비교, 성능 지표를 한 화면에서 확인할 수 있게 만든다.
