@'
# Unity Technical Showcase Portfolio Design

## 목표

목표는 게임 완성품보다 기술 검증 가능한 Unity Technical Showcase를 만드는 것이다. 면접관이 5~10분 안에 다음을 확인할 수 있어야 한다.

- Unity 런타임 구조 설계 능력
- 데이터 기반 Skill System 설계 능력
- Editor Tool 제작 능력
- Animation/Rendering/Optimization 이해도
- DX11 자체 엔진 경험을 Unity로 번역하는 능력
- 문서화와 UML로 복잡한 구조를 설명하는 능력

## 전체 아키텍처

프로젝트는 `Runtime`, `Editor`, `Demo`, `Tools`, `Content`를 명확히 분리한다.

핵심 모듈:

- Core
- Character
- Skill Runtime
- Skill Editor
- Animation Tool
- Shader Showcase
- Optimization Showcase
- Rendering Debug View
- UI
- Data
- Infrastructure

## 권장 Unity 버전 / 렌더 파이프라인

- Unity 2022.3 LTS 또는 2023 LTS
- URP 권장
- ShaderGraph + HLSL Custom Function 병행
- Addressables 사용
- Input System 사용
- UI Toolkit은 Editor Tool에 우선 사용, Runtime UI는 uGUI 또는 UI Toolkit 중 하나로 통일

Unity 개념 숙련도가 아직 부족하다면 HDRP보다 URP가 맞다. 포트폴리오 목적상 렌더링 이론을 보여주되, 프로젝트 완성 리스크를 낮춰야 한다.

## 폴더 구조

```text
Assets/
  _Project/
    Runtime/
      Core/
      Character/
      Skills/
        Data/
        Runtime/
        Targeting/
        Effects/
        Cooldowns/
        Conditions/
        Execution/
      Animation/
      Rendering/
      Optimization/
      UI/
      Infrastructure/
    Editor/
      SkillEditor/
      AnimationTool/
      DebugTools/
    Demo/
      Scenes/
      Prefabs/
      Profiles/
    Art/
      Characters/
      VFX/
      Materials/
      Textures/
    Shaders/
      HLSL/
      ShaderGraphs/
      Includes/
    Addressables/
    Tests/
      EditMode/
      PlayMode/
Docs/
  Architecture/
  UML/
  Guides/
```

## Assembly Definition 구조

```text
Project.Core.asmdef
Project.Character.asmdef
Project.Skills.Runtime.asmdef
Project.Animation.Runtime.asmdef
Project.Rendering.Runtime.asmdef
Project.Optimization.Runtime.asmdef
Project.UI.Runtime.asmdef
Project.Infrastructure.asmdef
Project.Skills.Editor.asmdef
Project.Animation.Editor.asmdef
Project.Debug.Editor.asmdef
Project.Tests.EditMode.asmdef
Project.Tests.PlayMode.asmdef
```

의존 방향:

- `Core`는 최대한 독립
- `Skills.Runtime`은 `Core`, `Character`, `Infrastructure`에 의존
- `Editor` assembly는 Runtime assembly를 참조하지만 Runtime은 Editor를 참조하지 않음
- Rendering/Optimization은 Skill에 직접 의존하지 않고 Demo Scene에서 조립

## 데이터 구조

### SkillDefinitionSO

- skillId
- displayName
- icon
- castType
- targetDefinition
- cooldownDefinition
- conditionDefinitions
- effectDefinitions
- animationTrigger
- vfxReference
- soundReference
- debugColor

### SkillInstance

- definition
- owner
- runtimeModules
- cooldownState
- executionState

### SkillContext

- owner
- casterTransform
- target
- targetPosition
- statProvider
- timeProvider
- randomProvider
- hitResults

### EffectDefinitionSO

- effectId
- effectType
- magnitude
- duration
- tickInterval
- stackingPolicy
- vfx
- sfx

### TargetingDefinitionSO

- targetType: Self, Single, Area, Cone, Projectile, Raycast
- layerMask
- range
- radius
- angle
- maxTargets
- sortingRule

### CooldownDefinitionSO

- cooldownTime
- chargeCount
- rechargeMode
- globalCooldownGroup

## Skill System 설계

### 핵심 인터페이스

```csharp
public interface ISkillModule
{
    void Initialize(SkillRuntimeContext context);
}

public interface ISkillCondition
{
    bool CanExecute(SkillContext context);
}

public interface ITargetResolver
{
    IReadOnlyList<SkillTarget> Resolve(SkillContext context);
}

public interface ISkillEffect
{
    void Apply(SkillContext context, SkillTarget target);
}

public interface ICooldownPolicy
{
    bool IsReady(SkillContext context);
    void Consume(SkillContext context);
}
```

