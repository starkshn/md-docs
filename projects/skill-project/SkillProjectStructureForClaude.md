# SkillProject Structure Analysis For Claude

이 문서는 `C:\kny\Project\Unity\SkillProject`를 회사 컴퓨터의 Claude에게 분석시키기 위한 전달 문서다.

목적은 기존 SkillProject의 구조를 파악하고, 현재 UnityTechnicalShowcase 포트폴리오에 어떤 개념을 가져갈 수 있는지 판단하는 것이다.

## Local Project Path

```text
C:\kny\Project\Unity\SkillProject
```

현재 이 프로젝트는 별도 Git 저장소가 아니다.

```text
.git 없음
```

따라서 회사 PC에서 분석하려면 프로젝트 폴더 자체를 복사하거나, 별도 임시 레포로 올리는 방식이 필요하다.

## Project Type

Unity 기반 스킬 시스템 실험 프로젝트로 보인다.

핵심 성격:

- ScriptableObject 기반 데이터 관리 실험
- EditorWindow 기반 Skill System 관리 툴 실험
- Effect / TargetSearcher / Stat / Category 데이터 구조 실험
- Entity StateMachine / Skill StateMachine 실험
- Skill UI Prefab과 테스트 씬 포함
- MackySoft SerializeReferenceExtensions 사용
- xNode 플러그인 포함

단, 일부 클래스는 이름만 있고 아직 빈 MonoBehaviour 상태다. Claude는 이 프로젝트를 완성된 스킬 시스템으로 보지 말고, 강의/실험 기반의 구조 후보로 분석해야 한다.

## Top-Level Folder Structure

```text
SkillProject/
├─ Assets/
├─ Packages/
├─ ProjectSettings/
├─ Library/          # Git 제외 대상
├─ Logs/             # Git 제외 대상
├─ obj/              # Git 제외 대상
├─ UserSettings/     # Git 제외 대상
└─ .vs/              # Git 제외 대상
```

## Assets Structure

```text
Assets/
├─ Animations/
├─ Effects/
├─ Fonts/
├─ Materials/
├─ Models/
├─ Plugins/
├─ Prefabs/
├─ Resources/
├─ Scenes/
├─ Scripts/
├─ Settings/
├─ Sprites/
├─ Test/
├─ TextMesh Pro/
└─ _Recovery/
```

## Package Dependencies

`Packages/manifest.json` 기준 주요 패키지:

```text
com.unity.cinemachine
com.unity.inputsystem
com.unity.timeline
com.unity.ugui
com.unity.visualscripting
com.unity.collab-proxy
com.unity.multiplayer.center
```

포트폴리오 재사용 관점:

- `ugui`: Skill UI 분석에 유효
- `inputsystem`: 현재 UnityTechnicalShowcase와 연결 가능
- `timeline`: Animation Tool 연구 후보
- `visualscripting`, `multiplayer.center`, `collab-proxy`: 포트폴리오 핵심에는 불필요할 가능성 있음

## External Plugins

```text
Assets/Plugins/MackySoft/MackySoft.SerializeReferenceExtensions
Assets/Plugins/xNode
```

### MackySoft SerializeReferenceExtensions

사용 위치:

```text
EffectData.cs
EffectStackAction.cs
TargetSearcher.cs
TargetSearchAction.cs
TargetSelectionAction.cs
```

의미:

- `[SerializeReference]` 기반 다형성 직렬화
- `SubclassSelector`로 EffectAction, TargetSearchAction 등을 인스펙터에서 선택 가능하게 만드는 구조
- Unity 포트폴리오의 모듈형 Skill Effect / Condition / Target 설계에 참고 가치가 높음

### xNode

프로젝트에 포함되어 있지만 현재 Skill 코드와 직접 연결된 흔적은 명확하지 않다.

Claude 분석 요청:

- xNode가 실제 Skill Tool에 사용되고 있는지 확인
- 사용되지 않았다면 제거 후보인지 판단
- 향후 Node 기반 Skill Editor로 확장할 가치가 있는지 평가

## Scripts Structure

```text
Assets/Scripts/
├─ Core/
├─ Editor/
└─ Test/
```

### Core

핵심 런타임/데이터 코드가 모여 있다.

```text
Core/
├─ Animation/
├─ Attribute/
├─ CustomAction/
├─ Effect/
├─ Entity/
├─ Skill/
├─ StateMachine/
├─ Stats/
├─ TargetSearcher/
└─ Utility/
```

### Editor

Unity Editor 확장 코드가 모여 있다.

