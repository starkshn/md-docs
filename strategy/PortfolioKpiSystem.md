# Portfolio KPI System

## 목적

현재 포트폴리오 문서는 무엇을 만들 것인지는 잘 정의되어 있다. 하지만 언제 성공했다고 판단할 것인지가 부족하다. KPI 시스템은 기능별 완성도를 Level로 나누고, 무한 확장을 막으며, 매주 진행률을 판단하기 위한 기준이다.

## 공통 KPI 원칙

각 기능은 Level 1부터 Level 5까지 단계적으로 평가한다.

- Level 1: 최소 개념 검증
- Level 2: 핵심 구조 분리
- Level 3: 런타임 통합
- Level 4: Tool / UI 연동
- Level 5: Before/After, Metrics, 문서, 면접 설명까지 완료

## Skill System KPI

| Level | 기준 | 완료 조건 |
| --- | --- | --- |
| Level 1 | Effect 분리 | Effect를 독립 인터페이스 또는 Definition으로 분리 |
| Level 2 | Target / Condition / Cooldown 분리 | Targeting, Condition, Cooldown 책임 분리 |
| Level 3 | Runtime Assembly | SkillDefinitionSO를 SkillFactory가 SkillInstance로 조립 |
| Level 4 | Tool 연동 | Skill Editor 또는 Showcase Panel에서 Skill 구성 변경 가능 |
| Level 5 | Before/After + Metrics | 하드코딩 Skill과 모듈형 Skill 비교, 실행 로그와 Metrics 표시 |

## Skill Tool KPI

| Level | 기준 | 완료 조건 |
| --- | --- | --- |
| Level 1 | Skill Asset 생성 | SkillDefinitionSO 생성 가능 |
| Level 2 | 모듈 편집 | Effect, Target, Condition, Cooldown 추가/수정 가능 |
| Level 3 | Validation | 누락/오류 설정 검증 가능 |
| Level 4 | Preview | Tool에서 Skill 실행 미리보기 가능 |
| Level 5 | Timeline + Recruiter Demo | Event Timeline, Metrics, 3분 시연 흐름 제공 |

## Animation Tool KPI

| Level | 기준 | 완료 조건 |
| --- | --- | --- |
| Level 1 | Clip Preview | Animation Clip 재생 미리보기 가능 |
| Level 2 | Bone Viewer | Bone Hierarchy 시각화 가능 |
| Level 3 | Event Timeline | Animation Event 타임라인 표시 가능 |
| Level 4 | Skill Event 연동 | Animation Event가 Skill 실행 흐름과 연결 |
| Level 5 | DX11 비교 설명 | DX11 Animation Channel과 Unity Playables 비교 문서화 |

## Shader Showcase KPI

| Level | 기준 | 완료 조건 |
| --- | --- | --- |
| Level 1 | Rim / Fresnel | 기본 커스텀 HLSL 셰이더 구현 |
| Level 2 | Dissolve | 파라미터 기반 Dissolve 구현 |
| Level 3 | Outline | Outline 방식 하나 이상 구현 |
| Level 4 | Feature Module 연동 | 셰이더 기능 ON/OFF 및 파라미터 UI 제공 |
| Level 5 | Before/After + SRP Batcher | 기본 Material과 비교, SRP Batcher 고려점 문서화 |

## Optimization Showcase KPI

| Level | 기준 | 완료 조건 |
| --- | --- | --- |
| Level 1 | Object Pooling | Pool 적용 전후 비교 가능 |
| Level 2 | LOD | LOD 적용 전후 비교 가능 |
| Level 3 | GPU Instancing | Draw Call 변화 표시 가능 |
| Level 4 | Metrics Dashboard | FPS, GC, Draw Call, Object Count 표시 |
| Level 5 | Recruiter Summary | 왜 실무적인 최적화인지 면접 설명 문서화 |

## Rendering Debug View KPI

| Level | 기준 | 완료 조건 |
| --- | --- | --- |
| Level 1 | RenderTexture View | Main Camera 결과를 RenderTexture로 표시 |
| Level 2 | Multi Camera | Before/After 또는 Debug Camera 구성 |
| Level 3 | Depth / Normal | Depth 또는 Normal Debug View 구현 |
| Level 4 | Render Pass | URP ScriptableRenderPass 후보 구조 적용 |
| Level 5 | 영상 시연 | 30초 GIF, 3분 설명 영상 계획 포함 |

## 완료 판단

KPI Level 5는 단순 구현 완료가 아니다. 다음 산출물이 있어야 한다.

- Source Code
- Git Commit
- Markdown
- PlantUML
- Before/After 비교
- Metrics
- Blog Draft
- Notion Journal
- Interview Notes
- Recruiter Summary
