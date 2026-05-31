@'
# Development Roadmap And Workflow

## 전체 기간 산정

Unity 숙련도가 아직 부족하다는 전제를 반영하면, 현실적인 개발 기간은 9~12개월이다. 퇴근 후와 주말 기준으로 주 12~18시간을 확보한다면 다음 일정이 적절하다.

## Phase 0: Unity 기초 재정비 - 4주

목표:

- Unity 프로젝트 구조 익숙해지기
- URP, Prefab, ScriptableObject, Assembly Definition, Addressables 기초 습득
- EditorWindow 기초 실습

산출물:

- 샘플 캐릭터 이동
- 간단 Skill 1개
- ScriptableObject 데이터 1개
- 간단 EditorWindow 1개

## Phase 1: Core / Skill Runtime Vertical Slice - 6주

목표:

- 데이터 기반 Skill System 최소 완성
- Target, Effect, Cooldown, Condition 분리
- Runtime Skill Assembly 구현

산출물:

- Skill 3종
- Target 방식 3종
- Effect 4종
- Cooldown UI
- PlayMode 테스트 일부

## Phase 2: Skill Editor - 6주

목표:

- Skill 생성/편집/저장/로드
- Effect/Condition/Target/Cooldown 모듈 편집
- Validation 및 Preview

산출물:

- Skill Editor Window
- Undo/Redo 일부
- Validation Log
- Preview 실행

## Phase 3: Animation Tool - 8주

목표:

- DX11 Animation Tool 경험을 Unity Editor로 재현
- Preview, Blend, Bone Viewer, Event Editor 구현

산출물:

- Animation Preview Window
- PlayableGraph 기반 Blend
- Bone Gizmo
- Event Timeline
- Skill Event 연동

## Phase 4: Shader Showcase - 6주

목표:

- DX11 렌더링 경험을 URP Shader로 시각화
- Rim, Dissolve, Fresnel, Toon, Outline, Distortion, Hologram 구현

산출물:

- Shader Viewer Scene
- Material parameter UI
- 전/후 비교 뷰

## Phase 5: Optimization Showcase - 6주

목표:

- 최적화 토글과 실시간 지표 표시
- 성능 개선 전/후 비교 가능

산출물:

- LOD, Culling, Pooling, Addressables, Instancing 샘플
- Metric Overlay
- Stress Test 버튼

## Phase 6: Rendering Debug View - 4주

목표:

- RenderTexture 멀티뷰 구성
- Normal, Wireframe, Overdraw, Shadow, Depth View 구현

산출물:

- Debug Camera Grid
- RendererFeature 일부
- Debug View UI

## Phase 7: Polish / Docs / Video - 4주

목표:

- README, UML, 기술 문서 정리
- 3~5분 시연 영상 제작
- GitHub 공개 준비

산출물:

- GitHub README
- `/Docs` 문서
- PlantUML
- Demo 영상
- 기술 블로그 글 2~3개

## 총 기간

- 최소: 8개월
- 권장: 10개월
- 안정: 12개월

현재 Unity 숙련도가 부족하므로 6개월 완성 계획은 리스크가 높다. 10개월 계획으로 잡고, 3개월마다 공개 가능한 Milestone을 만드는 것이 낫다.

## 주간 워크플로우

평일:

- 3일: 구현 1.5~2시간
- 1일: Unity 학습/문서 읽기 1시간
- 1일: 리팩토링/정리 1시간

주말:

- 토요일: 4~5시간 핵심 기능 구현
- 일요일: 3~4시간 테스트, 문서, 영상 캡처

## 기능별 완료 기준

각 기능은 다음 조건을 만족해야 완료로 본다.

- Runtime에서 동작한다.
- Editor 또는 Debug UI에서 조작 가능하다.
- Before/After 또는 Debug View가 있다.
- README에 설명 가능하다.
- 최소 1개 이상의 UML 또는 구조 다이어그램이 있다.
- 짧은 영상으로 보여줄 수 있다.

## Git 관리 전략

브랜치:

- `main`: 안정 데모
- `dev`: 통합 개발
- `feature/skill-runtime`
- `feature/skill-editor`
- `feature/animation-tool`
- `feature/shader-showcase`
- `feature/optimization-showcase`
- `feature/debug-view`

커밋 규칙:

- `feat(skill): add runtime target resolver`
- `editor(skill): add effect module inspector`
- `render(shader): add dissolve shader`
- `perf(pool): add projectile pool benchmark`
- `docs: add skill architecture diagram`

## 이직 경쟁력 평가

강한 점:

- 기존 DX11 엔진 경험을 Unity 시스템으로 번역한다는 점이 차별화된다.
- Editor Tool 제작은 실무 생산성 관점에서 강력하다.
- Skill System은 라이브 게임 클라이언트와 직접 연결된다.
- Rendering/Optimization Debug는 중견 이상 클라이언트 포지션에서 좋은 신호다.

주의할 점:

- 너무 많은 기능을 얕게 만들면 역효과다.
- Unity 기본기를 묻는 질문에 약하면 DX11 경험이 가려진다.
- 코드 품질, 폴더 구조, asmdef, 테스트, 문서가 같이 있어야 한다.

우선순위:

1. Skill Runtime
2. Skill Editor
3. Animation Tool
4. Optimization Showcase
5. Shader Showcase
6. Rendering Debug View

렌더링보다 Skill/Editor/Animation을 먼저 완성하는 것이 이직 시장에서는 더 안정적이다. 렌더링은 화려하지만, Unity 클라이언트 실무에서 바로 검증되는 역량은 시스템/툴/런타임 구조다.