### Runtime Skill Assembly

1. `SkillDefinitionSO` 선택
2. `SkillFactory`가 Definition의 하위 ScriptableObject들을 읽음
3. TargetResolver, Effects, Conditions, CooldownPolicy 생성
4. `SkillInstance` 생성
5. Character의 `SkillController`에 장착

### 실행 흐름

1. Input 또는 AI가 `TryExecute(skillId)` 호출
2. Condition 검사
3. Cooldown 검사
4. TargetResolver로 대상 계산
5. Animation/VFX windup 시작
6. Effect 적용
7. Cooldown 소비
8. Debug Timeline에 실행 로그 기록

## Skill Editor 설계

Unity Editor Window로 직접 제작한다.

기능:

- Skill 생성
- 기본 정보 편집
- Target 모듈 선택
- Effect 추가/삭제/정렬
- Condition 추가/삭제
- Cooldown 설정
- Preview 실행
- JSON 또는 ScriptableObject 저장/로드
- Validation: 누락된 Target, 잘못된 LayerMask, 음수 Cooldown, Effect 없는 Skill 경고
- Undo/Redo: Command Pattern 적용

Editor UI 구조:

- Left: Skill Asset List
- Center: Graph 또는 Module Stack
- Right: Inspector
- Bottom: Validation / Preview Log

## Animation Tool 설계

DX11 Animation Tool 경험을 Unity로 이식한다.

기능:

- Animation Preview
- Animation Blend
- Bone Viewer
- Keyframe Scrubber
- Event Editor
- Root Motion Toggle
- Upper/Lower Body Mask Preview
- Animation Export
- Skill Event 연동

구현 권장:

- `PlayableGraph` 기반 Preview
- SceneView Gizmo로 Bone 표시
- EditorWindow + Timeline 스타일 UI
- AnimationEventTrackSO로 이벤트 별도 저장

## Shader Showcase 설계

URP 기준으로 ShaderGraph와 HLSL Include를 병행한다.

효과:

- Rim Light
- Dissolve
- Fresnel
- Toon
- Outline
- Distortion
- Hologram
- Post Processing
- Glow/Bloom style effect

각 효과는 다음을 UI에 표시한다.

- 사용 입력: Normal, ViewDir, Noise, Depth 등
- 주요 파라미터
- Render Queue
- GPU 비용 추정
- 적용 전/후 비교

## Optimization Showcase 설계

기능:

- LOD
- Frustum Culling
- Occlusion Culling
- GPU Instancing
- SRP Batcher
- Object Pooling
- Addressables
- Async Loading

UI:

- 토글 패널
- 실시간 metric panel
- spawn count slider
- stress test button
- capture snapshot button

## Rendering Debug View 설계

RenderTexture 기반 멀티뷰를 구성한다.

View:

- Main View
- Wireframe View
- Normal View
- Overdraw View
- Shadow View
- Depth View

구현:

- 카메라 여러 개 사용
- URP RendererFeature로 Normal/Depth/Overdraw 텍스처 생성
- RenderTexture를 UI RawImage에 표시
- 선택한 오브젝트의 material/debug pass 전환

## UI 구조

- Top Toolbar: Mode 선택, Play/Pause, Reset
- Left Dock: 모듈 선택
- Center View: Demo Scene / Debug Views
- Right Inspector: 선택 대상 설정
- Bottom Timeline/Log: Skill 실행, Animation Event, Profiler Snapshot

## Demo Scene 구성

하나의 씬에서 모든 기능을 확인한다.

- Character
- Enemy Dummy
- Skill Tool Runtime Panel
- Skill Editor launcher
- Animation Tool launcher
- Shader Viewer area
- Optimization Viewer area
- Debug Camera Grid

## 추천 개발 원칙

- 처음부터 대형 RPG를 만들지 않는다.
- 기능 하나마다 `Runtime + Editor + Demo + Docs`를 닫고 다음 기능으로 간다.
- Unity 개념이 부족한 상태이므로 1단계는 Unity 기초와 작은 Vertical Slice에 집중한다.
- 과한 커스텀 렌더링보다 완성 가능한 URP RendererFeature 중심으로 간다.
- 면접용으로는 코드보다 실행 장면과 문서가 먼저 보인다. 단, 문서가 과장되면 역효과다.
