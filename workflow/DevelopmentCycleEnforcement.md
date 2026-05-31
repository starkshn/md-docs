# Development Cycle Enforcement Rules

## 목적

포트폴리오 개발 과정 전체를 GitHub, Technical Docs, Tistory Blog, Notion Development Journal과 연결한다. Codex는 단순히 기능 구현만 수행하면 안 된다.

각 기능은 반드시 아래 개발 사이클을 완료해야 한다.

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

위 단계가 모두 완료되지 않으면 해당 기능은 완료로 간주하지 않는다.

## 기술적 가치가 있는 기능만 블로그 작성

모든 기능을 블로그로 작성할 필요는 없다. Codex는 구현 내용 중 기술적으로 가치가 있는 부분을 식별해야 한다.

### 블로그 작성 대상

Skill System:

- Runtime Skill Assembly
- Data Driven Design
- ScriptableObject Architecture
- Feature Module Integration

Skill Tool:

- EditorWindow Architecture
- Validation Framework
- Tool UX

Animation Tool:

- Playables API
- Animation Event Pipeline
- Bone Visualization

Shader Showcase:

- Fresnel
- Rim Light
- Dissolve
- Outline
- SRP Batcher 대응

Optimization Showcase:

- Object Pooling
- GPU Instancing
- LOD
- Culling
- Addressables

Rendering Debug View:

- RenderTexture
- Multi Camera
- ScriptableRenderPass
- Before/After Comparison Framework

## 기능 완료 기준

Codex는 기능 구현이 끝났다고 판단하기 전에 반드시 아래 체크리스트를 확인한다.

### 구현

- 기능 동작
- 예제 씬 존재
- 최소 검증 완료

### 문서

- Markdown 작성 완료
- 설계 의도와 문제 해결 과정 포함
- 개선 방향 포함

### UML

- PlantUML 작성 완료
- 클래스 구조, 시퀀스, 데이터 흐름 중 필요한 항목 반영

### Git

- 설명 가능한 기술 단위로 Commit 완료

### 블로그

- Blog Draft 생성 완료
- 단순 구현 기록이 아니라 학습, 문제 발견, 재설계 이유 포함

### 노션

- Notion Development Journal 작성 완료
- 오늘 목표, 공부한 개념, 문제, 해결, 다음 작업 포함

### 면접

- Interview Summary 작성 완료
- 1분 설명, 3분 설명, 깊게 물어볼 질문 대비 포함

## Git Commit 규칙

Commit은 기능 단위가 아니라 “설명 가능한 기술 단위”로 수행한다.

좋은 예:

```text
feat: implement runtime skill assembly
feat: add effect-target-condition separation
feat: add skill validation framework
feat: implement playables animation preview
feat: add before-after comparison framework
feat: implement feature toggle architecture
```

나쁜 예:

```text
feat: update
feat: fix
feat: skill system complete
```

## Codex의 완료 선언 규칙

Codex는 최종 응답에서 다음을 구분해서 보고해야 한다.

- 구현 완료 여부
- 검증 완료 여부
- Markdown 완료 여부
- PlantUML 완료 여부
- Blog Draft 완료 여부
- Notion Journal 완료 여부
- Interview Notes 완료 여부
- Git Commit 완료 여부

모든 항목이 끝나지 않았다면 “기능 완료”라고 말하지 않는다. 대신 “구현 완료, 문서화 미완료”처럼 상태를 정확히 말한다.