```text
Editor/
├─ SkillSystemWindow.cs
├─ IdentifiedObjectEditor.cs
├─ EffectEditor.cs
├─ StatEditor.cs
├─ CustomEditorUtility.cs
├─ PropertyDrawer 계열
└─ 일부 빈/미완성 MonoBehaviour 파일
```

### Test

테스트/실험 코드가 있다.

```text
Test/
├─ Effect/
├─ Skill/
├─ EntityMovementTest.cs
├─ IndicatorTest.cs
├─ StatTest.cs
└─ TargetSearcherTest*.cs
```

## Data Asset Structure

`Assets/Resources`에 ScriptableObject 데이터가 저장되어 있다.

```text
Assets/Resources/
├─ Category/
├─ Database/
├─ Effect/
└─ Stat/
```

주요 데이터:

```text
Database/CategoryDatabase.asset
Database/EffectDatabase.asset
Database/StatDatabase.asset

Category/CATEGORY_RELATION_FRIEND.asset
Category/CATEGORY_RELATION_HOSPITAL.asset

Effect/EFFECT_Test.asset
Effect/EFFECT_Test2.asset

Stat/STAT_DAMAGE.asset
Stat/STAT_HP.asset
Stat/STAT_MP.asset
Stat/STAT_MOVE_SPEED.asset
Stat/STAT_SKILL_POINT.asset
...
```

## Key Runtime Data Architecture

### IdentifiedObject

파일:

```text
Assets/Scripts/Core/IdentifiedObject.cs
```

역할:

- ScriptableObject 기반 공통 데이터 베이스 클래스
- `id`, `codeName`, `displayName`, `description`, `icon`, `categories` 보유
- `ICloneable` 구현
- Category 포함 여부 확인 기능 제공

의미:

UnityTechnicalShowcase의 `SkillDefinitionSO`, `EffectDefinitionSO`, `StatDefinitionSO` 설계에 참고 가능하다.

### IODatabase

파일:

```text
Assets/Scripts/Core/IODatabase.cs
```

역할:

- `IdentifiedObject` 리스트를 관리하는 ScriptableObject Database
- Add / Remove / Sort / ID 재정렬
- `GetDataByID`, `GetDataCodeName` 제공
- Editor에서 AssetDatabase와 함께 사용됨

주의점:

- 이름이 `IODatabase`지만 실제로는 입출력 DB라기보다 `IdentifiedObjectDatabase`에 가깝다.
- Reflection으로 private field `id`를 수정한다.
- EditorUtility.SetDirty가 포함되어 Runtime / Editor 관심사가 약간 섞여 있다.

포트폴리오 반영 시 개선 후보:

- Runtime DB와 Editor DB 조작 로직 분리
- Reflection 사용 최소화
- ID 재정렬 정책 명확화
- Addressables 또는 GUID 기반 참조 검토

## Key Skill / Effect Concepts

### Effect

파일:

```text
Assets/Scripts/Core/Effect/Effect.cs
Assets/Scripts/Core/Effect/EffectData.cs
Assets/Scripts/Core/Effect/EffectStackAction.cs
Assets/Scripts/Core/Effect/EffectAction/*.cs
```

핵심 개념:

- Effect는 `IdentifiedObject` 기반 데이터로 보인다.
- EffectAction은 추상 클래스 기반 다형성 구조다.
- `DealDamageAction`, `IncreaseStatAction` 등 구체 액션이 존재한다.
- `[SerializeReference, SubclassSelector]`를 통해 액션 조합형 설계를 시도했다.

포트폴리오 가치:

- 모듈형 Skill Effect 설계의 좋은 참고 자료
- ScriptableObject + SerializeReference 조합의 장단점 분석 가능
- Skill Effect Pipeline 설계 근거로 사용 가능

### TargetSearcher

파일:

```text
Assets/Scripts/Core/TargetSearcher/TargetSearcher.cs
Assets/Scripts/Core/TargetSearcher/TargetSearchAction/*.cs
Assets/Scripts/Core/TargetSearcher/TargetSelectionAction/*.cs
Assets/Scripts/Core/TargetSearcher/IndicatorViewAction/*.cs
```

핵심 개념:

- Target Search와 Target Selection을 분리하려는 구조
- SearchArea / SelectedTarget
- SelectEntity / SelectPosition / SelectSelf / SelectSelfByOneClick
- IndicatorViewAction으로 범위 표시와 선택 UI를 분리하려는 흔적

포트폴리오 가치:

- Skill Targeting System 설계에 직접 참고 가능
- Target / Indicator / Selection을 분리한 구조는 기술 포폴 설명 포인트가 될 수 있음

