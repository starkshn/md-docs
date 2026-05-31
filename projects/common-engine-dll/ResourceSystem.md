@'
# Resource System Analysis

## 개요

리소스 시스템은 Prototype 기반이다. 원형 객체와 원형 Component를 레벨별로 등록하고, 런타임에서는 Clone을 통해 실제 인스턴스를 생성한다.

## 핵심 클래스

- `CPrototype_Manager`: Prototype 등록/검색/Clone
- `CObject_Manager`: Clone된 GameObject를 Layer에 보관
- `CLayer`: 실제 GameObject list 보관 및 업데이트/충돌 순회
- `CGameObject`: Component map 보유
- `CComponent`: Clone 가능한 기능 단위
- `CModel`, `CTexture`, `CShader`, `CVIBuffer*`: 대표 리소스 Component

## 객체 생성 흐름

1. Loader가 `AddPrototype`으로 GameObject/Component 원형 등록
2. Level 또는 Client 코드가 `AddGameObjectToLayer` 호출
3. ObjectManager가 GameInstance를 통해 PrototypeManager에 Clone 요청
4. PrototypeManager가 `CGameObject::Clone` 또는 `CComponent::Clone` 호출
5. Clone된 GameObject가 Layer에 추가
6. GameObject 초기화 중 필요한 Component를 `AddComponent`로 추가
7. Component도 PrototypeManager에서 Clone되어 GameObject의 `m_Components`에 저장

## 장점

- Prototype과 Runtime instance를 명확히 구분한다.
- Component 재사용성이 높다.
- 레벨별 Prototype clear 구조가 존재한다.
- Unity의 Prefab/ScriptableObject 사고와 연결하기 쉽다.

## 약점

- 문자열 기반 tag가 많아 오타가 런타임 오류로 이어진다.
- Clone 실패 원인 추적이 어렵다.
- 리소스 로딩과 게임 오브젝트 생성을 동기적으로 처리하는 구조가 강하다.
- Addressables 같은 비동기 로딩/참조 추적 구조는 없다.

## Unity 이식 방향

- Prototype Tag는 `AssetReference`, `GUID`, `enum`, `Addressable key`로 대체
- Component Clone은 Prefab instantiate / Pool spawn / ScriptableObject config로 분리
- 리소스 수명은 Addressables label과 Scene lifetime으로 관리
- Runtime 생성은 `Factory + Pool + RuntimeContext`로 통합

## 포트폴리오 적용 예시

Skill System에서 다음 구조로 재해석한다.

- `SkillDefinitionSO`: Prototype 역할
- `EffectDefinitionSO`, `TargetingDefinitionSO`, `CooldownDefinitionSO`: Component Prototype 역할
- `SkillFactory`: Runtime Skill Assembly
- `SkillInstance`: Clone된 런타임 객체
- `SkillContext`: 실행 시 Owner, Target, Position, Stat, Time, Random 제공
- `EffectPool`, `ProjectilePool`: 반복 생성 최적화
