# Inflearn Skill System Adaptation Rule

## 목적

Inflearn의 `유니티 모듈식 스킬 시스템` 강의는 그대로 복사할 대상이 아니라 학습 기준이다. 강의에서 얻은 개념을 현재 Unity Technical Showcase 아키텍처에 맞게 재설계해서 적용한다.

## 유지할 개념

- Modular Skill System
- ScriptableObject 기반 Skill Definition
- Effect / Target / Condition / Cooldown 분리
- Runtime Skill Assembly
- Editor Tool을 통한 Skill Asset 생성
- 데이터 기반 스킬 구성

## 변경해야 할 구조

강의 구조는 포트폴리오 구조에 맞게 다음 기준으로 바꾼다.

- 클래스 네이밍
- 폴더 구조
- Assembly Definition 분리
- Runtime / Editor 모듈 분리
- Feature Toggle System 연동
- Before / After Comparison System 연동
- Showcase Control Panel 연동
- Metrics Panel 연동
- RenderTarget 비교 구조 연동

## 매핑 규칙

```text
강의 Skill System
 -> SkillSystemModule

강의 Skill Editor
 -> SkillEditorModule

강의 Skill Data
 -> SkillDefinitionSO / EffectDefinitionSO / TargetingDefinitionSO / ConditionDefinitionSO

강의 Runtime Skill
 -> SkillInstance / SkillFactory / SkillController

강의 Tool UI
 -> ShowcaseControlPanel + SkillEditorPanel

강의 Debug 출력
 -> ModuleMetricsProvider + MetricsView + SkillEventTimeline

강의 단일 실행 화면
 -> Before / After RenderTarget Comparison View
```

## SkillSystemModule 요구사항

`SkillSystemModule`은 `IFeatureModule`을 구현한다.

- `FeatureToggleManager`에서 ON/OFF 가능해야 한다.
- `Enable` 시 스킬 시스템이 활성화된다.
- `Disable` 시 스킬 입력, 실행, 이펙트 출력이 중단된다.
- `Reset` 시 쿨타임, 타겟 상태, 실행 로그가 초기화된다.
- `GetMetrics`로 스킬 실행 횟수, 평균 실행 시간, 생성 Effect 수, GC Alloc 등을 반환한다.
- Before / After 비교 시스템과 연결된다.

## Skill Tool 구조

```text
ShowcaseControlPanel
 ├─ FeatureToggleView
 ├─ SkillEditorPanel
 ├─ SkillRuntimePanel
 ├─ SkillValidationPanel
 ├─ SkillEventTimeline
 └─ MetricsView
```

## Before / After Skill 비교

Before:

- 하드코딩된 스킬 실행
- Target / Effect / Condition 결합
- Tool 수정 불가
- 실행 흐름 확인 어려움
- Validation 없음

After:

- ScriptableObject 기반 Skill Definition
- Effect / Target / Condition / Cooldown 분리
- Runtime Skill Assembly
- Tool에서 스킬 구성 변경 가능
- Skill Event Timeline으로 실행 흐름 확인
- Validation Panel로 데이터 오류 확인
- MetricsView로 실행 비용 확인

## Codex 판단 기준

스킬 강의 내용을 적용할 때마다 다음 질문에 답한다.

1. 강의 구조를 그대로 넣어도 되는가?
2. Feature Module 구조와 충돌하지 않는가?
3. Runtime Assembly와 Editor Tool이 분리되어 있는가?
4. Before / After 비교 시스템과 연결 가능한가?
5. Showcase Control Panel에서 제어 가능한가?
6. MetricsView에 표시할 데이터가 있는가?
7. Animation, Shader, Optimization으로 확장 가능한가?
8. 면접에서 설명 가능한 구조인가?
9. 블로그 글에 학습 과정과 설계 변경 이유가 드러나는가?

## 문서화 형식

강의 내용을 참고할 때마다 다음 형식으로 남긴다.

```text
## 강의 원본 구조
## 그대로 사용할 부분
## 우리 프로젝트에 맞게 변경할 부분
## 최종 적용 구조
## 수정 이유
```

## 필수 PlantUML

- 강의 원본 구조 다이어그램
- 포트폴리오 적용 구조 다이어그램
- 강의 구조에서 우리 구조로 변환되는 Mapping Diagram
- Skill Runtime Sequence Diagram
- Skill Editor Tool Flow Diagram
- Before / After Skill Comparison Diagram

## 면접에서 설명할 포인트

강의를 따라 만든 것이 아니라, 강의에서 배운 모듈형 스킬 개념을 포트폴리오의 Feature Module, Before/After Comparison, Showcase Control Panel 구조에 맞게 재설계했다는 점을 강조한다.
