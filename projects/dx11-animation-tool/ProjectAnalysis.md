# DX11 Animation Tool Project Analysis

## 프로젝트 개요

DX11 Animation Tool은 DirectX 11 기반 자체 Engine DLL 위에서 제작한 애니메이션 검증/편집용 내부 툴이다. FBX 모델의 Skeleton, Animation Clip, Bone Transform, Animation Event, Blend, Root Motion을 확인하고 XML 데이터로 저장/로드하는 구조를 가진다.

## 프로젝트 목적

- Assimp 기반 Skeletal Animation 구조를 직접 이해하고 검증한다.
- 애니메이션 재생, 트랙 이동, 보간, 루트 모션, Bone 제어를 툴에서 시각화한다.
- 게임 런타임에서 사용할 Animation Event와 Blend 데이터를 외부 XML로 관리한다.
- ImGui 기반 Editor Tool 제작 경험을 확보한다.

## 개발 기간

로컬 이미지/노션 자료와 파일 타임스탬프 기준 2024년 10월부터 2025년 1월 전후까지 집중 개발 흔적이 확인된다.

## 주요 기능

- Animation Preview
- Animation List 선택 및 재생
- Track Position 제어
- Animation Blend / Interpolation
- Root Motion Bone 설정
- Upper/Lower Body 또는 Blend Bone 설정
- Bone Viewer
- Bone Look/Right/Up/Position 확인
- Bone 회전/제외 제어
- Ray 기반 Bone 방향 시각화
- Animation Event 추가/삭제/로드
- XML 기반 Animation Data 저장/로드

## 기술 스택

- C++
- DirectX 11
- HLSL
- Assimp
- ImGui
- imnodes
- ImSequencer
- tinyxml2
- 자체 Engine DLL / EngineSDK

## 핵심 구조

### CLevel_AnimTool

툴의 중심 레벨이다. ImGui UI를 그리고, 현재 선택한 Animation/Object/Bone/Event 상태를 제어한다.

담당 기능:

- Animation List 표시
- Play/Stop/Next/Prev 조작
- Bone 정보 표시
- Bone control UI
- Event 편집 UI
- 현재 Tool object 참조 관리

### CAT_Obj

툴에서 다루는 상위 오브젝트이다. `CAT_PartAnimObj`를 자식으로 보유하고, 모델 파트를 조립한다.

### CAT_PartAnimObj

실제 Animation Model을 보유하고 재생하는 핵심 GameObject이다.

담당 기능:

- 현재 Animation Index 관리
- Animation Play List 관리
- Loop / Multi Default / Multi Interpolation 재생
- Model Component 접근
- Animation 종료 로그
- Bone Matrix 조회
- Shader Resource 바인딩

### CModel / CAnimation / CChannel / CBone

Engine 계층의 Skeletal Animation 핵심 구조이다.

- `CModel`: Mesh, Material, Bone, Animation Clip 관리
- `CAnimation`: Clip 단위 Track, PlayType, Event 관리
- `CChannel`: Bone별 KeyFrame Track
- `CBone`: Skeleton node와 Combined Matrix 관리

## 데이터 구조

주요 XML:

- `LinkAnimInterpolationData.xml`
- `LinkRootMotionBoneName.xml`
- `LinkBlendBones.xml`
- `LinkAnimationEvents.xml`
- `LinkBoneData.xml`

## Unity 포트폴리오 전환 포인트

Animation Tool은 Unity 포트폴리오에서 가장 강하게 차별화할 수 있는 영역이다. 단순히 Animator Controller를 사용하는 것이 아니라, 다음을 직접 만들면 DX11 경험이 살아난다.

- PlayableGraph 기반 Animation Preview
- Bone Viewer Gizmo
- Animation Event Timeline Editor
- Runtime Skill Event 연동
- Upper/Lower body mask blend preview
- Root Motion toggle
- AnimationProfile ScriptableObject export

## 면접에서 강조할 포인트

- FBX Animation이 Clip/Bone/Channel/KeyFrame으로 어떻게 분해되는지 설명 가능하다.
- 단순 재생이 아니라 보간, 이벤트, 루트 모션, Bone별 디버깅을 툴로 만들었다.
- 이 경험을 Unity Editor Tool과 Skill/Animation 연동 구조로 재구성할 수 있다.
