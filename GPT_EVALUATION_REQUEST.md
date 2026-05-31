# GPT Evaluation Request - Unity Technical Showcase Portfolio

## 요청 목적

아래 설계는 게임 클라이언트 개발자 이직용 Unity 기술 포트폴리오 계획이다. 단순 게임 제작이 아니라, 클라이언트 개발자로서 시스템 설계, 툴 제작, 렌더링 이해도, 최적화 사고, 문서화 능력, 면접 설명력을 보여주는 것이 목적이다.

이 문서를 기준으로 다음 관점에서 냉정하게 평가해줘.

1. 2~5년차 게임 클라이언트 개발자 포트폴리오로 경쟁력이 있는가?
2. 범위가 과하지 않은가?
3. MVP 1순위가 현실적인가?
4. Unity 숙련도가 아직 부족한 상태에서 학습과 구현을 병행하기에 적절한가?
5. 면접관이 실행 화면과 문서만 보고 기술력을 이해할 수 있는 구조인가?
6. 구조가 너무 엔지니어링 과잉이거나 Unity스럽지 않은 부분은 없는가?
7. 추가하거나 줄여야 할 기능은 무엇인가?
8. 개발 순서와 블로그 순서가 적절한가?
9. 이 포트폴리오가 연봉 5,000~7,000만원 이직 목표에 얼마나 도움이 될 수 있는가?

---

## 현재 경력 및 목표

- 현재 게임 클라이언트 개발자로 근무 중
- 현 회사에서는 Unity(Lua) 라이브 서비스 유지보수 경험 보유
- 기존 개인 프로젝트 경험:
  - DX11 기반 Animation Tool
  - Gunfire Reborn Clone Project
  - 공통 Framework / Engine DLL
  - UE5 경험
- 목표:
  - 1~2년 내 중견 이상 게임 회사 이직
  - 목표 연봉 5,000~7,000만원
- 현재 약점:
  - Unity 개념과 숙련도가 아직 부족함
  - 실무에서 Unity를 주력으로 쓰는 상황은 아님
- 포트폴리오 방향:
  - 게임 하나를 만드는 것보다 Unity Technical Showcase 형태로 기술력을 증명

---

## 포트폴리오 핵심 방향

이 포트폴리오는 단순 RPG나 액션 게임이 아니다.

목표는 다음을 증명하는 것이다.

- 어떤 개념을 공부했는가
- 왜 그 개념이 필요한가
- Unity에서는 어떻게 적용하는가
- 기존 DX11 / Unreal 경험과 어떻게 연결되는가
- 어떤 문제를 해결했는가
- 어떤 구조로 확장 가능하게 만들었는가
- 면접에서 기술적으로 설명 가능한가

전체 사이클:

```text
개념 학습
 -> 미니 실험
 -> 포트폴리오 통합
 -> Markdown 문서화
 -> PlantUML 구조도 작성
 -> Tistory 기술 블로그 초안 작성
 -> 면접 설명 포인트 정리
```

---

## MVP 우선순위

### MVP 1순위

- Modular Skill System
- Skill Editor
- Technical Showcase Scene
- Markdown Docs
- PlantUML
- Feature Toggle System
- Before / After Comparison System
- Showcase Control Panel

### MVP 2순위

- Animation Tool
- Animation Event와 Skill 연동
- Shader Showcase

### MVP 3순위

- Optimization Showcase
- Rendering Debug View
- Tistory Blog Series 정리

처음부터 Skill, Editor, Animation, Shader, Optimization, Rendering Debug View를 모두 완성하려 하면 범위가 너무 넓다. 1차 완성 목표는 “모듈형 스킬 시스템 + 스킬 에디터 + 시연 씬”으로 좁힌다.

---

## Showcase Scene 설계

포트폴리오의 중심은 기능 목록이 아니라 하나의 기술 시연 대시보드다.

```text
Top    : Main View / Debug View / RenderTexture View 선택
Left   : Feature Module 목록과 ON/OFF Toggle
Center : Character / Combat / Shader / Animation 시연 영역
Right  : 선택 모듈 Inspector와 설정값
Bottom : Log / Metrics / Event Timeline
```

면접관이 실행했을 때 바로 보여야 하는 것:

- 어떤 기능이 켜져 있는가
- 적용 전에는 어떤 문제가 있는가
- 적용 후 무엇이 달라졌는가
- 성능 수치가 어떻게 변했는가
- 데이터와 런타임 흐름이 어떻게 분리되어 있는가
- 툴에서 어떤 값을 바꿀 수 있는가

---

## 공통 Feature Toggle 구조

모든 주요 기능은 `IFeatureModule`을 구현한다.

```text
IFeatureModule
- Initialize()
- Enable()
- Disable()
- Reset()
- Tick()
- CaptureBeforeState()
- CaptureAfterState()
- GetDebugData()
- GetMetrics()
```

중앙 관리자는 `FeatureToggleManager`다.

역할:

- 모듈 등록
- 모듈 ON/OFF
- 활성 모듈 목록 표시
- 모듈 상태 표시
- 모듈 의존성 체크
- Enable/Disable 로그 출력
- 모듈별 성능 지표 표시

