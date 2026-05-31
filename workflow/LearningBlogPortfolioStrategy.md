# Learning Based Portfolio Development and Blog Strategy

## 목적

본 포트폴리오는 단순히 기능을 구현하는 프로젝트가 아니다. 포트폴리오를 제작하는 과정 자체가 학습 과정이며, 학습 내용을 Technical Docs, Tistory Blog, Notion Development Journal, Interview Notes로 남기는 것을 목표로 한다.

기능 구현보다 중요한 것은 다음을 설명할 수 있는 것이다.

- 어떤 개념을 공부했는가
- 왜 해당 개념이 필요한가
- Unity에서는 어떻게 적용되는가
- DX11 / Unreal 경험과 어떻게 연결되는가
- 어떤 문제를 발견했는가
- 어떤 구조로 해결했는가
- 왜 해당 설계를 선택했는가
- 어떤 확장성을 확보했는가

## 개발 과정 = 학습 과정 = 블로그 작성 과정

각 기능은 아래 순서로 진행한다.

```text
개념 학습
↓
미니 실험
↓
강의 구조 분석
↓
우리 프로젝트 구조에 맞게 재설계
↓
포트폴리오 적용
↓
문서화
↓
기술 블로그 작성
↓
면접 정리
```

기능을 만들고 나서 블로그를 작성하는 것이 아니다. 기능을 공부하는 순간부터 블로그 초안을 함께 작성한다.

## Skill System 개발 중 반드시 기록할 내용

Skill System을 구현하면서 아래 내용을 계속 기록한다.

### 공부한 개념

- Data Driven Design
- ScriptableObject
- Factory Pattern
- Strategy Pattern
- Command Pattern
- Runtime Assembly
- Dependency Injection
- SOLID
- Feature Toggle Architecture

### 강의 구조

강의에서는 어떤 구조를 사용했는지 정리한다.

```text
Skill
Effect
Target
Condition
Cooldown
Skill Editor
```

### 우리 프로젝트 구조

강의 구조를 우리 포트폴리오 구조에 맞게 어떻게 변경했는지 정리한다.

```text
SkillSystemModule
SkillDefinitionSO
EffectDefinitionSO
TargetingDefinitionSO
ConditionDefinitionSO
SkillFactory
SkillInstance
SkillController
SkillEditorModule
FeatureToggleManager
ComparisonViewSystem
ShowcaseControlPanel
```

### 변경 이유

- 왜 강의 구조를 그대로 사용하지 않았는가?
- Feature Module 구조와 통합해야 하는 이유는 무엇인가?
- Before / After 비교 시스템과 연동해야 하는 이유는 무엇인가?
- Tool Framework와 연결해야 하는 이유는 무엇인가?
- 확장성을 어떻게 확보했는가?

## 기술 블로그에서 강조할 부분

기술 블로그는 단순 구현 방법을 설명하는 글이 아니다. 다음 흐름을 중심으로 작성한다.

1. 공부한 개념
2. 강의 구조 분석
3. 문제점 발견
4. 구조 개선
5. 최종 설계
6. 얻은 인사이트

예시 흐름:

```text
모듈형 스킬 시스템을 공부하면서 Strategy Pattern을 다시 정리했다.
강의에서는 이런 구조를 사용했다.
하지만 현재 포트폴리오 구조에는 그대로 맞지 않았다.
그래서 Feature Module 구조로 변경했다.
최종적으로 SkillSystemModule, SkillFactory, SkillInstance, SkillEventTimeline 구조를 사용했다.
단순히 강의를 따라치는 것보다 실제 프로젝트 구조에 맞게 재설계하는 과정이 훨씬 중요했다.
```

## 모듈화 자체를 블로그 주제로 활용

포트폴리오의 가장 큰 차별점은 기능이 아니라 모듈화다. 모든 기능은 “어떻게 모듈화했는가”를 설명할 수 있어야 한다.

| 대상 | 블로그 핵심 질문 |
| --- | --- |
| Skill System | 왜 Effect / Target / Condition을 분리했는가 |
| Skill Tool | 왜 Runtime과 Editor를 분리했는가 |
| Animation Tool | 왜 Playables를 사용했는가 |
| Shader Showcase | 왜 Shader를 Feature Module로 만들었는가 |
| Optimization Showcase | 왜 각 최적화 기능을 독립 모듈로 만들었는가 |
| Rendering Debug View | 왜 RenderTexture 기반 비교 구조를 만들었는가 |

## 포트폴리오 차별화 포인트 문서화

Codex는 기능 구현보다 먼저 “이 기능의 차별화 포인트”를 정의해야 한다.

예시:

```text
기능: Object Pooling

일반적인 구현:
Pool Manager 하나 생성

포트폴리오 구현:
Feature Module로 ON/OFF 가능
Before/After 비교 가능
Metrics 출력 가능
Debug UI 제공
Markdown 문서화
PlantUML 작성
Blog Draft 작성
Interview Notes 작성
```

## 기술 블로그 시리즈 추가

### 모듈화 시리즈

- 왜 모든 기능을 Feature Module로 설계했는가
- Runtime과 Editor를 분리한 이유
- Assembly Definition 기반 모듈화
- Feature Toggle Architecture 설계

### 강의 재설계 시리즈

- 모듈형 스킬 시스템 강의 분석
- 강의 구조를 실무 구조로 바꾸기
- Skill Tool 구조 개선하기
- Runtime Skill Assembly 재설계

### 포트폴리오 아키텍처 시리즈

- Unity Technical Showcase 전체 구조
- Before / After Comparison Framework
- RenderTarget 기반 기술 시연 시스템
- Showcase Control Panel 설계

## Codex가 항상 기억해야 할 것

포트폴리오의 목표는 “스킬 시스템 구현”이 아니다.

목표는 “공부한 개념을 실무 수준의 모듈형 구조로 재설계하고 그 과정을 설명할 수 있는 개발자”임을 증명하는 것이다.

따라서 Codex는 기능 구현 시 항상 아래 내용을 함께 산출해야 한다.

- 공부한 개념
- 강의 구조 분석
- 우리 구조와의 차이점
- 변경 이유
- 모듈화 포인트
- 확장성 포인트
- 기술 블로그 초안
- 면접 설명 포인트
- PlantUML
- 최종 아키텍처 반영 내용
