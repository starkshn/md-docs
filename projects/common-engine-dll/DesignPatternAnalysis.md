@'
# Design Pattern Analysis

## Singleton

대표 클래스:

- `CGameInstance`
- Client의 `CEffectManager`
- Client의 `CParticleManager`

목적:

- 엔진 전역 기능 접근
- Manager 생명주기 단순화
- 게임 코드에서 빠른 접근 제공

장점:

- 학습/개인 프로젝트에서는 구현과 사용이 쉽다.
- DirectX 엔진 초기화 흐름을 한 곳에서 통제하기 쉽다.

단점:

- 의존성이 숨겨진다.
- 테스트가 어렵다.
- Manager 간 결합도가 높아진다.

Unity 포트폴리오 개선 방향:

- 전역 Singleton 남발 대신 `RuntimeContext`, Scene-level Service, ScriptableObject Event Channel을 사용
- 반드시 전역이어야 하는 것만 Singleton 또는 Bootstrapper로 제한

## Facade

대표 클래스:

- `CGameInstance`

설명:

`CGameInstance`는 Graphic, Input, Timer, Level, Prototype, Object, Renderer, Pipeline, Light, RenderTarget, Picking, UI, Sound 기능을 단일 API로 노출한다. Client는 각 Manager를 직접 알지 않아도 엔진 기능을 호출할 수 있다.

## Factory

대표 함수:

- `Create(...)`
- `Clone(...)`

대부분의 엔진 클래스가 static `Create`와 virtual `Clone`을 제공한다. 생성 실패 시 `SafeRelease`하는 패턴도 일관된다.

## Prototype

대표 클래스:

- `CPrototype_Manager`
- `CGameObject::Clone`
- `CComponent::Clone`

설명:

원형 객체를 등록한 뒤, 런타임에서 복제해 사용하는 구조이다. Unity의 Prefab/ScriptableObject와 연결되는 중요한 경험이다.

## Component Pattern

대표 클래스:

- `CGameObject`
- `CComponent`
- `CTransform`, `CModel`, `CShader`, `CTexture`, `CCollider`, `CNavigation`

설명:

GameObject는 기능을 직접 다 가지지 않고 Component map을 통해 기능을 조립한다. Unity의 핵심 구조와 거의 같은 사고방식이다.

## State Pattern

대표 사례:

- Player state enum
- Monster/Boss attack index
- Animation play type
- Camera effect state
- Trigger/interact type

설명:

명시적인 State 객체 계층보다는 enum과 조건문 기반 상태 전환이 많다. 포트폴리오에서는 이 부분을 `IState`, `StateMachine<T>` 또는 Unity Animator/Playable 연계로 개선할 수 있다.

## Observer / Event

대표 사례:

- Animation Alert Point / Sound Event
- UI Manager 등록 및 조회
- Animation Tool callback

설명:

완전한 Observer 인프라보다는 이벤트 포인트와 callback이 부분적으로 사용된다. Unity에서는 `C# event`, `UnityEvent`, `ScriptableObject Event Channel` 중 목적에 맞게 분리하는 것이 좋다.

## Command

DX11 프로젝트에서는 명확한 Command 객체 패턴은 강하게 드러나지 않는다. 하지만 Animation Tool의 UI 조작, Skill Editor의 저장/로드/Undo/Redo에는 Command Pattern을 적용할 가치가 크다.

Unity 포트폴리오 적용:

- `IEditorCommand`
- `AddEffectCommand`
- `RemoveEffectCommand`
- `ChangeSkillPropertyCommand`
- Undo/Redo stack

## Template Method

대표 사례:

- `CGameObject`의 `InitializePrototype`, `Initialize`, `PriorityUpdate`, `Update`, `LateUpdate`, `Render`
- `CLevel` 파생 클래스의 Ready/Update/Render

설명:

기본 생명주기를 base class가 정의하고, 파생 객체가 필요한 단계만 override한다.

## Composite

대표 사례:

- `CContainerObject` / `CPartObject`
- UI Panel / UI Element 계층

설명:

Player, Monster, Weapon, Body 등 PartObject를 조립하는 구조와 UI parent-child 구조가 Composite에 가깝다.
