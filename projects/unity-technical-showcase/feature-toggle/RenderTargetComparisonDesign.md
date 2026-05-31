# RenderTarget Comparison Design

## 목적

RenderTexture를 사용해 기능 적용 전과 후의 결과를 동시에 출력한다. 렌더링, 셰이더, 최적화, 스킬 실행 결과를 같은 비교 프레임 안에서 보여주는 것이 목표다.

## 문제 정의

단일 카메라 화면만 있으면 기능 적용 차이가 흐릿해진다. 특히 Shader, Debug View, Optimization은 비교 기준이 없으면 기술적 가치가 잘 드러나지 않는다.

## 설계 방향

Before Camera와 After Camera를 같은 위치와 FOV로 동기화한다. Before는 기능 비활성 상태를, After는 기능 활성 상태를 렌더링한다. 두 RenderTexture는 UI RawImage에 연결하고, Metrics Panel에서 수치 차이를 표시한다.

## Render Target 구조

```text
Before Camera
 -> Before Render Pass
 -> Before RenderTexture

After Camera
 -> After Render Pass
 -> After RenderTexture

UI
 -> RawImage Before
 -> RawImage After
 -> Metrics Panel
```

## URP 고려 사항

- `ScriptableRendererFeature`로 Debug Pass를 추가한다.
- `ScriptableRenderPass`에서 Normal, Depth, Overdraw, Wireframe 유사 뷰를 구성한다.
- `Camera Color Target` 접근 방식은 Unity/URP 버전에 따라 달라질 수 있으므로 버전별 API 확인이 필요하다.
- Built-in Pipeline의 Replacement Shader 개념은 URP에서 Renderer Feature나 별도 Debug Material 방식으로 대체한다.

## View Mode

- Before Only: 적용 전 상태만 표시
- After Only: 적용 후 상태만 표시
- Side By Side: 좌우 비교
- Split Screen: 한 화면 분할 비교
- Overlay Difference: 차이 영역 강조
- Debug View: Normal, Depth, Overdraw 등 디버그 뷰 표시

## 적용 예시

Skill System:

- Before: 하드코딩 스킬, 결합된 Target/Effect/Condition
- After: ScriptableObject 기반 Skill Definition, Runtime Assembly, Tool 수정 가능

Shader Showcase:

- Before: 기본 Lit Material
- After: Rim Light, Dissolve, Outline, Fresnel, Toon Shading

Optimization Showcase:

- Before: Pooling, LOD, Instancing 미적용
- After: Pooling, LOD, GPU Instancing, Culling Debug 적용

Rendering Debug View:

- Before: Main Camera 결과만 표시
- After: Depth, Normal, Wireframe, Overdraw, Shadow View 동시 표시

## 구현 단계

1. `ComparisonCameraRig`로 카메라 동기화를 구현한다.
2. `RenderTargetController`에서 RenderTexture를 생성/해제한다.
3. `ComparisonViewPanel`에서 RawImage 바인딩과 View Mode를 구현한다.
4. `RenderPassController`로 Debug Pass 후보를 분리한다.
5. `MetricsPanelPresenter`로 수치 차이를 표시한다.

## 면접에서 설명할 포인트

DX11에서 Render Target을 활용해 디버그 렌더링을 구성했던 경험을 Unity의 RenderTexture와 URP Render Pass로 옮긴 구조라고 설명한다. 엔진 레벨 개념을 Unity API로 재해석했다는 점이 핵심이다.
