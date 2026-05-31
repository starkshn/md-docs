# Module Dashboard Design

## 목적

`NY_Tool_ModuleDashboard`는 전체 모듈을 조회하고 제어하는 Editor Tool 또는 Runtime Tool이다. 포트폴리오의 “모듈형 프레임워크” 성격을 실행 화면에서 보여주는 핵심 도구다.

## 역할

- 등록된 모듈 목록 표시
- 카테고리별 필터링
- 모듈 ON/OFF
- 모듈 Reset
- 모듈 의존성 표시
- 모듈별 Metrics 표시
- Before / After 지원 여부 표시
- Tool Module 연결 상태 표시
- Blog / Docs / Interview Notes 링크 표시

## 예시 UI

```text
[Core]
  [ON] NY_Core_ModuleHub
  [ON] NY_Comparison_ViewSystem

[Skill]
  [ON] NY_Skill_SystemModule
  [ON] NY_Skill_EditorModule
  [ON] NY_Skill_ValidationModule

[Shader]
  [OFF] NY_Shader_DissolveModule
  [ON] NY_Shader_OutlineModule

[Optimization]
  [ON] NY_Optimization_PoolingModule
  [OFF] NY_Optimization_LODModule
```

## 데이터 소스

Dashboard는 `NY_Core_ModuleDescriptor`를 기반으로 표시한다.

```csharp
[Serializable]
public class NY_Core_ModuleDescriptor
{
    public string Id;
    public string DisplayName;
    public ENY_ModuleCategory Category;
    public string Description;
    public string[] Dependencies;
    public bool SupportsComparison;
    public bool SupportsMetrics;
    public bool HasEditorTool;
}
```

## 표시 항목

| 항목 | 설명 |
| --- | --- |
| Module Id | 내부 식별자 |
| Display Name | UI 표시명 |
| Category | Skill, Shader 등 카테고리 |
| State | Registered, Initialized, Enabled 등 상태 |
| Dependencies | 필요한 모듈 목록 |
| Metrics | FPS, GC, 실행 시간 등 |
| Comparison | Before/After 지원 여부 |
| Tool | Tool Module 연결 여부 |
| Docs | Markdown 링크 |
| Blog | Blog Draft 링크 |
| Interview | Interview Notes 링크 |

## 확장 포인트

- 모듈 검색
- 카테고리 필터
- Risk 상태 표시
- KPI Level 표시
- Notion 링크 표시
- Demo Video 링크 표시
- Module Descriptor 기반 Docs 자동 생성

## 면접 설명 포인트

Dashboard는 기능을 많이 만들었다는 표시가 아니라, 모든 기능을 하나의 프레임워크에서 관리한다는 증거다. 모듈 상태, 의존성, Metrics, Before/After 지원 여부를 한 화면에서 보여주면 프로젝트 관리 능력과 도구 제작 능력을 동시에 보여줄 수 있다.
