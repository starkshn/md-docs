# Feature Toggle Architecture

## 목적

Unity Technical Showcase의 모든 주요 기능을 독립 모듈로 만들고, 런타임에서 ON/OFF할 수 있게 만든다. 이 구조의 목적은 기능을 많이 나열하는 것이 아니라, 면접관이 실행 화면만 보고도 각 기능의 필요성, 적용 전 문제, 적용 후 개선점, 성능 변화, 모듈 독립성을 바로 이해하게 만드는 것이다.

## 문제 정의

기술 포트폴리오가 단순 기능 모음으로 끝나면 강점이 잘 보이지 않는다. 스킬, 애니메이션, 셰이더, 최적화, 렌더링 디버그가 각각 따로 동작하면 시연 흐름이 끊기고, 코드 구조도 면접에서 설명하기 어렵다.

따라서 모든 기능은 같은 생명주기와 같은 제어 방식을 가져야 한다.

## 설계 방향

모든 기능은 `IFeatureModule`을 구현한다. `FeatureToggleManager`는 모듈 등록, 활성화, 비활성화, 의존성 확인, 상태 표시, 로그 기록, 성능 지표 수집을 담당한다.

핵심 생명주기:

- `Initialize`
- `Enable`
- `Disable`
- `Reset`
- `Tick`
- `CaptureBeforeState`
- `CaptureAfterState`
- `GetDebugData`
- `GetMetrics`

## 클래스 구조

```text
Core
 ├─ IFeatureModule
 ├─ FeatureModuleBase
 ├─ FeatureToggleManager
 ├─ ModuleDependencyResolver
 └─ ModuleMetricsProvider

Modules
 ├─ SkillSystemModule
 ├─ SkillEditorModule
 ├─ AnimationToolModule
 ├─ ShaderShowcaseModule
 ├─ OptimizationShowcaseModule
 └─ RenderingDebugViewModule
```

세부 최적화나 셰이더 기능도 독립 모듈이 될 수 있다.

```text
LODModule
CullingModule
PoolingModule
InstancingModule
DissolveShaderModule
OutlineShaderModule
```

## 데이터 흐름

1. `ShowcaseControlPanel`에서 사용자가 모듈 ON/OFF를 선택한다.
2. `FeatureToggleManager`가 모듈 존재 여부와 의존성을 확인한다.
3. 활성화 전 `CaptureBeforeState`를 호출한다.
4. `Enable`을 호출하고 모듈 상태를 갱신한다.
5. 활성화 후 `CaptureAfterState`를 호출한다.
6. `ModuleMetricsProvider`가 FPS, GC, Draw Call, 실행 시간 등 지표를 수집한다.
7. UI는 모듈 상태, 로그, Metrics, Before/After 결과를 표시한다.

## UI 흐름

`ShowcaseControlPanel`은 포트폴리오의 메인 조작 지점이다.

- Feature Module 목록
- ON/OFF Toggle
- 모듈별 상태 표시
- 활성 모듈 목록
- 의존성 경고
- 모듈별 설정 패널
- Metrics 표시
- Reset

## Unity API 후보

- `MonoBehaviour` 또는 별도 Service 객체 기반 모듈 호스트
- `ScriptableObject` 기반 모듈 메타데이터
- `UnityEvent` 또는 C# event 기반 상태 변경 알림
- `ProfilerRecorder` 기반 성능 지표 수집
- `Assembly Definition` 기반 Runtime / Editor / UI 분리

## DX11 경험과의 연결점

DX11 Framework의 Manager 구조와 유사하게 중앙 관리자가 모듈 생명주기를 통제한다. 단, Unity에서는 엔진 루프를 직접 소유하지 않으므로 `MonoBehaviour` 업데이트 루프, Unity Profiler, RenderTexture, URP 확장 지점을 활용해서 Unity 방식으로 재설계한다.

## 구현 단계

1. `IFeatureModule`과 `FeatureModuleBase`를 만든다.
2. `FeatureToggleManager`를 구현한다.
3. 모듈 등록과 ON/OFF UI를 연결한다.
4. `ModuleDependencyResolver`로 의존성 검사를 추가한다.
5. `ModuleMetricsProvider`로 공통 Metrics 수집을 붙인다.
6. Skill System MVP부터 실제 모듈로 연결한다.
7. Animation, Shader, Optimization, Debug View로 확장한다.

## 확장 포인트

- 모듈별 ScriptableObject 설정 파일
- 모듈 프리셋 저장/로드
- 모듈 조합별 성능 비교
- Screenshot/GIF 캡처용 상태 고정
- Tistory 블로그용 Before/After 이미지 자동 수집

## 면접에서 설명할 포인트

이 구조는 “기능을 많이 만들었다”가 아니라 “모든 기능을 동일한 생명주기와 제어 방식으로 통합했다”는 점을 보여준다. 특히 Unity 숙련도가 부족한 상태에서 시작하더라도, DX11 엔진 제작 경험을 Unity의 모듈형 아키텍처로 재해석했다는 설명이 가능하다.

## NY 네이밍 적용 메모

초기 문서의 `IFeatureModule`, `FeatureToggleManager`, `ModuleMetricsProvider` 개념은 최종 구현에서 다음 이름으로 사용한다.

| 초기 개념명 | 최종 구현명 |
| --- | --- |
| `IFeatureModule` | `INY_Module` |
| `IFeatureToolModule` | `INY_ToolModule` |
| `IComparableModule` | `INY_ComparableModule` |
| `FeatureToggleManager` | `NY_Core_ModuleHub` |
| `ModuleRegistry` | `NY_Core_ModuleRegistry` |
| `ModuleMetricsProvider` | `NY_Core_ModuleMetricsCenter` |
| `ShowcaseControlPanel` | `NY_Tool_ModuleDashboard` |
| `ComparisonViewSystem` | `NY_Comparison_ViewSystem` |

최신 네이밍 규칙은 `docs/conventions/NamingConvention.md`와 `projects/unity-technical-showcase/framework/ModuleNamingConvention.md`를 따른다.
