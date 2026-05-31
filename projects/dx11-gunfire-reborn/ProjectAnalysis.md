# Gunfire Reborn Clone Project Analysis

## 프로젝트 개요

Gunfire Reborn Clone은 DirectX 11 기반 자체 Framework/Engine DLL 위에서 제작한 1인칭 액션 슈팅 클론 프로젝트이다. 렌더링, 애니메이션, 오브젝트 생성, UI, 파티클, 충돌, 보스 패턴, NavMesh, 후처리 효과를 직접 구현한 기술 중심 프로젝트다.

## 프로젝트 목적

- 상용 엔진 없이 DirectX 11 기반 게임 클라이언트 구조를 직접 설계한다.
- Component / Prototype / Manager 기반 엔진 구조를 학습하고 재사용 가능한 Framework로 만든다.
- FPS 전투, 투사체, 몬스터 AI, 보스 패턴, 파티클, UI, 렌더링 후처리까지 하나의 런타임에서 통합한다.
- 이후 Unity 포트폴리오에서 시스템 설계와 렌더링 이해도를 증명할 기반 경험으로 사용한다.

## 개발 기간

로컬 파일과 산출물 기준으로 2024년 하반기부터 2025년 2월 전후까지 집중 개발한 흔적이 확인된다.

## 주요 기능

- FPS Player / Weapon / Projectile 구조
- Monster 01~06 및 Boss 구조
- Boss smash, meteor, rock, spawn pattern
- Projectile collision, wall hit, monster hit
- Particle manager 및 개별 particle effect
- Trail buffer 기반 sword/projectile trail
- Torch billboard / glow effect
- HP bar, crosshair, minimap, damage font, perspective UI
- NavMesh 기반 이동 및 sliding vector 테스트
- Dissolve, Glow, Distortion, Outline, Shadow, Deferred Lighting
- Map Tool / Class Tool 계층

## 기술 스택

- C++
- DirectX 11
- HLSL
- Assimp
- DirectXTK
- Effects11
- FMOD
- tinyxml2
- ImGui
- 자체 Engine DLL / EngineSDK

## 엔진 구조 연결

Gunfire 프로젝트는 `Engine` DLL을 중심으로 동작한다.

- `Client`: 실제 게임 런타임. Player, Monster, Boss, UI, Projectile, Particle 구현
- `Engine`: Core, Renderer, Resource, Animation, Object, Component, Scene, Physics, UI 제공
- `EngineSDK`: Client가 참조하는 Include/Lib/DLL 배포 계층
- `Map_Tool`: 맵/배치/툴 기능
- `Class`: 실험/툴/맵 관련 프로젝트 흔적

## 주요 클래스 그룹

### Player

- `CPlayer`
- `CPlayerBody`
- `CPlayerWeapon`
- `CPlayerBullet`

Player는 `CStateObjectContainer` 기반으로 Body/Weapon PartObject를 조립한다. Unity 포트폴리오에서는 `CharacterController + SkillController + EquipmentController` 구조로 이식하기 좋다.

### Monster / Boss

- `CMonsterBase`
- `CMonster01` ~ `CMonster06`
- `CMonsterBodyBase`
- `CMonsterWeaponBase`
- `CBoss`, `CBossBody`, `CBossWeapon`, `CBossRock`

상속 기반으로 몬스터 종류를 확장한다. Unity에서는 상속보다 `AIController + Behavior + SkillDefinition` 조합으로 개선하는 것이 좋다.

### Projectile / Effect / Particle

- `CProjectile`
- `CBullet`, `CPlayerBullet`, `CMonsterBullet`, `CBossRock`
- `CEffect`, `CEffectTrail`, `CEffectManager`
- `CParticle`, `CParticleManager`

반복 생성이 많은 계층이므로 Unity 포트폴리오에서는 Object Pooling과 Addressables 비동기 로딩을 붙여 성능 개선 사례로 만들기 좋다.

### UI

- `CUIBG`
- `CUICrossHair`
- `CUIDamageFont`
- `CUIHPBar`
- `CUITexPerspective`

2D UI와 원근 투영 UI가 섞여 있다. Unity에서는 World Space UI, Screen Space UI, RenderTexture Debug UI로 재구성할 수 있다.

## 포트폴리오 전환 포인트

이 프로젝트에서 가장 강하게 가져갈 수 있는 요소는 다음이다.

- Deferred Rendering과 RenderTarget Debug View 경험
- Prototype 기반 런타임 객체 생성 구조
- Component 기반 GameObject 구조
- Boss/Projectile/Effect/Particle Runtime 구조
- UI와 게임 월드 좌표 연동
- NavMesh/Picking/Collider 구조 이해

단순 클론이라는 이름보다 `DX11 Technical Game Framework Demo`로 포장하는 것이 더 적절하다.