예시 모듈:

```text
SkillSystemModule
SkillEditorModule
AnimationToolModule
ShaderShowcaseModule
OptimizationShowcaseModule
RenderingDebugViewModule
LODModule
CullingModule
PoolingModule
InstancingModule
DissolveShaderModule
OutlineShaderModule
```

평가 요청:

- Unity 프로젝트에서 이 정도 공통 모듈 구조가 적절한가?
- MVP 단계에서는 과한가?
- `IFeatureModule` 생명주기 중 줄이거나 바꿔야 할 것이 있는가?

---

## Before / After Comparison System

모든 핵심 기능은 적용 전/후 비교가 가능해야 한다.

```text
Before Camera
 -> Before Render Pass
 -> Before RenderTexture
 -> UI RawImage Before

After Camera
 -> After Render Pass
 -> After RenderTexture
 -> UI RawImage After

ModuleMetricsProvider
 -> MetricsPanelPresenter
 -> Metrics Diff UI
```

View Mode:

- Before Only
- After Only
- Side By Side
- Split Screen
- Overlay Difference
- Debug View

목적:

- 면접관이 코드보다 먼저 결과 차이를 볼 수 있게 함
- 최적화, 렌더링, 셰이더, 스킬 구조 개선을 시각적으로 증명
- 블로그용 캡처와 GIF 제작에도 활용

평가 요청:

- Before/After RenderTexture 비교가 기술 포트폴리오에서 설득력 있는가?
- 초기 MVP에 반드시 넣어야 하는가, 아니면 1.5단계로 미뤄야 하는가?
- URP에서 구현 난이도가 과하지 않은가?

---

## Skill System 설계

Inflearn의 `유니티 모듈식 스킬 시스템` 강의를 참고하되 그대로 복사하지 않는다.

강의는 다음 개념을 학습하기 위한 기준으로 사용한다.

- Modular Skill System
- Effect / Target / Condition / Cooldown 분리
- ScriptableObject 기반 Skill Definition
- Runtime Skill Assembly
- Editor Tool을 통한 Skill Asset 생성

우리 프로젝트에서는 다음처럼 변환한다.

```text
강의 Skill System -> SkillSystemModule
강의 Skill Editor -> SkillEditorModule
강의 Skill Data -> SkillDefinitionSO / EffectDefinitionSO / TargetingDefinitionSO / ConditionDefinitionSO
강의 Runtime Skill -> SkillInstance / SkillFactory / SkillController
강의 Tool UI -> ShowcaseControlPanel + SkillEditorPanel
강의 Debug 출력 -> ModuleMetricsProvider + MetricsView + SkillEventTimeline
강의 단일 실행 화면 -> Before / After RenderTarget Comparison View
```

Skill System Before/After:

Before:

- 하드코딩된 스킬 실행
- Target / Effect / Condition 결합
- Tool에서 수정 불가
- 실행 흐름 확인 어려움
- Validation 없음

After:

- ScriptableObject 기반 Skill Definition
- Effect / Target / Condition / Cooldown 분리
- Runtime Skill Assembly
- Tool에서 스킬 구성 변경 가능
- Skill Event Timeline으로 실행 흐름 확인
- Validation Panel로 데이터 오류 확인
- MetricsView로 실행 비용 확인

평가 요청:

- 스킬 시스템을 MVP 1순위로 두는 것이 맞는가?
- 스킬 에디터까지 포함하는 것이 너무 부담스럽지는 않은가?
- ScriptableObject 중심 데이터 설계가 포트폴리오에 잘 보이는가?
- 면접에서 설명하기 좋은 구조인가?

---

## Skill Editor 설계

Skill Editor는 Unity EditorWindow 또는 런타임 Tool Panel 형태로 구성한다.

MVP 목표:

- Skill 생성
- Effect 추가/삭제
- Targeting 선택
- Condition 추가/삭제
- Cooldown 설정
- 저장/로드
- Validation
- Preview 실행
- Skill Event Timeline 표시

Skill Tool UI:

```text
ShowcaseControlPanel
 ├─ FeatureToggleView
 ├─ SkillEditorPanel
 ├─ SkillRuntimePanel
 ├─ SkillValidationPanel
 ├─ SkillEventTimeline
 └─ MetricsView
```

평가 요청:

- EditorWindow와 런타임 패널 중 무엇을 먼저 만드는 것이 나은가?
- 기획자용 Tool UX를 보여주려면 어떤 최소 기능이 필요한가?
- Odin 없이 직접 구현하는 것이 포트폴리오에 장점인가?

---

## Animation Tool 계획

DX11 Animation Tool 경험을 Unity로 이식한다.

기능 후보:

- Animation Preview
- Animation Blend
- Bone Viewer
- Keyframe Editor
- Event Editor
- Animation Export
- Playables API 기반 Preview
- Animation Event와 Skill System 연동

평가 요청:

- MVP 2순위로 미루는 것이 적절한가?
- DX11 경험을 Unity에서 가장 잘 보여주는 최소 기능은 무엇인가?
- Keyframe Editor까지 만들면 과한가?

