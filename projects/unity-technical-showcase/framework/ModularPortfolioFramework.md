# Modular Portfolio Framework

## 목적

Unity Technical Showcase는 여러 기능을 Scene에 직접 붙여 만든 기능 모음이 아니다. 전체 프로젝트는 하나의 `NY Core Framework` 위에 기능 모듈을 계속 쌓아가는 구조로 설계한다.

목표는 다음과 같다.

- 프레임워크 구조가 바뀌어도 각 기능 모듈이 최소 수정으로 대응 가능해야 한다.
- 새 기능을 추가해도 기존 기능을 거의 수정하지 않아야 한다.
- 필요 없는 기능은 쉽게 제거 가능해야 한다.
- Runtime 기능과 Editor Tool 기능 모두 모듈화되어야 한다.
- 전체 모듈을 중앙에서 조회, 활성화, 비활성화, 설정, 상태 확인할 수 있어야 한다.
- 포트폴리오 전체가 “모듈형 기술 쇼케이스 프레임워크”로 보여야 한다.

## 전체 구조

```text
NY Core Framework
↓
NY Module Hub
↓
Category Modules
↓
Feature Modules
↓
Tool Modules
↓
Before / After Comparison
↓
Metrics
↓
Docs / Blog / Interview Notes
```

## 설계 원칙

- 모든 기능은 모듈로 등록된다.
- 모듈은 직접 Scene에 붙어서 독립적으로 움직이지 않는다.
- 모듈의 생명주기는 `NY_Core_ModuleHub`가 통제한다.
- Runtime 모듈과 Editor Tool 모듈은 분리한다.
- 모듈 간 직접 참조를 피하고 `NY_Core_ModuleContext`, EventBus, ServiceLocator 또는 DI Container를 통해 연결한다.
- Before/After 비교, Metrics, Docs, Blog, Interview Notes는 모듈 메타데이터와 연결한다.

## 핵심 클래스

```text
NY_Core_ModuleHub
NY_Core_ModuleRegistry
NY_Core_ModuleController
NY_Core_ModuleDependencyGraph
NY_Core_ModuleMetricsCenter
NY_Core_ModuleContext
NY_Tool_ModuleDashboard
```

## 핵심 인터페이스

```csharp
public interface INY_Module
{
    string Id { get; }
    string DisplayName { get; }
    ENY_ModuleCategory Category { get; }
    ENY_ModuleState State { get; }

    void Initialize(NY_Core_ModuleContext context);
    void Enable();
    void Disable();
    void ResetModule();
    void Tick(float deltaTime);

    NY_Core_ModuleMetrics GetMetrics();
}
```

```csharp
public interface INY_ToolModule : INY_Module
{
    void DrawToolGUI();
    void DrawDebugGUI();
    void BindTargetModule(INY_Module module);
}
```

```csharp
public interface INY_ComparableModule
{
    void CaptureBefore();
    void CaptureAfter();
    NY_Comparison_Data GetComparisonData();
}
```

## 모듈 카테고리

- Core
- Skill
- Animation
- Shader
- Optimization
- RenderingDebug
- Tool
- Comparison
- Metrics
- Documentation

## 확장 방식

새 기능을 추가할 때는 다음 절차를 따른다.

1. Backlog에서 Must / Should / Could / Won't 위치를 정한다.
2. Architecture Governance 검사를 통과한다.
3. `INY_Module` 또는 `INY_ToolModule` 구현 여부를 결정한다.
4. `NY_Core_ModuleDescriptor`를 작성한다.
5. `NY_Core_ModuleRegistry`에 등록한다.
6. 필요하면 `INY_ComparableModule`을 구현한다.
7. Metrics, Docs, Blog, Interview Notes 연결 여부를 정의한다.

## 제거 방식

모듈 제거 시 다른 기능이 깨지지 않아야 한다.

- 다른 모듈이 직접 참조하지 않아야 한다.
- 의존성은 `NY_Core_ModuleDependencyGraph`에서만 관리한다.
- 이벤트 구독은 Disable/Dispose 단계에서 해제한다.
- Tool Module은 Target Module이 없을 때 비활성 상태로 표시한다.

## 면접 설명 포인트

이 구조는 Unity 기능을 단순히 만든 것이 아니라, 직접 엔진을 만들었던 경험을 Unity 포트폴리오 구조로 재해석한 것이다. 핵심은 기능 수가 아니라 기능을 추가/제거/비교/문서화할 수 있는 프레임워크를 설계했다는 점이다.
