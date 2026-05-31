# Module Assembly Definition Plan

## 목적

Assembly Definition은 모듈 경계를 코드 레벨에서 강제한다. Runtime이 Editor를 참조하지 않게 하고, Feature Module이 Core에만 직접 의존하도록 만든다.

## Assembly 구조

```text
NY.Core.Runtime
NY.Core.Editor

NY.Skill.Runtime
NY.Skill.Editor

NY.Animation.Runtime
NY.Animation.Editor

NY.Shader.Runtime
NY.Shader.Editor

NY.Optimization.Runtime
NY.Optimization.Editor

NY.RenderingDebug.Runtime
NY.RenderingDebug.Editor

NY.Comparison.Runtime
NY.Comparison.Editor

NY.Tool.Runtime
NY.Tool.Editor
```

## 참조 규칙

- Runtime Assembly는 Editor Assembly를 참조하지 않는다.
- Feature Module은 Core에만 직접 의존한다.
- Module 간 직접 참조는 최소화한다.
- 공통 데이터 구조는 Core 또는 Shared에 둔다.
- Editor Tool은 Runtime Module을 제어할 수 있다.
- Runtime Module은 Editor Tool을 몰라야 한다.

## 권장 참조 방향

```text
NY.Skill.Runtime -> NY.Core.Runtime
NY.Skill.Editor -> NY.Skill.Runtime
NY.Skill.Editor -> NY.Core.Editor

NY.Tool.Editor -> NY.Core.Editor
NY.Tool.Editor -> NY.Core.Runtime

NY.Comparison.Runtime -> NY.Core.Runtime
NY.RenderingDebug.Runtime -> NY.Core.Runtime
```

## 금지 참조

```text
NY.Core.Runtime -> NY.Skill.Runtime
NY.Skill.Runtime -> NY.Skill.Editor
NY.Skill.Runtime -> NY.Animation.Runtime
NY.Shader.Runtime -> NY.Optimization.Runtime
```

모듈 간 연결은 직접 Assembly 참조 대신 EventBus, Interface, Service, ModuleHub를 통해 처리한다.

## 면접 설명 포인트

Assembly Definition은 단순 빌드 속도 최적화가 아니라 의존성 방향을 강제하기 위한 장치다. Runtime과 Editor를 분리하고 Feature Module 간 직접 결합을 줄였다는 점이 핵심이다.
