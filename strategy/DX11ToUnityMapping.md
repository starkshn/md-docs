# DX11 to Unity Mapping

## 목적

DX11 엔진 제작 경험은 이 포트폴리오의 핵심 차별화 포인트다. 이 문서는 DX11에서 직접 구현했던 개념을 Unity에서 어떤 API와 구조로 재해석하는지 정리한다.

## Mapping Table

| DX11 / Custom Engine | Unity | 포트폴리오 적용 |
| --- | --- | --- |
| Prototype Manager | ScriptableObject + Factory | SkillDefinitionSO, SkillFactory |
| GameObject / Component 구조 | GameObject / MonoBehaviour / Component | SkillController, FeatureModule Host |
| Resource Manager | Addressables / Resources / AssetDatabase | Asset 관리와 Tool Save/Load |
| Render Target Debug | RenderTexture / Camera.targetTexture | Before/After Comparison, Debug View |
| Shader Pass | ShaderLab / HLSL / URP Pass | Rim, Dissolve, Outline, Debug Shader |
| Render Pipeline 제어 | URP ScriptableRendererFeature / ScriptableRenderPass | Rendering Debug View |
| Animation Channel | AnimationClip / Playables API | Animation Preview, Blend, Event Timeline |
| Bone Hierarchy | Transform Hierarchy / Animator Bone | Bone Viewer |
| Scene Manager | SceneManager / Addressables Scene Loading | Showcase Scene 구성 |
| Object Pool | Custom Pool / Unity Pool API | Pooling Module, Metrics |
| Manager Singleton | Service / Bootstrap / ScriptableObject Config | FeatureToggleManager, ModuleMetricsProvider |
| Debug UI | UGUI / UI Toolkit / EditorWindow | Showcase Control Panel |

## 면접에서 설명할 핵심

이 포트폴리오는 Unity API를 단순히 따라 쓰는 프로젝트가 아니다. DX11에서 직접 다뤘던 렌더 타겟, 애니메이션 채널, 리소스 관리, 오브젝트/컴포넌트 구조를 Unity 방식으로 재해석한 프로젝트다.

예시 설명:

```text
DX11에서는 Render Target을 직접 만들고 RTV/SRV를 관리했지만, Unity에서는 Camera.targetTexture와 RenderTexture로 같은 개념을 구성했습니다. 이 구조를 Before/After Comparison System에 적용해 기능 적용 전후를 시각적으로 비교했습니다.
```

```text
DX11 Animation Tool에서는 Animation Channel과 Bone Matrix를 직접 계산했지만, Unity에서는 AnimationClip, Transform Hierarchy, Playables API를 활용해 Preview와 Event Timeline을 구성했습니다.
```

## 블로그 주제

- DX11 Render Target Debug를 Unity RenderTexture로 옮기기
- DX11 Prototype Manager와 Unity ScriptableObject Factory 비교
- DX11 Animation Channel과 Unity Playables API 비교
- Custom Engine Component 구조와 Unity Component 구조 비교
