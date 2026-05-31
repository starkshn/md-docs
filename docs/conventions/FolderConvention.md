# Folder Convention

## Unity 폴더 구조

```text
Assets/_Project/
  Core/
    Runtime/
      Modules/
      Services/
      Events/
      Metrics/
    Editor/
      ModuleDashboard/
  Modules/
    Skill/
      Runtime/
      Editor/
      Data/
      Tests/
      Docs/
    Animation/
      Runtime/
      Editor/
      Data/
      Tests/
      Docs/
    Shader/
      Runtime/
      Editor/
      Data/
      Tests/
      Docs/
    Optimization/
      Runtime/
      Editor/
      Data/
      Tests/
      Docs/
    RenderingDebug/
      Runtime/
      Editor/
      Data/
      Tests/
      Docs/
  Showcase/
    Scenes/
    UI/
    Prefabs/
  Comparison/
    Runtime/
    Editor/
  Shared/
    Runtime/
    Editor/
```

## 원칙

- 폴더는 기능 카테고리 기준으로 나눈다.
- Runtime, Editor, Data, Tests, Docs를 명확히 분리한다.
- 클래스명에는 `NY_Category_Role`을 사용하지만 폴더명은 과도한 Prefix를 붙이지 않는다.
- `Assets/_Project` 아래에 포트폴리오 코드를 모아 Unity 기본/외부 에셋과 분리한다.
