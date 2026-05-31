# Learning And Implementation Plan

이 문서는 Unity Technical Showcase 포트폴리오를 만들면서 어떤 개념을 먼저 공부하고, 어떤 미니 실험을 거친 뒤, 어떻게 메인 포트폴리오에 통합할지 정의한다.

## Core Rule

각 기능은 바로 구현하지 않는다. 반드시 아래 순서를 따른다.

```text
Concept Study
-> Mini Experiment
-> Portfolio Integration
-> Technical Documentation
-> Tistory Blog Draft
-> Interview Summary
```

## Skill System

### Study Topics

- Modular Architecture
- SOLID Principles
- Strategy Pattern
- Command Pattern
- Factory Pattern
- Data Driven Design
- ScriptableObject
- Runtime Skill Assembly
- Cooldown System
- Targeting System
- Condition System
- Effect Pipeline

### Unity Analysis

- ScriptableObject는 SkillDefinition, EffectDefinition, TargetingDefinition, CooldownDefinition의 데이터 원본으로 사용한다.
- Runtime에서는 ScriptableObject를 직접 실행하지 않고, Factory가 Runtime Skill Instance로 조립한다.
- MonoBehaviour 의존을 줄이고 순수 C# 런타임 모듈을 우선 설계한다.

### DX11 / Unreal Comparison

- DX11 프로젝트의 Prototype Manager와 Clone 흐름은 Unity의 ScriptableObject + Factory + Prefab/Pool 구조와 연결된다.
- Unreal의 Gameplay Ability System과 비교하면, 이 포트폴리오에서는 GAS의 축소판을 직접 설계하는 것이 목표다.

### Mini Experiments

- ScriptableObject 하나로 단일 스킬 데이터 만들기
- Target Resolver 하나만 구현하기
- Effect Module 하나만 구현하기
- Cooldown을 UI에 표시하기
- Runtime Skill Assembly 로그 출력하기

### Implementation Plan

- `SkillDefinitionSO`
- `ISkillCondition`
- `ITargetResolver`
- `ISkillEffect`
- `ICooldownPolicy`
- `SkillFactory`
- `SkillInstance`
- `SkillController`

### Blog Draft Topics

- 모듈형 스킬 시스템을 설계하는 이유
- ScriptableObject 기반 스킬 데이터 설계
- Effect / Target / Condition 분리 설계
- 런타임 스킬 조립 구조 만들기

### Interview Points

- 스킬을 상속 구조가 아니라 데이터와 모듈 조립으로 설계한 이유
- ScriptableObject와 Runtime Instance를 분리한 이유
- Target, Condition, Effect를 분리했을 때 확장성이 좋아지는 이유

## Skill Editor

### Study Topics

- Unity Editor Scripting
- Custom Editor
- EditorWindow
- SerializedObject
- SerializedProperty
- Odin 없이 Tool 만들기
- Graph View 또는 Node Editor 구조
- Asset Save / Load
- Validation System

### Unity Analysis

- EditorWindow는 스킬 목록, 모듈 편집, Validation, Preview를 담당한다.
- SerializedObject/SerializedProperty를 사용해 Undo, Prefab override, Inspector 연동성을 확보한다.
- Graph View는 필수는 아니다. 초기 버전은 Module Stack UI가 더 현실적이다.

### DX11 / Unreal Comparison

- DX11 Animation Tool에서 ImGui로 만든 내부 툴 경험을 Unity EditorWindow로 이전한다.
- Unreal Editor Utility Widget과 비교하면 Unity EditorWindow는 C# 코드 기반으로 빠르게 커스텀 가능하다.

### Mini Experiments

- SkillDefinitionSO 생성 버튼 만들기
- SerializedProperty로 Effect 리스트 편집하기
- Validation 메시지 출력하기
- AssetDatabase로 저장/로드하기

### Implementation Plan

- `SkillEditorWindow`
- `SkillAssetListView`
- `SkillModuleInspector`
- `SkillValidationPanel`
- `SkillPreviewRunner`
- `IEditorCommand` 기반 Undo/Redo 후보

### Blog Draft Topics

- Unity EditorWindow로 스킬 툴 만들기
- 스킬 데이터 검증 시스템 설계
- 기획자가 사용할 수 있는 Tool UX 설계

### Interview Points

- 런타임 코드와 에디터 코드를 asmdef로 분리한 이유
- Tool UX에서 검증/프리뷰가 중요한 이유
- Odin 없이 기본 Unity API로 툴을 만든 이유

## Animation Tool

### Study Topics

- Skeletal Animation
- Bone Hierarchy
- Local / World Transform
- Matrix
- Quaternion
- Keyframe
- Animation Clip
- Animation Event
- Animation Blending
- Mecanim
- Playables API
- Animation Rigging
- Timeline 구조

### Unity Analysis

- Unity Animator는 일반 게임 로직에는 좋지만, 포트폴리오용 Animation Preview Tool은 Playables API가 더 적합하다.
- Bone Viewer는 SceneView Gizmo와 Transform Hierarchy 분석으로 구현한다.
- Animation Event는 Skill Event와 연결해 기술적 의미를 만든다.

### DX11 / Unreal Comparison

- DX11의 `CModel -> CAnimation -> CChannel -> CBone` 구조는 Unity의 `AnimationClip -> Curve/Binding -> Transform` 구조와 비교한다.
- Unreal의 Animation Montage/Notify와 Unity Animation Event/Timeline/Playable을 비교한다.

### Mini Experiments

- PlayableGraph로 AnimationClip 하나 재생
- 두 AnimationClip Blend
- SceneView에 Bone Gizmo 표시
- Animation Event Marker 데이터 만들기

### Implementation Plan