### Stats

파일:

```text
Assets/Scripts/Core/Stats/Stat.cs
Assets/Scripts/Core/Stats/Stats.cs
Assets/Scripts/Core/Stats/StatOverride.cs
Assets/Scripts/Core/Stats/StatScaleFloat.cs
```

핵심 개념:

- Stat은 `IdentifiedObject` 기반 데이터
- `STAT_DAMAGE`, `STAT_HP`, `STAT_MP` 등의 데이터가 Resources에 존재
- Effect와 Cost 계산에 사용될 가능성이 큼

포트폴리오 가치:

- Skill Cost / Damage Formula / Buff 시스템 설계 기반으로 참고 가능

## Skill StateMachine / Entity StateMachine

폴더:

```text
Assets/Scripts/Core/Entity/StateMachine
Assets/Scripts/Core/Skill/StateMachine
```

존재하는 상태 이름:

```text
EntityDefaultState
RollingState
DeadState
EntitySkillState
CastingSkillState
ChargingSkillState
InSkillPrecedingActionState
InSkillActionState

ReadyState
SearchingTargetState
CastingState
ChargingState
InPrecedingActionState
InActionState
CooldownState
```

주의점:

- 일부 Skill StateMachine 파일은 빈 MonoBehaviour 상태다.
- Entity 쪽 StateMachine은 상대적으로 구조가 더 잡혀 있을 가능성이 있다.

Claude 분석 요청:

- 실제로 동작하는 StateMachine이 어느 쪽인지 확인
- SkillStateMachine 폴더가 설계만 있고 미구현인지 확인
- EntityStateMachine과 SkillStateMachine을 UnityTechnicalShowcase에서 어떻게 재설계할지 제안

## Skill Editor Tool

핵심 파일:

```text
Assets/Scripts/Editor/SkillSystemWindow.cs
```

역할:

- `Tools/Skill System` 메뉴로 EditorWindow 열기
- Category / Stat / Effect Database를 탭으로 관리
- Database 없으면 `Assets/Resources/Database`와 데이터 폴더 자동 생성
- New / Remove Last / Sort By Name 제공
- 선택된 `IdentifiedObject`를 CustomEditor로 표시

현재 지원 타입:

```csharp
SetupDatabases(new[] { typeof(Category), typeof(Stat), typeof(Effect) });
```

즉, 현재 창은 이름은 Skill System이지만 실제로는 Category / Stat / Effect 데이터 관리 툴에 가깝다.

포트폴리오 반영 시 개선 방향:

- SkillDefinitionSO까지 관리 대상 확장
- Effect / Target / Condition / Cost / Cooldown을 별도 탭으로 분리
- Validation System 추가
- Runtime Skill Assembly Preview 추가
- 데이터 생성 위치와 네이밍 규칙 정리
- Editor 전용 asmdef로 분리

## Prefab / UI Assets

주요 Prefab:

```text
Indicator.prefab
Kachujin G Rosales.prefab
xbot - Enemy.prefab
xbot - Friend.prefab

UI/Entity HUD.prefab
UI/Skill Progress Bar.prefab
UI/Skill Tooltip.prefab
UI/SkillBar/Skill Bar.prefab
UI/SkillBar/Skill Slot.prefab
UI/SkillEffectView/Skill Effect View.prefab
UI/SkillTree/Skill Tree View.prefab
```

포트폴리오 가치:

- Skill runtime 시연 UI 참고
- Skill Bar / Tooltip / Skill Tree UI를 Showcase Scene의 우측 Inspector나 Skill Demo Panel로 재해석 가능

## Scenes

```text
Assets/Scenes/SampleScene.unity
Assets/Scenes/Test Scene.unity
Assets/Scenes/Test Scene/NavMesh.asset
```

분석 요청:

- `Test Scene`에서 어떤 테스트가 연결되어 있는지 확인
- Prefab / Test Script / Resources 데이터가 실제로 연결되어 동작하는지 확인
- UnityTechnicalShowcase로 옮길 만한 샘플 흐름이 있는지 확인

## Current Strengths

이 프로젝트에서 가져갈 만한 강점:

1. ScriptableObject 기반 데이터 관리 구조
2. Database asset 자동 생성 EditorWindow
3. IdentifiedObject 기반 공통 데이터 모델
4. EffectAction 다형성 구조
5. SerializeReference + SubclassSelector 활용
6. Target Search / Selection / Indicator 분리 아이디어
7. Stat / Effect / Category 데이터 분리
8. Skill UI Prefab 구성 아이디어
9. StateMachine 기반 스킬 흐름 설계 시도

