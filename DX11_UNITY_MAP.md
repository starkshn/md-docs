# DX11 UNITY MAP

이 문서는 기존 DX11 엔진 / Animation Tool 경험을 Unity 연구 주제로 연결한다.

## 목적

면접에서 단순히 Unity 기능을 사용했다고 설명하는 것이 아니라, 직접 엔진을 구현했던 경험을 Unity 구조와 비교해서 설명하기 위함이다.

## Mapping Table

| DX11 / 자체 엔진 경험 | Unity 연구 주제 | 포트폴리오 표현 방식 |
|---|---|---|
| Engine DLL 구조 | Assembly Definition / ModuleHub | 모듈 단위 구조 설계 |
| Prototype Manager | ScriptableObject / Factory | Data Driven Skill 생성 |
| GameObject / Component | Unity GameObject / MonoBehaviour / Component | Component 구조 비교 |
| Scene Manager | Unity Scene / Additive Scene | Scene 전환 실험 |
| Resource Manager | Addressables / Resources / AssetReference | 로딩 구조 비교 |
| Render Target | RenderTexture | Debug View / Before-After View |
| Renderer Pipeline | URP / ScriptableRendererFeature | 렌더링 구조 분석 |
| Animation Channel | AnimationClip / Playables | Animation Preview |
| Bone Hierarchy | Transform Hierarchy | Bone Viewer |
| State Pattern | Animator / StateMachineBehaviour / 직접 FSM | Skill / Animation State |
| Object Pool | Unity Object Pooling | GC / Instantiate 비교 |
| Event System | C# Event / UnityEvent / Scriptable Event | Skill Event / Animation Event |
| Tool Framework | EditorWindow / CustomEditor | Skill Tool / Animation Tool |
| Debug Framework | Gizmos / Handles / Profiler / Frame Debugger | Showcase Debug Panel |

## 우선 연구 주제

1. ScriptableObject + Factory로 Prototype Manager 재해석
2. RenderTexture로 DX11 Render Target Debug 재해석
3. Playables로 Animation Channel / Blend 재해석
4. Object Pooling으로 Runtime Object 관리 재해석
5. EditorWindow로 자체 Tool Framework 재해석

## 설명 방식

각 주제는 아래 구조로 정리한다.

```text
DX11에서는 어떻게 했는가
↓
Unity에서는 어떤 API가 대응되는가
↓
그 차이가 왜 생기는가
↓
포트폴리오에서는 어떻게 구현했는가
↓
면접에서 무엇을 증명하는가
```

## 보존 자료

상세 분석은 아래 폴더에 남긴다.

- `projects/common-engine-dll/`
- `projects/dx11-animation-tool/`
- `projects/dx11-gunfire-reborn/`
- `projects/unity-technical-showcase/`
