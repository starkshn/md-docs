# Unity Technical Showcase

## MVP Priority

### MVP 1

- [Modular Skill System](skill-system/00_README.md)
- [Skill Editor](skill-editor/00_README.md)
- [Technical Showcase Scene](showcase-scene/ShowcaseSceneDesign.md)
- Markdown Docs
- PlantUML

### MVP 2

- Animation Tool
- Animation Event and Skill integration
- Shader Showcase

### MVP 3

- Optimization Showcase
- Rendering Debug View
- Tistory Blog Series polish

## Documents

- [Architecture Design](ArchitectureDesign.md)
- [Development Roadmap](DevelopmentRoadmap.md)
- [Learning And Implementation Plan](learning/LearningAndImplementationPlan.md)
- [MVP Scope Strategy](mvp/MvpScopeStrategy.md)
- [Feature Documentation Template](feature-template/FeatureDocumentationTemplate.md)
- [Showcase Scene Design](showcase-scene/ShowcaseSceneDesign.md)
- [Before / After Rule](showcase-scene/BeforeAfterRule.md)

## UML

- [Unity Portfolio Architecture](uml/UnityPortfolioArchitecture.puml)
- [Skill Execution Sequence](uml/SkillExecutionSequence.puml)
- [Unity Workflow](uml/UnityWorkflow.puml)
- [MVP Priority Structure](mvp/MvpPriorityStructure.puml)
- [Showcase Dashboard Layout](showcase-scene/ShowcaseDashboardLayout.puml)

## Blog Candidates

- Designing a data-driven modular skill system in Unity
- Building a Unity skill editor for runtime assembly
- Creating a technical showcase instead of a generic RPG portfolio
- Building a portfolio dashboard that shows Before / After technical improvements

## Feature Toggle / Before-After Showcase Core

포트폴리오의 모든 기능은 `IFeatureModule` 기반 독립 모듈로 설계한다. `FeatureToggleManager`가 ON/OFF, 의존성, 상태, 로그, Metrics를 관리하고, `ComparisonViewSystem`이 Before/After RenderTexture 비교를 담당한다.

관련 문서:

- [FeatureToggleArchitecture](feature-toggle/FeatureToggleArchitecture.md)
- [BeforeAfterComparisonSystem](feature-toggle/BeforeAfterComparisonSystem.md)
- [ShowcaseControlPanelDesign](feature-toggle/ShowcaseControlPanelDesign.md)
- [RenderTargetComparisonDesign](feature-toggle/RenderTargetComparisonDesign.md)
- [InflearnSkillSystemAdaptation](feature-toggle/InflearnSkillSystemAdaptation.md)

핵심 원칙:

- 강의 구조는 그대로 복사하지 않고 현재 포트폴리오 구조에 맞게 재설계한다.
- 모든 주요 기능은 Runtime에서 ON/OFF 가능해야 한다.
- 모든 주요 기능은 Before/After 비교와 Metrics를 제공해야 한다.
- Showcase Control Panel이 시연 UX의 중심이다.