## Current Weaknesses / Risks

주의할 점:

1. 일부 핵심 이름의 클래스가 빈 MonoBehaviour다.
   - `Skill.cs`
   - `SkillData.cs`
   - `SkillSystem.cs`
   - 일부 SkillStateMachine 계열
2. Runtime 코드와 Editor 코드 관심사가 일부 섞여 있다.
3. Resources 기반 데이터 로딩은 규모가 커지면 관리 한계가 있다.
4. Reflection으로 private id를 수정한다.
5. xNode가 실제 Skill Tool에 사용되는지 불명확하다.
6. asmdef 분리가 없다.
7. 네임스페이스가 없다.
8. Test 코드와 Runtime 코드 경계가 약하다.
9. 현재 UnityTechnicalShowcase의 모듈형 구조에는 그대로 이식하면 안 된다.

## Claude Analysis Request

Claude에게 아래 관점으로 분석을 요청하면 좋다.

```text
이 Unity SkillProject를 분석해줘.

목표는 이 프로젝트를 그대로 이식하는 것이 아니라,
UnityTechnicalShowcase 포트폴리오에서 재사용할 수 있는 설계 아이디어와 버려야 할 구조를 구분하는 것이다.

분석 기준:

1. 전체 폴더 구조
2. ScriptableObject 데이터 구조
3. IODatabase / IdentifiedObject 설계 장단점
4. SkillSystemWindow EditorWindow 구조
5. Effect / EffectAction / SerializeReference 구조
6. TargetSearcher 구조
7. Stat / Category 구조
8. Entity StateMachine과 Skill StateMachine 구조
9. 실제 구현된 부분과 빈 껍데기인 부분 구분
10. UnityTechnicalShowcase에 가져갈 수 있는 구조
11. 가져가면 안 되는 구조
12. asmdef / namespace / module 구조로 재설계하는 방법
13. 포트폴리오에서 면접 설명 포인트로 쓸 수 있는 내용

최종 산출물:

- 구조 요약
- 장점
- 문제점
- 재설계 제안
- UnityTechnicalShowcase 적용 우선순위
- 면접 설명 포인트
```

## Recommended Reuse Plan

UnityTechnicalShowcase에 바로 복사하지 말고 아래 순서로 재해석한다.

### Phase 1: Concept Extraction

가져올 개념:

- IdentifiedObject 스타일의 공통 데이터 모델
- ScriptableObject Database 관리 방식
- EffectAction 다형성 구조
- TargetSearcher 분리 구조
- EditorWindow 기반 데이터 관리 툴

### Phase 2: Redesign

UnityTechnicalShowcase 기준으로 변경:

```text
IdentifiedObject
→ NY_Data_DefinitionBase

IODatabase
→ NY_Data_Database<T>

SkillSystemWindow
→ NY_SkillEditor_Window

EffectAction
→ NY_Skill_EffectAction

TargetSearcher
→ NY_Skill_TargetingModule
```

### Phase 3: Integration

현재 포트폴리오 구조에 맞춰 적용:

```text
00_Core
01_Runtime
02_Modules
03_Tools
04_Showcase
07_Data
```

asmdef 기준:

```text
NY.Core
NY.Runtime
NY.Modules
NY.Editor
NY.Showcase
```

### Phase 4: Documentation

기술 블로그 / 면접용으로 정리할 주제:

- ScriptableObject 기반 스킬 데이터 관리
- SerializeReference로 EffectAction 다형성 구현하기
- EditorWindow로 Skill Database Tool 만들기
- Target Search와 Target Selection을 분리한 이유
- 기존 실험 프로젝트를 포트폴리오 구조로 재설계한 과정

## Conclusion

SkillProject는 완성된 스킬 시스템이라기보다, UnityTechnicalShowcase의 Skill System / Skill Tool 설계에 참고할 수 있는 실험 자료다.

가장 가치 있는 부분은 다음이다.

```text
ScriptableObject Database
EditorWindow Database Tool
SerializeReference EffectAction
TargetSearcher 분리 구조
Stat / Category / Effect 데이터 분리
```

가장 조심해야 할 부분은 다음이다.

```text
빈 MonoBehaviour 클래스
Runtime / Editor 관심사 혼합
Resources 의존
asmdef / namespace 부재
xNode 사용 여부 불명확
```

따라서 Claude 분석의 목적은 이 프로젝트를 그대로 평가하는 것이 아니라, 현재 포트폴리오에 맞게 재설계할 수 있는 핵심 개념을 뽑아내는 것이다.
