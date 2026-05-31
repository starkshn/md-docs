# Assembly Convention

## Assembly Naming

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

## 규칙

- Runtime은 Editor를 참조하지 않는다.
- Feature Runtime은 Core Runtime만 직접 참조한다.
- Feature Editor는 자기 Runtime과 Core Editor를 참조할 수 있다.
- 모듈 간 직접 참조는 피하고 EventBus, Context, Interface로 연결한다.
- Assembly 변경이 필요하면 Architecture Governance Report에 영향 범위를 남긴다.
