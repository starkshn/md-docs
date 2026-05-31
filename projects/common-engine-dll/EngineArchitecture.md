# Engine Architecture Analysis

## 프로젝트 개요

### Gunfire Reborn Clone Project

- 위치: `C:\kny\Project\DirectX\GunFireReborn\DX11_FrameWork`
- 목적: Gunfire Reborn 스타일의 1인칭 액션/슈팅 전투, 몬스터, 보스, 투사체, 파티클, UI, NavMesh, Deferred Rendering을 자체 DX11 Framework 위에서 구현한 프로젝트
- 주요 프로젝트: `Client`, `Engine`, `Map_Tool`, `Class`
- 개발 기간 추정: 소스 및 산출물 타임스탬프 기준 2024년 하반기부터 2025년 2월 전후까지 집중 개발 흔적 확인

### DX11 Animation Tool

- 위치: `C:\kny\Project\DirectX\AnimTool`
- 목적: FBX/Skeletal Animation 확인, 애니메이션 재생/트랙 제어, 보간, 루트 모션, Bone Viewer, Bone 회전 제어, 이벤트 저장/로드를 지원하는 내부 툴
- 주요 프로젝트: `Client`, `Engine`, `EngineSDK`
- 개발 기간 추정: 이미지/노션 자료 기준 2024년 10월~2025년 1월 전후 집중 개발 흔적 확인

### 공통 Framework / Engine DLL

두 프로젝트 모두 `Engine.dll`, `Engine.lib`, `EngineSDK/Inc`, `EngineSDK/Lib` 형태로 엔진 기능을 클라이언트 프로젝트에 제공한다. Gunfire Reborn 쪽은 소스가 더 최신화되어 있고, AnimTool 쪽은 ImGui/ImSequencer/imnodes 등 툴링 의존성이 더 강하다.

## 기술 스택

- C++
- DirectX 11
- HLSL
- Win32 / MFC 스타일 엔트리 프로젝트
- Assimp 기반 FBX/Animation 로딩
- DirectXTK
- Effects11
- FMOD
- ImGui, imnodes, ImSequencer
- tinyxml2
- 자체 Engine DLL / EngineSDK 구조

## 전체 엔진 구조

엔진의 중심은 `CGameInstance`이다. `CGameInstance`는 Singleton이면서 Facade 역할을 수행하며, Client가 직접 여러 매니저를 만지지 않고 엔진 기능에 접근하게 한다.

핵심 흐름은 다음과 같다.

1. `CGameInstance::InitializeEngine`에서 Graphic, Input, Renderer, Prototype, Object, Level, Light, RenderTarget, Picking, Frustum, UI, Sound 등 매니저 생성
2. Loader가 레벨별 Prototype 등록
3. Client Level이 `AddGameObjectToLayer`로 GameObject 사본 생성 요청
4. `Prototype_Manager`가 Prototype을 Clone
5. `Object_Manager`가 Layer에 GameObject 보관
6. 매 프레임 `PriorityUpdate -> Update -> LateUpdate -> Renderer.DrawRenderObject`
7. GameObject는 필요한 RenderGroup에 자신을 등록하고 Renderer가 그룹별 렌더링 수행

## 모듈별 역할과 의존성

### Core

- 대표 클래스: `CBase`, `CGameInstance`, `CTimer_Manager`, `CTimer`, `CLevel`, `CLevel_Manager`
- 역할: 엔진 생명주기, 참조 카운트 기반 메모리 관리, 레벨 전환, 시간 관리
- 의존성: 대부분의 엔진 기능이 `CGameInstance`를 통해 접근된다.

### Renderer

- 대표 클래스: `CRenderer`, `CGraphic_Device`, `CRenderTargetManager`, `CRenderTarget`, `CShader`, `CLightManager`, `CShadow`
- 역할: 렌더 그룹 큐 관리, Deferred Rendering, MRT, Light Accumulation, Shadow, Glow, Blur, Outline, Distortion, UI 렌더링
- 의존성: `GameObject`가 렌더 그룹에 자신을 등록하고, Renderer는 RenderTargetManager와 Shader를 사용해 패스를 구성한다.

### Resource