- `AnimationPreviewWindow`
- `PlayableGraphController`
- `BoneViewerOverlay`
- `AnimationEventTrackSO`
- `AnimationSkillEventBridge`

### Blog Draft Topics

- DX11에서 구현했던 애니메이션 시스템을 Unity로 옮기기
- Bone Transform과 Quaternion 정리
- Runtime Animation Preview Tool 만들기
- Animation Event와 Skill 연동 구조

### Interview Points

- Mecanim과 Playables API의 차이
- Quaternion이 필요한 이유
- Animation Event를 Skill System과 분리/연동하는 방식

## Shader Showcase

### Study Topics

- Unity ShaderLab
- HLSL
- URP Shader 구조
- Vertex Shader
- Fragment Shader
- Normal
- Tangent Space
- Fresnel
- Rim Light
- Dissolve
- Outline
- Toon Shading
- Render Queue
- Depth
- Stencil
- GrabPass 대체 방식
- Shader Variant
- SRP Batcher 대응

### Unity Analysis

- URP에서는 ShaderGraph와 HLSL Custom Function을 병행한다.
- GrabPass는 URP에서 기본 방식이 아니므로 Opaque Texture, Camera Color Texture, RendererFeature 대체 방식을 학습한다.
- SRP Batcher를 깨는 Material/CBUFFER 구조를 주의한다.

### DX11 / Unreal Comparison

- DX11 HLSL 경험을 Unity ShaderLab/HLSL로 이전한다.
- Unreal Material Graph와 Unity ShaderGraph의 장단점을 비교한다.

### Mini Experiments

- Fresnel 단독 Shader
- Dissolve 단독 Shader
- Outline 방식 2개 비교
- Render Queue/Depth 차이 실험

### Implementation Plan

- Rim Light
- Dissolve
- Fresnel
- Toon
- Outline
- Distortion
- Hologram
- Post Processing

### Blog Draft Topics

- Unity URP Shader 구조 정리
- Fresnel / Rim Light 원리와 구현
- Dissolve Shader 구현
- Outline Shader 구현 방식 비교
- SRP Batcher 친화적인 Shader 작성법

### Interview Points

- Vertex/Fragment 단계 구분
- Depth/Stencil/Render Queue가 렌더링 결과에 미치는 영향
- SRP Batcher 대응을 고려한 Shader 작성 방식

## Optimization Showcase

### Study Topics

- Unity Profiler
- Frame Debugger
- Rendering Statistics
- CPU Bottleneck
- GPU Bottleneck
- Draw Call
- Batching
- GPU Instancing
- SRP Batcher
- LOD Group
- Frustum Culling
- Occlusion Culling
- Object Pooling
- Addressables
- Async Loading
- Memory Profiler

### Unity Analysis

- 최적화는 적용보다 측정이 먼저다.
- Profiler, Frame Debugger, Rendering Stats를 통해 병목을 분류한다.
- Object Pooling, Addressables, LOD, Culling은 ON/OFF 비교가 가능해야 한다.

### DX11 / Unreal Comparison

- DX11에서는 Draw Call, RenderTarget, Alpha sorting, Frustum을 직접 다뤘다.
- Unity에서는 엔진이 많은 부분을 처리하지만, Profiler로 원인을 추적하고 설정을 제어하는 능력이 중요하다.

### Mini Experiments

- Projectile 500개 Pooling ON/OFF 비교
- 동일 Mesh 1000개 GPU Instancing 비교
- LOD 적용 전후 비교
- Addressables async load 실험

### Implementation Plan

- `OptimizationDashboard`
- `PoolingBenchmark`
- `LODTestZone`
- `InstancingTestZone`
- `AddressablesLoadTest`
- `ProfilerMetricOverlay`

### Blog Draft Topics

- Unity Profiler로 병목 지점 찾기
- Draw Call과 Batching 정리
- LOD / Culling 최적화 실험
- Object Pooling 적용 전후 비교
- Addressables와 비동기 로딩 구조

### Interview Points

- CPU 병목과 GPU 병목을 구분하는 방법
- Draw Call과 SetPass Call의 의미
- Pooling이 GC와 프레임 스파이크에 미치는 영향

## Rendering Debug View

### Study Topics

- Camera
- RenderTexture
- Multi Camera Rendering
- CommandBuffer
- Replacement Shader
- Depth Texture
- Normal Texture
- Wireframe View
- Overdraw View
- Debug View
- Post Processing

### Unity Analysis

- RenderTexture는 카메라 출력과 디버그 뷰를 UI에 연결하는 핵심이다.
- URP에서는 Camera stacking, RendererFeature, CommandBuffer를 조합한다.
- Normal/Depth Debug View는 렌더링 이해도를 보여주는 강한 포트폴리오 장치다.

### DX11 / Unreal Comparison

- DX11의 MRT Debug RTV 구조를 Unity RenderTexture 멀티뷰로 이식한다.
- Unreal의 Buffer Visualization과 유사한 기능을 Unity에서 직접 구성한다.

### Mini Experiments

- RenderTexture로 카메라 화면 출력
- Depth Texture 표시
- Normal Debug Shader 출력
- Multi Camera View 구성

### Implementation Plan

- `DebugViewManager`
- `DebugCameraRig`
- `DebugViewPanel`
- `NormalDebugPass`
- `DepthDebugPass`
- `OverdrawDebugMaterial`

### Blog Draft Topics

- RenderTexture 기반 멀티뷰 디버거 만들기
- Unity에서 Normal / Depth Debug View 만들기
- 여러 카메라를 이용한 기술 시연 화면 구성

### Interview Points

- RenderTexture를 사용하는 이유
- Depth/Normal Texture가 후처리와 디버깅에 필요한 이유
- Debug View가 렌더링 문제 분석에 주는 가치