---

## Shader Showcase 계획

DX11에서 구현했던 렌더링/셰이더 경험을 Unity URP로 옮긴다.

기능 후보:

- Rim Light
- Dissolve
- Fresnel
- Toon
- Outline
- Distortion
- Hologram
- Post Processing

평가 요청:

- MVP 2순위가 적절한가?
- 가장 먼저 구현해야 할 셰이더 2~3개는 무엇인가?
- 포트폴리오에서 Shader Graph보다 HLSL 직접 작성이 더 강한가?

---

## Optimization Showcase 계획

실시간으로 ON/OFF 가능한 최적화 시연을 목표로 한다.

기능 후보:

- LOD
- Frustum Culling
- Occlusion Culling
- GPU Instancing
- SRP Batcher
- Object Pooling
- Addressables
- Async Loading

표시 지표:

- FPS
- Frame Time
- Draw Call
- SetPass
- GC Alloc
- Memory
- Active Object Count
- Pool Hit/Miss

평가 요청:

- MVP 3순위로 미루는 것이 맞는가?
- 가장 포트폴리오 효과가 큰 최적화 주제는 무엇인가?
- Unity Profiler 결과를 문서화하는 방식이 적절한가?

---

## Rendering Debug View 계획

카메라와 RenderTexture를 이용해 여러 디버그 뷰를 동시에 출력한다.

기능 후보:

- Main View
- Wireframe View
- Normal View
- Depth View
- Overdraw View
- Shadow View
- Multi Camera Rendering
- CommandBuffer
- URP ScriptableRendererFeature

평가 요청:

- MVP 3순위로 미루는 것이 맞는가?
- URP에서 Debug View를 직접 구현하는 난이도가 어느 정도인가?
- 기술 면접에서 강하게 보일 수 있는 Debug View는 무엇인가?

---

## 문서 구조

각 기능 폴더는 같은 템플릿을 따른다.

```text
projects/unity-technical-showcase/<feature-name>/
  00_README.md
  01_Concept.md
  02_MiniExperiment.md
  03_Architecture.md
  04_Implementation.md
  05_BlogDraft.md
  06_Interview.md
  07_BeforeAfter.md
  uml/
```

공통 구조 문서:

```text
projects/unity-technical-showcase/feature-toggle/
  FeatureToggleArchitecture.md
  BeforeAfterComparisonSystem.md
  ShowcaseControlPanelDesign.md
  RenderTargetComparisonDesign.md
  InflearnSkillSystemAdaptation.md
  uml/
```

평가 요청:

- 문서 템플릿이 과하지 않은가?
- 블로그와 포트폴리오, 면접 준비를 동시에 커버하기에 좋은가?
- 줄여야 할 문서가 있는가?

---

## 개발 로드맵 초안

### Phase 0. Unity 기초와 프로젝트 세팅

- URP 프로젝트 생성
- Assembly Definition 구조 설계
- GitHub Repository 구성
- README / docs / uml 구조 확정
- Showcase Scene 기본 UI 생성

### Phase 1. Feature Toggle Core

- `IFeatureModule`
- `FeatureModuleBase`
- `FeatureToggleManager`
- `ModuleMetricsProvider`
- `ShowcaseControlPanel` 기본 UI

### Phase 2. Skill System MVP

- SkillDefinitionSO
- Effect / Target / Condition / Cooldown 분리
- SkillFactory
- SkillInstance
- SkillController
- Runtime Skill Assembly
- 하드코딩 스킬 Before와 모듈형 스킬 After 비교

### Phase 3. Skill Editor MVP

- Skill 생성
- Effect 추가
- Target 설정
- Condition 설정
- Cooldown 설정
- Validation
- 저장/로드
- Preview

### Phase 4. Before / After Comparison

- Before Camera
- After Camera
- RenderTexture 출력
- Side By Side View
- Metrics Panel
- Skill System 비교 연결

### Phase 5. Animation / Shader 확장

- Animation Preview
- Animation Event와 Skill 연동
- Rim Light
- Dissolve
- Outline

### Phase 6. Optimization / Debug View 확장

- Object Pooling Before/After
- GPU Instancing Before/After
- LOD Before/After
- Depth / Normal Debug View

평가 요청:

- 이 순서가 맞는가?
- 초보~중급 Unity 숙련도 기준에서 위험한 단계는 어디인가?
- 6개월 / 9개월 / 12개월 기준으로 어떻게 줄이는 게 좋은가?

---

## 최종 평가 요청 답변 형식

```text
1. 전체 평가 점수 / 100
2. 가장 강한 점
3. 가장 위험한 점
4. MVP에서 반드시 남겨야 할 것
5. MVP에서 빼야 할 것
6. Unity 초보~중급 관점에서 먼저 공부할 것
7. 면접관에게 가장 잘 보일 시연 흐름
8. 블로그 글 작성 우선순위
9. 6개월 현실 버전
10. 12개월 확장 버전
11. 연봉 5,000~7,000만원 이직 목표 기준 경쟁력 평가
12. 최종 추천 방향
```
