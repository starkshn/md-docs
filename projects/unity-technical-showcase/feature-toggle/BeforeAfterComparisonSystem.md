# Before / After Comparison System

## 목적

각 기능의 적용 전과 적용 후를 RenderTexture 기반으로 동시에 보여준다. 포트폴리오에서 중요한 것은 결과물이 아니라 변화가 보이는 것이다. Before/After 비교는 스킬 구조, 셰이더, 최적화, 애니메이션 툴, 렌더링 디버그의 기술적 차이를 즉시 드러내는 시연 장치다.

## 문제 정의

면접관은 전체 코드를 오래 읽지 않는다. 실행 화면에서 변화가 보이지 않으면 기술 구현의 가치가 약해 보인다. 따라서 모든 핵심 기능은 Before 상태와 After 상태를 비교 가능한 형태로 제공해야 한다.

## 설계 방향

`ComparisonViewSystem`은 Before Camera와 After Camera를 관리하고, 각각의 결과를 RenderTexture로 출력한다. UI는 View Mode에 따라 Before Only, After Only, Side By Side, Split Screen, Overlay Difference, Debug View를 표시한다.

## 클래스 구조

```text
Comparison
 ├─ ComparisonViewSystem
 ├─ ComparisonCameraRig
 ├─ RenderTargetController
 ├─ RenderPassController
 └─ MetricsPanelPresenter
```

## 데이터 흐름

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

## UI 흐름

1. 사용자가 기능 모듈을 선택한다.
2. Before 상태를 캡처한다.
3. 기능 적용 전 화면을 Before RenderTexture에 출력한다.
4. 모듈을 활성화한다.
5. After 상태를 캡처한다.
6. 기능 적용 후 화면을 After RenderTexture에 출력한다.
7. Metrics Panel에 성능 차이를 표시한다.

## View Mode

- `BeforeOnly`
- `AfterOnly`
- `SideBySide`
- `SplitScreen`
- `OverlayDifference`
- `DebugView`

## Unity API 후보

- `Camera.targetTexture`
- `RenderTexture`
- `RawImage`
- URP `ScriptableRendererFeature`
- URP `ScriptableRenderPass`
- `CommandBuffer`
- `Camera Color Target`
- Debug Material
- Replacement Shader 대체 구조

## DX11 경험과의 연결점

DX11에서 Render Target을 분리해 디버그 뷰나 후처리 결과를 확인하던 방식과 유사하다. Unity에서는 직접 SwapChain과 RTV를 다루기보다는 Camera, RenderTexture, URP Render Pass를 사용해서 같은 개념을 구성한다.

## 구현 단계

1. Before/After Camera Rig를 만든다.
2. RenderTexture 생성과 해제를 `RenderTargetController`로 분리한다.
3. `ComparisonViewSystem`에서 View Mode 전환을 구현한다.
4. `MetricsPanelPresenter`로 Before/After 지표 차이를 표시한다.
5. Skill System부터 Before/After 비교에 연결한다.
6. Shader, Optimization, Rendering Debug View로 확장한다.

## 확장 포인트

- Overlay Difference 픽셀 차이 시각화
- Screenshot/GIF 캡처
- 블로그용 Before/After 이미지 저장
- 프로파일링 결과 CSV 저장
- View Mode 프리셋 저장

## 면접에서 설명할 포인트

Before/After 구조는 기술 구현을 “보이게” 만드는 장치다. 특히 최적화와 렌더링 기능은 코드 설명보다 시각적 비교와 수치 비교가 설득력이 높다.
