# Skill Course Learning Workflow

이 문서는 인프런 모듈식 스킬 시스템 강의를 학습하면서 `SkillProject`와 `UnityTechnicalShowcase`를 어떻게 분리해서 운영할지 정리한다.

## Course

인프런 강의:

```text
유니티 모듈식 스킬 시스템
```

현재 학습 프로젝트:

```text
C:\kny\Project\Unity\SkillProject
```

최종 포트폴리오 프로젝트:

```text
C:\kny\Project\Unity\UnityTechnicalShowcase
```

## 핵심 원칙

`SkillProject`는 학습/실험장이다.

`UnityTechnicalShowcase`는 포트폴리오용 재설계 프로젝트다.

강의 코드를 그대로 포트폴리오에 복사하지 않는다.

강의에서 개념을 익힌 뒤, 현재 포트폴리오 구조에 맞게 다시 설계해서 적용한다.

## 왜 이렇게 나누는가

스킬 시스템은 앞부분만 보고 구조를 확정하면 위험하다.

강의 후반부에서 다음 구조가 추가되거나 변경될 수 있다.

- Skill Data
- Effect
- Target Search
- Condition
- Cost
- Cooldown
- Editor Tool
- Runtime Skill Flow
- Skill StateMachine
- UI 연동

따라서 강의를 끝까지 들은 뒤 전체 구조를 분석하고, 그 다음 TechShowcase에 맞게 재설계하는 것이 안전하다.

## Project Roles

### SkillProject

역할:

- 인프런 강의 따라가기
- Unity 개념 학습
- ScriptableObject 실험
- EditorWindow 실험
- SerializeReference 실험
- Effect / Target / Stat / Category 구조 이해
- 실패해도 되는 실험 공간

관리 기준:

- 강의 흐름을 우선한다.
- 구조가 다소 지저분해져도 학습 목적이면 허용한다.
- 포트폴리오 품질 기준을 강요하지 않는다.

### UnityTechnicalShowcase

역할:

- 최종 포트폴리오
- 구조 재설계 결과물
- asmdef 기반 모듈화
- Runtime / Editor 분리
- Skill System / Skill Tool / Addressables / Debug / Metrics 중심 구현

관리 기준:

- 강의 구조를 그대로 복사하지 않는다.
- 학습한 개념을 포트폴리오 구조에 맞게 재설계한다.
- 면접에서 설명 가능한 구조만 넣는다.
- 불필요한 실험 코드는 넣지 않는다.

## Recommended Workflow

```text
1. SkillProject에서 강의 진행
2. 강의 단원별 핵심 개념 기록
3. SkillProject 코드에서 실제 구현 방식 확인
4. 강의 완료 후 Codex가 전체 구조 분석
5. 가져갈 개념 / 버릴 구조 분리
6. UnityTechnicalShowcase용 아키텍처 재설계
7. asmdef / Core / Runtime / Modules / Editor 구조 확정
8. TechShowcase에 구현
9. 문서화 / 면접 포인트 정리
```

## Daily Learning Note Template

강의를 들을 때 하루에 길게 정리할 필요는 없다.

아래 5줄 정도만 남기면 충분하다.

```text
날짜:
오늘 만든 기능:
사용한 Unity 개념:
핵심 클래스:
TechShowcase에 가져갈 점:
바꿔야 할 점:
```

예시:

```text
2026-06-11
오늘 만든 기능: SkillSystemWindow에서 데이터 생성 버튼 구현
사용한 Unity 개념: EditorWindow, AssetDatabase, ScriptableObject
핵심 클래스: SkillSystemWindow, IODatabase, IdentifiedObject
TechShowcase에 가져갈 점: ScriptableObject Database 관리 툴 구조
바꿔야 할 점: Runtime / Editor 관심사 분리, asmdef 적용
```

## What To Do Now

현재 단계에서 할 일:

```text
1. SkillProject에서 인프런 강의를 끝까지 진행
2. 학습 중 핵심 개념을 짧게 기록
3. SkillProject가 완성되면 Codex에게 전체 분석 요청
4. 분석 결과를 바탕으로 TechShowcase 재설계
```

TechShowcase에서 지금 해도 되는 것:

```text
- 폴더 구조 정리
- asmdef 개념 학습
- asmdef 생성 준비
- Core / Runtime / Editor 경계 구상
- 문서 정리
```

TechShowcase에서 아직 하지 않는 것이 좋은 것:

```text
- SkillSystem 본 구현
- SkillEditor 본 구현
- Effect 구조 확정
- Target 구조 확정
- Condition 구조 확정
- Runtime Skill Assembly 확정
```

## Final Analysis Plan

인프런 강의를 완료한 뒤 Codex가 분석할 항목:

```text
1. 전체 폴더 구조
2. ScriptableObject 데이터 구조
3. IdentifiedObject / IODatabase 설계
4. SkillSystemWindow Editor Tool 구조
5. Effect / EffectAction 구조
6. TargetSearcher 구조
7. Stat / Category 구조
8. Skill StateMachine 구조
9. Entity StateMachine 구조
10. 실제 동작하는 부분과 빈 껍데기 구분
11. 강의 구조의 장점
12. 강의 구조의 단점
13. TechShowcase에 가져갈 개념
14. TechShowcase에서 버릴 구조
15. asmdef / namespace / module 기준 재설계
```

## Portfolio Story

면접에서 설명할 스토리는 다음 방향으로 잡는다.

```text
처음에는 인프런 강의를 따라가며 모듈형 스킬 시스템의 기본 구조를 학습했습니다.
그 과정에서 ScriptableObject 데이터 구조, EffectAction, TargetSearcher,
EditorWindow 기반 데이터 관리 방식을 익혔습니다.

하지만 포트폴리오 프로젝트에서는 강의 구조를 그대로 복사하지 않고,
asmdef 기반 모듈 구조, Runtime / Editor 분리, 데이터 검증,
Showcase Debug UI에 맞게 재설계했습니다.
```

이 스토리가 중요한 이유:

- 단순 강의 클론이 아니다.
- 학습한 내용을 실무형 구조로 재해석했다.
- Unity 숙련도 상승 과정이 문서로 남는다.
- 면접에서 설계 판단을 설명할 수 있다.

## Current Decision

현재 결정:

```text
SkillProject를 먼저 끝까지 진행한다.
강의 완료 전에는 TechShowcase에 Skill System 본 구현을 넣지 않는다.
강의 완료 후 Codex가 SkillProject 전체를 분석한다.
그 분석을 기반으로 UnityTechnicalShowcase의 Skill System / Skill Tool 구조를 재설계한다.
```
