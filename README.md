# Technical Portfolio Documentation

This repository is the source-of-truth documentation workspace for my game client technical portfolio.

The Markdown files are the primary artifacts. PlantUML diagrams are managed next to the Markdown files that explain them, so the same content can later be reused in a technical blog, GitHub portfolio, or a static portfolio website.

## Folder Structure

```text
technical-portfolio-docs/
  README.md
  workflow/
    Workflow.md
    BlogPortfolioPublishing.md
  projects/
    dx11-gunfire-reborn/
      ProjectAnalysis.md
      RenderingPipeline.md
      PerformanceOptimization.md
      uml/
    dx11-animation-tool/
      ProjectAnalysis.md
      AnimationSystem.md
      uml/
    common-engine-dll/
      EngineArchitecture.md
      ResourceSystem.md
      DesignPatternAnalysis.md
      uml/
    unity-technical-showcase/
      ArchitectureDesign.md
      DevelopmentRoadmap.md
      uml/
  shared/
    templates/
    uml/
```

## Projects

- [DX11 Gunfire Reborn Clone](projects/dx11-gunfire-reborn/ProjectAnalysis.md)
- [DX11 Animation Tool](projects/dx11-animation-tool/ProjectAnalysis.md)
- [Common Engine DLL](projects/common-engine-dll/EngineArchitecture.md)
- [Unity Technical Showcase](projects/unity-technical-showcase/ArchitectureDesign.md)

## MVP First Release\n\n- [MVP Scope Strategy](projects/unity-technical-showcase/mvp/MvpScopeStrategy.md)\n- [Technical Showcase Scene Design](projects/unity-technical-showcase/showcase-scene/ShowcaseSceneDesign.md)\n- [Before / After Rule](projects/unity-technical-showcase/showcase-scene/BeforeAfterRule.md)\n- [Feature Documentation Template](projects/unity-technical-showcase/feature-template/FeatureDocumentationTemplate.md)\n\n## Workflow

- [Documentation Workflow](workflow/Workflow.md)
- [Blog and Portfolio Publishing Workflow](workflow/BlogPortfolioPublishing.md)

## Authoring Rule

1. Write or update Markdown first.
2. Extract architecture relationships from Markdown into PlantUML.
3. Keep each PlantUML file beside the project document it belongs to.
4. Use `shared/uml` only for duplicated or cross-project diagrams.
5. Link documents with relative Markdown links so they can be reused in GitHub, a static blog, or a portfolio website.


## Learning / Blog / Journal Workflow

이 포트폴리오는 기능 구현 자체보다 “학습한 개념을 실무 수준의 구조로 재설계하고 설명하는 과정”을 증명하는 것이 목표다.

필수 개발 사이클:

```text
Concept Study
↓
Architecture Design
↓
Mini Experiment
↓
Implementation
↓
Verification
↓
Git Commit
↓
Markdown Documentation
↓
PlantUML Update
↓
Tistory Blog Draft
↓
Notion Development Journal
↓
Interview Notes
```

관련 문서:

- [LearningBlogPortfolioStrategy](workflow/LearningBlogPortfolioStrategy.md)
- [DevelopmentCycleEnforcement](workflow/DevelopmentCycleEnforcement.md)
- [NotionJournalAndWeeklyReview](workflow/NotionJournalAndWeeklyReview.md)
- [DifferentiationTrackingSystem](workflow/DifferentiationTrackingSystem.md)

Codex는 기능 구현 시 항상 공부한 개념, 강의 구조 분석, 우리 구조와의 차이점, 변경 이유, 모듈화 포인트, 확장성 포인트, 기술 블로그 초안, 면접 설명 포인트, PlantUML, 최종 아키텍처 반영 내용을 함께 산출해야 한다.

## Strategy Layer: KPI / Risk / Recruiter Mode

포트폴리오가 무한 확장되지 않도록 전략 계층을 추가한다. 앞으로 기능을 추가하거나 완료 판단을 할 때는 아래 문서를 먼저 확인한다.

- [PortfolioKpiSystem](strategy/PortfolioKpiSystem.md)
- [FeatureBacklog](strategy/FeatureBacklog.md)
- [PortfolioRiskLog](strategy/PortfolioRiskLog.md)
- [PortfolioDashboard](strategy/PortfolioDashboard.md)
- [DX11ToUnityMapping](strategy/DX11ToUnityMapping.md)
- [DemoVideoPlan](strategy/DemoVideoPlan.md)
- [RecruiterMode](strategy/RecruiterMode.md)

최상위 질문:

```text
이 기능이 일반 Unity 포트폴리오와 비교해서 어떤 차별성을 만들고 있는가?
```

이 질문에 답하지 못하면 기능을 추가하지 않는다.

## Master Plan Diagram

전체 포트폴리오 구조, 전략 계층, 개발 사이클, MVP 우선순위, 산출물 흐름은 아래 PlantUML에서 한눈에 확인한다.

- [PortfolioMasterPlan.puml](shared/uml/PortfolioMasterPlan.puml)