- 대표 클래스: `CPrototype_Manager`, `CTexture`, `CModel`, `CMesh`, `CShader`, `CVIBuffer*`
- 역할: 리소스 원형 등록, Clone 기반 인스턴스 생성, 모델/텍스처/셰이더/버퍼 로딩
- 의존성: GameObject의 Component 추가는 Prototype_Manager의 Component Clone에 의존한다.

### Animation

- 대표 클래스: `CModel`, `CAnimation`, `CChannel`, `CBone`
- 역할: FBX/Dat/Anim 로딩, Bone 계층 관리, Channel별 KeyFrame 보간, Animation PlayType, Animation Blend, Animation Event
- 의존성: Model Component가 Mesh/Bone/Animation을 소유하고, 렌더링 시 Shader에 Bone Matrix를 바인딩한다.

### Object

- 대표 클래스: `CGameObject`, `CPartObject`, `CContainerObject`, `CAlphaObject`, `CLayer`, `CObject_Manager`
- 역할: Prototype Clone 객체 보관, Layer 단위 업데이트, PartObject 조립, Alpha sorting용 ViewZ 관리
- 의존성: Object_Manager는 Layer 배열을 레벨별로 관리하고, Layer는 GameObject list를 보관한다.

### Component

- 대표 클래스: `CComponent`, `CTransform`, `CModel`, `CShader`, `CTexture`, `CVIBuffer`, `CCollider`, `CNavigation`
- 역할: GameObject 기능 조립 단위. Unity의 Component와 유사한 구조이다.
- 의존성: GameObject가 `map<wstring, CComponent*>`로 Component를 소유한다.

### Scene

- 대표 클래스: `CLevel`, `CLevel_Logo`, `CLevel_Loading`, `CLevel_GamePlay`, `CLevelBoss`, `CLevel_AnimTool`
- 역할: 레벨별 Prototype 로딩, Object 배치, 전환, 씬별 Update/Render
- 의존성: Loader가 Prototype을 준비하고 Level이 Object_Manager를 통해 객체를 생성한다.

### Physics

- 대표 클래스: `CCollider`, `CBoundingAABB`, `CBoundingOBB`, `CBoundingSphere`, `CNavigation`, `CCell`, `CQuadTree`, `CPicking`
- 역할: 충돌, Picking, NavMesh, Frustum/공간 판정
- 의존성: Layer가 Collider를 가진 GameObject를 순회하면서 충돌 검사한다.

### UI

- 대표 클래스: `CUIObject`, `CUIParent`, `CUIPanel`, `CUIElement`, `CUIManager`, Client의 `UIHPBar`, `UIDamageFont`, `UICrossHair` 등
- 역할: 패널/엘리먼트 계층, 2D/원근 UI, Damage Font, HP Bar, Crosshair, Minimap
- 의존성: UIManager가 Panel/Element를 이름 기반으로 관리하고 Renderer의 `RG_UI`에서 depth sorting 후 렌더링한다.

## 구조적 장점

- 엔진과 게임 코드가 DLL/Client로 분리되어 재사용 구조를 가진다.
- Prototype + Component + Layer 구조가 Unity식 사고와 연결된다.
- Rendering, Animation, Resource, Scene, Object 수명 주기를 직접 제어한 경험이 명확하다.
- Unity 포트폴리오에서 단순 사용자가 아니라 엔진 내부 구조를 이해한 클라이언트 개발자라는 증거가 된다.

## 구조적 약점 및 개선 포인트

- `CGameInstance`가 너무 많은 기능을 직접 노출해 God Object가 되기 쉽다.
- 문자열 기반 Prototype/Component Tag는 오타와 런타임 오류에 취약하다.
- Manager Singleton 의존이 강해 테스트와 병렬 개발이 어렵다.
- Object Pooling이 전역 구조로 체계화되어 있지 않아 투사체/파티클에서 성능 압박 가능성이 있다.
- Layer 충돌 검사 구조는 규모가 커지면 Broad Phase 최적화가 필요하다.

Unity 포트폴리오에서는 위 약점을 개선하는 방향으로 설계하면 좋다. 예를 들어 `Addressables + ScriptableObject ID + Service Locator 최소화 + DI 가능한 Runtime Context + Pooling 표준화`를 보여주면 DX11 경험을 현대 Unity 구조로 번역했다는 인상을 줄 수 있다.
