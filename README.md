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

