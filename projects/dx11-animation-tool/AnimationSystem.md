# Animation System Analysis

## 개요

Animation Tool과 Gunfire Reborn Clone은 Assimp 기반의 Skeletal Animation 구조를 사용한다. 핵심 클래스는 `CModel`, `CAnimation`, `CChannel`, `CBone`이다.

## 핵심 구조

### CModel

- Component로 동작한다.
- Mesh, Material, Bone, Animation을 소유한다.
- `PlayAnimation`, `SetupAnimation`, `SetCurrentAnimationIndex`, `SetInterpolationAnimationIndex` 등을 제공한다.
- Render 시 Mesh별 Bone Matrix를 Shader에 바인딩한다.

### CAnimation

- 하나의 Animation Clip 역할이다.
- 여러 `CChannel`을 가진다.
- Play Type: `ONCE`, `LOOP`, `REPLAY_WHEN_PLAY`, `REPLAY`
- 현재 Track Position, TickPerSecond, Duration을 관리한다.
- Alert Point / Alert Point Sound를 통해 애니메이션 이벤트를 처리한다.

### CChannel

- 특정 Bone에 대응되는 KeyFrame Track이다.
- KeyFrame 리스트를 보유한다.
- 현재 Track Position 기준으로 보간한 Local Transform을 Bone에 반영한다.

### CBone

- Bone 계층과 Combined Matrix를 관리한다.
- Skinning Matrix 계산에 사용된다.

## Animation Tool 기능 분석

Animation Tool은 `CLevel_AnimTool`, `CAT_Obj`, `CAT_PartAnimObj`, `CAnimTool_Camera` 중심으로 구성된다.

확인된 기능은 다음과 같다.

- Animation Preview
- Animation List 선택 및 재생
- Track Position 확인/제어
- Animation Blend / Interpolation
- Root Motion Bone XML 로드
- Blend Bone XML 로드
- Animation Event XML 로드/저장
- Bone Matrix 확인
- Bone Look/Right/Up/Position Debug
- 특정 Bone Animation 제외 및 수동 Matrix 제어
- Ray를 통한 Bone 방향 시각화
- ImGui 기반 툴 UI

## 데이터 파일

Animation Tool의 주요 데이터는 XML로 관리된다.

- `LinkAnimInterpolationData.xml`
- `LinkRootMotionBoneName.xml`
- `LinkBlendBones.xml`
- `LinkAnimationEvents.xml`
- `LinkBoneData.xml`

## 설계 패턴

- Component Pattern: Model이 GameObject의 Component로 동작
- Prototype Pattern: Model Component는 Prototype에서 Clone
- State Pattern: Animation PlayType, Player/Monster State에 따라 Animation 전환
- Observer/Callback 유사 구조: Animation Event와 callback 등록 구조
- Tool MVC 유사 구조: `Level_AnimTool`이 UI와 현재 선택 상태를 제어하고, `CAT_PartAnimObj`가 실제 모델 런타임을 담당

## Unity 포트폴리오 이식 방향

Unity에서는 Animator Controller만 보여주면 DX11 경험이 드러나지 않는다. 다음 수준까지 구현해야 차별화된다.

- `AnimationClip` Preview Window
- `PlayableGraph` 기반 Runtime Blend
- Bone Viewer Gizmo
- Keyframe/Event Timeline Editor
- Animation Event를 Skill Trigger와 연결
- Root Motion toggle 및 preview
- Upper/Lower body mask blend preview
- Export: `AnimationProfile` ScriptableObject 또는 JSON

## 권장 Unity 구조

- Runtime: `AnimationRuntime`, `AnimationGraphController`, `AnimationEventDispatcher`
- Editor: `AnimationPreviewWindow`, `BoneViewerOverlay`, `KeyframeTimeline`, `AnimationEventEditor`
- Data: `AnimationProfileSO`, `AnimationEventTrackSO`, `BoneMaskSO`, `BlendProfileSO`

## 포트폴리오에서 보여줄 장면

한 캐릭터를 중심으로 다음 패널을 제공한다.

- Clip 선택
- 재생/정지/프레임 이동
- Blend From/To 선택 및 blend time 조절
- Bone Hierarchy Tree
- Bone Gizmo on/off
- Event marker 추가/삭제
- Event 발생 시 Skill Effect 또는 Sound Trigger 확인
